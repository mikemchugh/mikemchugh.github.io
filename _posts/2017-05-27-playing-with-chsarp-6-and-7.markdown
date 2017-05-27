---
layout: post
title:  "Playing with C# 6 and 7 - Read-only auto properties"
date:   2017-05-27 14:00:00 +0100
categories: C#
---

# Playing with C# 6 and 7

My projects at work are stuck on older versions of C#, so whilst reading *C# 7.0 in a Nutshell* by *Ben Albahari* and *Joseph Albahari*, I thought I would try out some of the new features I've been missing out on.

We'll start with C# 6's read-only automatic properties.

## C# 6

### Read only auto properties

Immutability provide benefits such as:

 * thread safety
 * reduces cognitive load
 * easy to test

Prior to C# 6 we could nearly achieve immutability with automatic properties by using a `private set` as in the code below, though we lose immutability if someone else adds in a method such as `MofifyFoo(bool newFoo)` to our class as this will have access to our `IsFoo` property:

```csharp
public class FooChecker
{
  public bool IsFoo { get; private set; }
  
  public FooChecker(bool isFoo)
  {
    IsFoo = isFoo;
  }

  public void ModifyFoo(bool newFoo)
  {
    IsFoo = newFoo;
  }
}

void Main()
{
  var fooIsOn = new FooChecker(true);
  var fooIsOff = new FooChecker(false);
}
```

To achieve actual immutability prior to C# 6 we would have to be a bit more verbose and include a `readonly` backing field.

```csharp
public class FooChecker
{
  public bool IsFoo { get { return _isFoo; } }
  private readonly bool _isFoo;

  public FooChecker(bool isFoo)
  {
    _isFoo = isFoo;
  }
  
  public void ModifyFoo(bool newFoo)
  {
    IsFoo = newFoo; // this will not compile
  }
}

void Main()
{
  var fooIsOn = new FooChecker(true);
  var fooIsOff = new FooChecker(false);
}
```

Now we no longer need to worry anybody changing the value of `IsFoo`.

C# 6 enables us to do away with verbosity with the following code:

```csharp
public class FooChecker
{
  public bool IsFoo { get; }

  public FooChecker(bool isFoo) 
  {
    IsFoo = isFoo;
  }

  public void ModifyFoo(bool newFoo)
  {
    IsFoo = newFoo; // this will not compile
  }
}

void Main()
{
  var fooIsOn = new FooChecker(true);
  var fooIsOff = new FooChecker(false);
}
```