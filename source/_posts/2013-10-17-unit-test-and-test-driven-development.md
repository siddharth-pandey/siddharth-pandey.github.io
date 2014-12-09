---
layout: post
title: "Unit Test and Test Driven Development in ASP.NET MVC application"
date: 2013-10-17
comments: true
categories: [Test Driven Development, Unit Testing, nUnit, xUnit, MVC, .NET, Testing, Coding Style, ASP.NET, C#, TDD]
---

This article aims to summarize the concept of testing which can help you while writing tests using any framework out there. I will be writing more on this topic and will also attach any relevant demo applications on github. 

### Types of Testing
There are many types of testing that you may want to apply to your application, namely:  

- Unit Test & Test Driven Development (TDD)
- User Interface Testing
- Integration Testing
- Acceptance Testing 
- Performance Testing
- Accessibility Testing
- Security Testing

<!-- more -->

### Testing with ASP.NET Web Forms

If you are coming from ASP.NET Web Forms background and if you have done any testing in it, you may have find that it is not that easy to test your application because web forms aggregates and integrates the logic and the display i.e. view of your application. And this is what it makes testing very difficult.

### Testing with ASP.NET MVC

The concept of Model View Controller (MVC) is designed by keeping testing in mind. The design of an application based on MVC concept makes an distinction to have a separate Model (data), the display of the application i.e. View and the Controller that has the logic to bind the Model to the View.

Below are some resources that you will need to test your MVC application:

1. Visual Studio 2010/2012/Express 2013 (RC)
2. One of any testing software framework - nUnit or xUnit or MSTest.
3. Mocking Framwork - There are many free frameworks available out there but I'm going to use the free version of JustMock.
4. You can also download nUnit Runner - that doesn't depend on Visual Studio and runs independently.

### Caveat

There are couple of Caveat that we need to discuss before discussing the key concepts of testing an application:

1. There is no one right way to test.
2. Testing is something relatively new in the software development industry and people have different views to how to organize your tests, code, etc. This subject is open to discussion.
3. There is no one right way to refactor. You & your team should adapt the same pattern of the way to refactor so as to run on the same track and make a good design of your application.
4. Best practices - even these are subjective. Stick to something what the community follows and then extend it as per your needs.

### MVC and TDD

#### Unit Testing

1. Test a single unit - a Class or (better) a method.
2. Test in isolation of one another and to rest of the application. Test very small unit of functionality of your application.

#### TDD

1. Uses Unit Testing to drive the design of your application.
2. Is all about Test-First approach.
3. There is a term referred as Red Green Refactor, which means

- Red Phase - create a failed test.
- Green Phase - write just enough code to pass the above failed test.
- Refactor Phase - clean up you code and then retest it to make sure your refactoring has not affected your test and it runs well.
- Repeat  - repeat the above process again from Red - Green - Refactor phase.

#### Robert C. Martin's Laws - known as Uncle Bob in the community

Uncle Bob has mentioned three laws to keep in mind while writing a successful TDD:

1. Write no production code until you have written a failing test.
2. Write no more in your unit test then enough to make it fail.
3. Write no more production code then enough to make it pass.

#### Key points to remember whilst you write your First Test

1. Test one feature only.
2. Write the above test, run it and see it fail. It's very important to see it fail - because only by seeing it fail you can have the confidence when you see it pass that you have corrected the issue.
3. Fix only enough so that your test can pass. It's very important - don't get ahead of yourself to make a pass for your test anyway. As,

- Remember **YAGNI  ** - **You Ain't Gonna Need It** . Sometimes you often end up working and spending time on something that you won't need later, so, avoid that. 
- If no. 3 above is not followed then you are writing something which is not tested and may be will not be tested in the future as well as many of the code that you have written just makes pass for the test very easily.
- Run your test and see it succeed.
- Refactor and retest - to see your refactor has not broken the test.
- Repeat the whole process from no. 1 above.

#### Asserts

1. It's a way to see if you have in fact succeed i.e. what you expect to be true.
2. Normally using any testing framework, you will find the keyword - "Assert" to make an assert of what you expect to be true.
3. **Rule to remember: You should have only one "logical" assert per test.** It's fine to have on or more assert statement but logically you should test just one thing and to ensure what is reason that your test should fail.
4. There are many aspects that you can check while asserting namely,

- Equality - AreEqual, AreNotEqual, etc.
- Identity - AreSame, AreNotSame, Contains, etc.
- Condition - IsTrue, IsFalse, IsNull, IsNotNull, IsNan, IsEmpty, IsNotEmpty, etc.
- Type Checking - IsInstanceOf<t>, IsNotInstanceOf<t>, IsAssignableFrom<t>, etc.</t></t></t>
- Exception Throw or not thrown.
- String - Contains, StartsWith, EndsWith, AreEqualIgnoringCase, IsMatch (regex), etc.
- Collection - AllItemsAre... InstanceOfType, NotNull, Unique, Equal, Equivalent, etc.
- File - AreEqual, AreNotEqual, etc.
- Driectory - AreEqual, AreNotEqual, etc.
- Asserts to force a result - Assert.Pass, Assert.Fail, Assert.Ignore, etc.

#### Red - Green Refactoring Cycle

  
  

<tbody>
<tr><td style="text-align: center;"><a href="http://4.bp.blogspot.com/-Neui5RASyE8/Ul-5UoulcjI/AAAAAAAAA5w/n7AVKYI7aKw/s1600/rgr.PNG" imageanchor="1" style="margin-left: auto; margin-right: auto;"><img border="0" height="162" src="http://4.bp.blogspot.com/-Neui5RASyE8/Ul-5UoulcjI/AAAAAAAAA5w/n7AVKYI7aKw/s400/rgr.PNG" width="400"></a></td></tr>
<tr><td class="tr-caption" style="text-align: center;">Red - Green Refactoring Cycle</td></tr>
</tbody>

  
  

#### But how do you Refactor ?

Uncle Bob says - Follow **SOLID**

1. **Single Responsibility: **

- Exactly one reason for a Class/method to change.
- One responsibility per Class/method.
- **Open Closed Principle:**

- Your Class should be open for extension, closed for modification.
- Creates dependable api to your Class.
- Derive but don't modify internals of your Class.
- **Liskov Substitution Principle:**

- Ability to replace instances with their sub-types at run-time.
- **Interface Segregation Principle:**

- No client should be forced to depend on method it doesn't use.
- Create small interfaces.
- **Dependency Inversion Principle:**

- Depend on abstractions and not on concrete implementation. This is the art of dependency injection.

#### Key points to remember whilst Refactoring

1. Names matter

- Spend time while naming
- Renaming is very cheap - do it if you feel so.
- Use meaningful names.
- Don't be afraid of long names.
- Make names pronounceable.
- Classes = Nouns
- Methods = Verbs
- Collections are plural.
- Avoid encoding:

  - No Hungarian Notation
  - Interfaces do not begin with I.
- Functions/Methods should be small.
- Do one thing & do it well.
- Avoid Switch Statements

- Use derived types where possible.
- Use Descriptive names - don't be afraid of long names.
- Minimize number of parameters you pass to a method

- Zero is ideal
- One or two are workable
- Three or more are too much cognitive load of understanding how your method works and those parameters interact. 
- **Don't Repeat Yourself (DRY)**
- **YAGNI**
- Structured Programming is dead - in a small method, multiple returns can clarify.
- Use fewer & smarter comments

- To explain intent when obscure.
- Use **ToDo** comments but no in production code.
- Avoid most comments and fix the code instead.
- **The Law Of Demeter**

- Modules should not know about innards of objects.
- Objects hide their data.
- Objects expose their public methods.
- Use Exceptions, not errors

- Don't return null or pass null.
- Classes should be small.
- Single Responsibility should be applied to classes.
- Refactor your Tests by keeping **FIRST** in mind

- **Fast**

  - Test should run quickly else you won't run it and then it has no value.
- **Independent**

  - Order of the tests must not matter.
  - No dependencies between tests.
- **Repeatable**

  - Running the same test twice should yield the same answer reliably.
- **Self-Validating**

  - Tests should return Boolean: Pass or Fail but no ambiguity.
- **Timely**

  - Tests should be written just before production code.

This was all about the concepts that you should keep in your mind while writing programs. Practice the above in your daily work and you will notice the difference it makes in your way to write applications.

  
  

Stay tuned for sample application to write tests with MVC.

  
  

