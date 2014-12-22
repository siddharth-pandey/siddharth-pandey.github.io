---
layout: post
title: "How to compress, decompress a string in c# using GZipStream?"
date: 2014-09-15 11:37:12 +0000
comments: true
categories: [C#, .NET, ASP.NET]
sharing: true
---

I recently had a scenario where my application was sending raw json data to send to the browser in string format. This data was used as a viewstate by using hidden input element. When the app started to run in production envrionment, we realised that this raw data is very big in size and needs to be compressed. 

So, the only solution available here was to compress the raw data and decompress it when app wants to access the data. Both needs to happen server-side. My app uses .NET v4.5, so I thought to use the out of the box classL [GZipStream](http://msdn.microsoft.com/en-us/library/system.io.compression.gzipstream.aspx)

<!-- more -->

Below is the code for compress and decompress feature:

```
    /// <summary>
    /// Represents a class that can be consumed to compress/decompress string.
    /// </summary>
    public static class Compressor
    {
        /// <summary>
        /// Use this to compress UTF-8 string to Base-64 string.
        /// </summary>
        /// <param name="text">The string value to compress.</param>
        /// <returns></returns>
        public static string Compress(this string text)
        {
            var buffer = Encoding.UTF8.GetBytes(text);
            var memoryStream = new MemoryStream();
            using (var stream = new GZipStream(memoryStream, CompressionMode.Compress, true))
            {
                stream.Write(buffer, 0, buffer.Length);
            }
            memoryStream.Position = 0;
            var compressed = new byte[memoryStream.Length];
            memoryStream.Read(compressed, 0, compressed.Length);
            var gZipBuffer = new byte[compressed.Length + 4];
            Buffer.BlockCopy(compressed, 0, gZipBuffer, 4, compressed.Length);
            Buffer.BlockCopy(BitConverter.GetBytes(buffer.Length), 0, gZipBuffer, 0, 4);
            return Convert.ToBase64String(gZipBuffer);
        }

        /// <summary>
        /// Use this to decompress Base-64 string to UTF-8 string.
        /// </summary>
        /// <param name="compressedText"></param>
        /// <returns></returns>
        public static string Decompress(this string compressedText)
        {
            var gZipBuffer = Convert.FromBase64String(compressedText);
            using (var memoryStream = new MemoryStream())
            {
                int dataLength = BitConverter.ToInt32(gZipBuffer, 0);
                memoryStream.Write(gZipBuffer, 4, gZipBuffer.Length - 4);
                var buffer = new byte[dataLength];
                memoryStream.Position = 0;
                using (var gZipStream = new GZipStream(memoryStream, CompressionMode.Decompress))
                {
                    gZipStream.Read(buffer, 0, buffer.Length);
                }
                return Encoding.UTF8.GetString(buffer);
            }
        }

    }
```

The above utitlity helper can be used in following way:

```
    // to compress rawData object's value.
    var dataToPersist = Compressor.Compress(JsonConvert.SerializeObject(rawData));

    // to decompress the dataToPersist in particular type.
    var data = JsonConvert.DeserializeObject<Type>(Compressor.Decompress(dataToPersist));

```
