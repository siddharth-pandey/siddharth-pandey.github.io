---
layout: post
title: "Introduction to Dependency Injection"
date: 2015-01-12 19:42:43 +0000
comments: true
categories: [Software Practices, .NET, C#]
sharing: true
---
##What is Dependency Injection?

In simple words, Dependency Injection (DI), is a type of IoC where the creation and binding of a dependency is moved outside of the class that depends on it.

Say suppose when you pack your lunch, you know what you have packed inside it. But when you know that the food will be provided, you know that you need not to worry about lunch, it will just be served when you need it.

Similar to above example, when you don't use DI, your class will have the creation and binding of dependencies inside it. But when you use DI, your class will just work taking into consideration that the required dependencies will be provided by a service.

<!-- more -->

##Where do dependencies come from?

For example, in your class `MyClass`, you have a dependency on say class `Dependency`. Let us assume that `MyClass` directly depends on `Dependency`. Now, to follow DIP, we create an interface `IDependency` that `Dependency` implements. So our class now looks like this:

```
public class MyClass
{
    private IDependency _depencency = new Dependency();  
}
```

Even after creating an interface, `MyClass` still creates an object of class `Dependency` inside it and it means it is controlling the the creation of it.

So we can introduce an `Injector` which will take care of the issue above and it will have knowledge of `MyClass` & `IDependency`. Using this `Injector`, we can make `MyClass` have no knowledge about `Dependency` class.

##Types of Dependency Injection

 - Constructor Injection
    + is very common and simple.
    + pass the dependency into dependent class via constructor of the class.
    + example of constructor injection:

        ```
        // usage
        ICreditCard creditCard = new MasterCard();
        Shopper shopper = new Shopper(creditCard);

        public class Shopper
        {
            private readonly ICreditCard creditCard;

            public Shopper(ICreditCard creditCard)
            {
                this.creditCard = creditCard;
            }
        }
        ```

 - Setter Injection
    + Instead of passing dependency via a constructor, create a setter (property in C#) on the dependent class.
    + Use the setter to set the dependency.
    + Order of usage of this setter is very important because unlike Constructor Injection, you can create an object of class and may or may not set the dependency.
    + The dependency may be modified even after creating an object of class which gives us flexibility but its risky at the same time. 
    + example of setter injection:

        ```
        // usage 
        ICreditCard creditCard = new MasterCard();
        Shopper shopper = new Shopper();
        shopper.CreditCard = creditCard;

        public class Shopper
        {
            public ICreditCard CreditCard { get; set; }
        }
        ```

 - Interface Injection
     + Dependent class implements an interface.
     + Injector uses the interface to set the dependency.
     + not so common as the other types above but comparetively is complex.
     + example of interface injection:

        ```
        // usage 
        ICreditCard creditCard = new MasterCard();
        Shopper shopper = new Shopper();
        ((IDependOnCreditCard)shopper).Inject(creditCard);

        public class Shopper : IDependOnCreditCard
        {
            private ICreditCard creditCard;
            public void Inject(ICreditCard creditCard)
            {
                this.creditCard = creditCard;
            }
        }

        public interface IDependOnCreditCard
        {
            void Inject(ICreditCard creditCard);
        }
        ```

##Cautions

 - Leaks the internal implementation details of a class
     + Violates encapsulation
 - Prevents deferred creation
     + Dependencies created before needed so that it can be passed to the class that needs it.
     + Watch out for large object graphs as your dependencies as it may lead to memory issues if its created without any requirements.
 - DI makes easier to unit tests classes because you don't care about dependencies that a particular class needs! So, watch out for too many dependencies.




