# Null Safety in Flutter

## What is null?

The null value is an instance of the Null class, without null safety a variable (eg: String) can be two things, it could actual variable or it could be null.
To understand better we can take an example.

```dart
void main(){
    Map<String, dynamic> _person={"name":"John",};
    print(_person);
}
```

Here we have a **Map** called **person** with key **name**, and if we try to access a key that does not exist in that map we get a null value which means that there is no value for that key in that map. and there are many situations where we can use null values. Null is **good** and uses full when u take care of it and protect code from it. we can use if statements to check if a value is null

```dart
void main(){
    Map<String, dynamic> _person={"name":"John",};
    if(_person["age"]==null){
        print("Age is null")
    }else{
        print(_person);
    }
}
```

But sometimes null values are unwanted because if we can guarantee that a value can never be null we don”t need to check for it.

## Null safety

null safety (also known as **Void safety**) is a guarantee within an object-oriented programming language that no object references will have null or void values.
Some of the languages having null safety are **C#**, **kotlin**, and **swift**.

## Why do we need null safety?

Null safety eliminates that problem at the root by changing the type hierarchy. The Null type still exists, but it’s no longer a subtype of all types. If you run this Dart program without null safety, it throws null errors like the **NoSuchMethodError exception**. The Runtime failures suck. This is especially true in a language like Dart that is designed to run on an end user’s device. If a server application fails, you can often restart it before anyone notices. So we need to make sure that the app should not crash because of null errors.

## null safety in Flutter

**Flutter 2** supports null safety. Null safety is a relatively modern productivity feature that helps us avoid cases of null exceptions in our applications, These exceptions are a set of bugs that are particularly not easily debugged. Null safety is a great milestone for the language and it also enables performance improvements and it was introduced in Dart v2.9 as a Language feature.
The means that all types in Dart are non-nullable by default.

With null safety feature we can catch null errors at compile time rather than at runtime.
The Dart is 100% sure that the files list, and the elements in it, cannot be null. When Dart analyzes your code and determines that a variable is non-nullable, that variable is always non-nullable: if you inspect your running code in the debugger, you’ll see that non-nullability is retained at runtime. Dart shares sound null safety with Swift, but not very many other programming languages.

## With Dart null safety

If we try to assign null to any type of variable compiler will throw an error since all types in Dart are non-nullable by default. Unless you explicitly tell Dart that a variable can be null, it will consider it non-nullable.
For example with null safe Dart, a String can only be a String not null but we can purposely define a variable to be null or that variable type.
We can create a non-nullable variable and initialize it later, Dark makes it possible because it supports definite assignment.

![](https://lh4.googleusercontent.com/SMPYPG2VitB1F9IcwrT8qj5rcts55lVtfKEZqZcbbmDco5dId_x85Si3DT2lOf8qLk7TxIc6v_xT1l2abjLamNcWV2ah4DZOvlDjJS0)

But if we try to access the variable before it is definitely assigned it will through compile-time error.

![](https://lh4.googleusercontent.com/xJBYtKjjnSxycK5rWGPE6NXhw62eeJ-TNgIS6G0CpZ7H17g1NUtDCi6WvWBRlDN_7qbhMDhh8UdsOjBPR0qBtnEfcxNoB1_8osPCh9FnSDFCpBZvn0QkE6iN8-Y5exDfTiCgmjiD)

## Declaring Non-Nullable Variables

When we use non-nullable variables we must ensure that Non-nullable variables must always be initialized with non-null values.

![](https://lh6.googleusercontent.com/qA5mS4Oi9HJHaaD64iOmBLuRIruzq1VmbU0CXAA5HpzPgkOMvVkwt2Ub7PvKJxmD0YWi87dI5V3oOcECyFhXMXV31OwuFI1owRaZmi4)

For example, if we try to initialize a String variable \_name with null, it will throw a compile-time error and refuse to compile the code. As a result runtime, null checks are no longer necessary.
Here we can discuss some basic changes in Dart with null safety added.

## Declaring Nullable Variable

What if we need to declare nullable variables? For that purpose, Dart provides a special ? symbol.

![](https://lh5.googleusercontent.com/YLeF_SZSHkCTN_h3L64eSYtBA-U7A5UooWXwtcDT3LaIQLmg3LHXXYCkOWu4czdv8lUPIEK942oMHAygsleIRuSGLl52LvklhKBvZJDr)

Here variables name and age are declared as nullable variables by using ? and we don”t need to initialize these variables before using them. there are initialized to null by default and Also, we can reassign to null whenever we need.

## The assertion operator

There are cases where we know that something can”t be null , but we need to can”t prove it to the compiler. In these cases, the assertion operator can help.

![](https://lh4.googleusercontent.com/k9bJGhFeELSFkg0sMp7pBQ9LEYfIT40pw3T-v2mpzpw5bcMdBoxUW1EQheeHLSujFtcCD0DRP3gyaucEFcM-WH6gOtGhpm77Tp2ujm4GwuQolZmy-ixVLMAHhm9q9ZQCkoKuqmv9)
The assertion operator ! helps to assign a nullable variable to a non-nullable variable

## The Late keyword

The late keyword comes in handy to denote variables that are not initialized immediately they are created, but whenever they are accessed. This implies that we can have non-null instance fields that will be initialized later on.

![](https://lh6.googleusercontent.com/WN2osv1R4yorYePNsoAY8jvIgepXR7jU2JgY62GKQPYqsQC0jrHFJtiiWWLEJ4Zu20Rl9V1ArYFvTKDqsFb2GAwQOuq84xiRWJK3l5QQXIwWXMtbHJql1jufIjlF4li_rsCMGIOB)

Here the textEditingController is only initialized at the initState method not where it’s created. this helps when we assign value to it.

## Advantages of null safety in dart

- We can reduce most of the runtime errors and crashes.
- We can write null-safe code with strong compile-time guarantees.
- We can more easily declare our intent.
- The Dart compiler can optimize our code and the compiler doesn’t need to look null check to a variable that we specifically defined as null, resulting in smaller and faster programs.
