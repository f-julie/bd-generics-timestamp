## Using TimestampedData\<T>

### Context

We're going to complete a new class, `TimestampedData`,
which stores a data value of any Object type, represented by the generic
parameter, `T`, plus a timestamp corresponding to when the data was
collected. This could be useful in code responsible for monitoring data
collected over time, for example.

Today we'll be following these general steps:

1. Inspect an approach we might take if we didn't have generics available to us.
   We could create a new `Timestamped[Type]` class for every type of data we want to attach a timestamp to.
   For example, `TimestampedString` could pair a `String` and a timestamp.
1. Inspect the start of the implementation of the `TimestampedData<T>` class that allows us to store **any**
   Java object with a timestamp (including `String`)
1. Implement the rest of `TimestampedData<T>`
1. Complete some unit tests for `TimestampedData<T>`
1. Use `TimestampedData<T>` in some code

### Step 1: Read `TimestampedString`

Read the existing `TimestampedString` class found in the same package as this README.
You should see that it stores a `String data` and `ZonedDateTime timestamp` and
provides getters to retrieve those values.

You have completed this step when:
* You understand what `TimestampedString` is doing (storing a `String` with a corresponding `ZonedDateTime`)

### Step 2: Read `TimestampedData`

Read the existing `TimestampedData` class found in the same package as this README.
`TimestampedData` is identical to `TimestampedString`, except `TimestampedData`
can store **any** Java object, not just a `String`. As you read, look for where we
were using `String data` in `TimestampedString`. Those places now use a generic `T data`.

You have completed this step when:
* You understand what has been changed between `TimestampedData` and `TimestampedString` so that `TimestampedData`
  can store **any** Java object.

### Step 3: Finish implementation of `TimestampedData`

`TimestampedData` is missing a getter for the `data` attribute. Implement that
missing getter, `getData()`. What will be the return type of this method?...

You have completed this step when:
* You have implemented the `getData()` method of `TimestampedData`

### Step 4: Finish writing the test code

1. Find the `TimestampedDataTest` test class under tst/
1. Read through the test cases
3. Several test methods are waiting for the `getData()` method to be
   implemented to add missing assertions to their `THEN` sections. Add
   the missing assertions to the 3 implemented tests:
    * `dataAndTimestampConstructor_withNonNullValues_constructsInstance`
    * `dataAndTimestampConstructor_withNullData_constructsInstance`
    * `dataConstructor_withData_defaultsTimestampToNow`
1. Implement the last test: `dataConstructor_withNullData_constructsInstance`

You can run the tests from command line with:

    `./gradlew -q clean :test`
    
You have completed this step when:
* You have updated all places marked with `PARTICIPANTS` comments in `TimestampedDataTest`
* All tests are passing

### Step 5: Use the class!

1. Open the `DataLogger` class and finish the implementation of the `logData()` method by creating a
   `TimestampedData` object for each pair from the two arrays provided to `logData()`, then printing out the
   contents to the console using `System.out.println()`.
    * Think about what the generic parameter should be for this use of `TimestampedData`
    * Can you use `TimestampedData`'s `toString()` to make the eventual printing out simple?
    
You have completed this step when:
* You have updated `logData()` to create a `TimestampedData` for each data/timestamp pair and print its contents.

### Step 6: Commit and push

Commit your working code and push it to your remote branch.

### Step 7: Return to Canvas quiz to answer a few questions

Open your commit in code browser so you can paste a URL into Canvas, then answer the questions about this activity
using the `TimestampedData` class.
