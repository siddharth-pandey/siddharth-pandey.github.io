---
layout: post
title: "How to store data using SQLiteDatabase in Android application?"
date: 2015-01-28 09:35:19 +0000
comments: true
categories: [Android, Java, Android Studio]
sharing: true
---

I was asked by one of my friend to help him to save some data in his android application. Due to that nature of the application, his preferred storage option was [SQLiteDatabase](http://developer.android.com/reference/android/database/sqlite/SQLiteDatabase.html) which resides under `android.database.sqlite` namespace. It exposes methods to manage a SQLite database. It also has methods to create, delete, execute SQL commands, and perform other common database management tasks.

<!-- more -->
[You can view and download the sample application here](https://github.com/siddharth-pandey/Students-Catalog). Feel free to download or modify the project by extending it.

Let us look at the following code below that is taken from the project mentioned in the link above.

Below is the code from `onCreate()` overload function that is called when the activity is first created.

```
/** Called when the activity is first created. */
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        editRollno=(EditText)findViewById(R.id.editRollno);
        editName=(EditText)findViewById(R.id.editName);
        editMarks=(EditText)findViewById(R.id.editMarks);
        btnAdd=(Button)findViewById(R.id.btnAdd);
        btnDelete=(Button)findViewById(R.id.btnDelete);
        btnModify=(Button)findViewById(R.id.btnModify);
        btnView=(Button)findViewById(R.id.btnView);
        btnViewAll=(Button)findViewById(R.id.btnViewAll);
        btnShowInfo=(Button)findViewById(R.id.btnShowInfo);

        // setup click listener for all the buttons
        btnAdd.setOnClickListener(this);
        btnDelete.setOnClickListener(this);
        btnModify.setOnClickListener(this);
        btnView.setOnClickListener(this);
        btnViewAll.setOnClickListener(this);
        btnShowInfo.setOnClickListener(this);

        // database related code
        db = openOrCreateDatabase("StudentDB", Context.MODE_PRIVATE, null);
        db.execSQL("CREATE TABLE IF NOT EXISTS student(rollno VARCHAR,name VARCHAR,marks VARCHAR);");
    }
```

Let us look at the code above. We get references to all the buttons and edittext widgets in our code that is quite straightforward. Then we setup click listeners for all the buttons. To do that we make our Activity class implement `View.OnClickListener` interface. We are using this way to setup click handlers so basically, the `onClick()` function is called when a `View` has been clicked. 

Next is the code related to database. `openOrCreateDatabase()` function, as the name suggests opens `StudentDB` database if it exists already. If not, it then creates it. The first paramter is the name of the database that we want to open or create i.e. `StudentDB`. The second parameter, `Context.MODE_PRIVATE` indicates that the database file can only be accessed by the calling application or all applications sharing the same user ID. The third parameter is a `Cursor` factory object which can be left null if not required.

The second statement, `db.execSQL()` function is to execute any SQL command. Above, it is used to create a table named `student` if it doesn't exist. We use this function for queries like `INSERT, UPDATE, DELETE`.

This app also uses `db.rawQuery()` that runs the provided SQL and returns aCursor over the result set and we check the result by using `moveToFirst()` function that moves the cursor to the first row and returns a boolean. If false we then show either a alert or Toast message to user.

I'm not going to paste all the code from project here as the main statements and functions are already covered above. Download the project and give it a try.



