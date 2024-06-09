# My own programming language
I'm not making a programming language. But these are some features I would add.
This will be compared to Java.

## Replacement for "key" strings

Many things need strings in a non-normal-string-context (how I see it). This new symbol # could be used in replacement of double quotes in any string, but should be used like this:
```java
// Old code
String response = json.getElement("response");
// New code
String response = json.getElement(#response#);
```

## Proper placeholder symbol

Some things like wikis might need placeholders in their code. This new symbol * could be used in replacement of multi-line comments.
```java
// Old code
String myVariable = json.getElement(/* insert the field you want to get here*/);
// New code
String myVariable = json.getElement(* insert the field you want to get here *);
```

## A new way of assigning variables

This was supposed to be for changing mutating methods (replacing some with return / copying methods). A new way to assign variables with a simple keyword assign. (could be shortened somehow)
```java
// Old code
String hello = "Hello world!";
hello = hello.substring(0, 5);
// New code
String hello = "Hello world!";
assign hello.substring(0, 5);
```

## Conditions

The function / lambda conditions are fine but could be simplified.
```java
// Old code
public static void main(String[] args) {
  scheduleCondition(() => System.out.println("hello!"), 1000, () => thing.isTrue);
}

public static void scheduleCondition(Runnable runnable, int time, Runnable condition) {
  schedule(() => {
    if (condition()) runnable()
   }, time);
}
// New code
public static void main(String[] args) {
  scheduleCondition(() => System.out.println("hello!"), 1000, ~thing.isTrue~);
}

public static void scheduleCondition(Runnable runnable, int time, Condition condition) {
  schedule(() => {
    if (condition) runnable();
   }, time);
}
```

## Important comments

In Java, all comments get discarded at compilation, which makes sense but can be bad for decompilers looking through some code. The alternative to this is usually defining a string with the comment.

```java
// Old code
String comment = "This code seems harmful but doesn't go to any servers. Verify in other classes."
deleteEverything();
// New code
!// This code seems harmful but doesn't go to any servers. Verify in another classes.
!/* trust */!
deleteEverything();
```

In this case, there could be a special opcode for it.
```java
comment "This and that"
invokestatic #7 // Method whatever
```
