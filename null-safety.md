# Null Safety in Flutter

## What is null?

The null value is an instance of the Null class without null safety, a variable (e.g.: String) can be two things, it could be an actual variable, or it could be null. For example:

```dart
void main(){
    Map<String, dynamic> _person={"name":"John",};
    print(_person);
}
```

Here we have a **Map** called **person** with a key name, and if we try to access a key that does not exist in that map, we get a null value which means that there is no value for that key in that map. And there are many situations where we can use null values. Null is **good** and useful when you take care of it and protect code from it. We can use “if statements” to check if a value is null.

```DArt
void main(){
    Map<String, dynamic> _person={"name":"John",};
    if(_person["age"]==null){
        print("Age is null")
    }else{
        print(_person);
    }
}
```

But sometimes null values are unwanted because if we can guarantee that a value can never be null, we don”t need to check for it.

## Null safety

Null safety (also known as **Void safety**) guarantees that no object references will have null or void values. There are only a few programming languages that provide null safety.

Some of the languages having null safety are **C#**, **Kotlin**, and **Swift**.

## Why do we need null safety?

Null safety removes the problem due to null at the root level by changing the type hierarchy. The Null type still exists, but it’s no longer a subtype of all types. If you run the Dart program without null safety, it throws null errors like the **NoSuchMethodError exception**. In a language like Dart that is designed to run on an end user’s device, It is very necessary to make sure the app does not crash. Because we cannot fix such exceptions with a restart. So we need to make sure that the app does not crash because of null errors.

## Null safety in Flutter

**Flutter 2** supports null safety. Null safety is a modern productivity feature that helps us avoid cases of null exceptions in our flutter applications; These null exception bugs are not easily debugged. Null safety is a great update to the Dart language, and it also enables high performance. Null safety was introduced in Dart v2.9 as a Language feature. Now the Dart language is 100% sure that the files list and its elements cannot be null. It means that all types in Dart are non-nullable by default.

With the null safety feature, we can catch null errors at compile time rather than at runtime. When Dart analyzes the code and determines that a variable is non-nullable, that variable is always non-nullable. The non-nullability is retained even at runtime. Dart shares sound null safety with Swift.

## With Dart null safety

If we try to assign null to any type of variable compiler will throw an error since all types in Dart are non-nullable by default. Unless you explicitly tell Dart that a variable can be null, it will consider it as a non-nullable variable. For example, with null safe Dart, a String can only be a String, not null, but we can purposely define a variable to be null or that variable type. We can create a non-nullable variable and initialize it later. Dart makes it possible because it supports definite assignments.

![](https://raw.githubusercontent.com/rinujacobthomas/blog/main/1.png)

But if we try to access the variable before it is definitely assigned, it will throw a compile-time error.

![](https://raw.githubusercontent.com/rinujacobthomas/blog/main/error.png)

## Declaring Non-Nullable Variables

When we use non-nullable variables, ensure that we initialize non-nullable variables with non-null values.

```Dart
void main(){
    String _name = "john";
}
```

But, if we try to initialize a String variable \_name with null.

![](https://raw.githubusercontent.com/rinujacobthomas/blog/main/nonnullable.png)

It will throw a compile-time error and refuse to compile the code. As a result, runtime null checks are no longer necessary. Here we can discuss some basic changes in Dart with null safety added.

## Declaring Nullable Variable

What if we need to declare nullable variables? For that purpose, Dart provides a special “?” symbol.

![](https://raw.githubusercontent.com/rinujacobthomas/blog/main/nullable.png)

Here variables name and age are declared as nullable variables by using “?” and we don’t need to initialize these variables before using them. They are initialized to null by default. And also, we can reassign them to null whenever we need.

## The assertion operator

There are cases where we know that a variable can’t be null, but the compiler may consider it as null. In these cases, we use the assertion operator.

![](https://raw.githubusercontent.com/rinujacobthomas/blog/main/assertion.png)

The assertion operator “!” helps to assign a nullable variable to a non-nullable variable

## The Late keyword

The late keyword comes in handy to denote variables that are not initialized immediately they are created, but whenever they are accessed. It means that we can have a non-null instance of a variable that will be initialized later on.

![](https://raw.githubusercontent.com/rinujacobthomas/blog/main/late.png)

Here the textEditingController is only initialized at the initState method, not where it is created; this helps when we assign value to it.

## Advantages of null safety in dart

- We can reduce most of the runtime errors and crashes.

- We can write null-safe code.

- We can more easily declare our intent.

- The Dart compiler doesn’t need to look for null checks to variables that we defined explicitly as null, resulting in smaller and faster programs.
