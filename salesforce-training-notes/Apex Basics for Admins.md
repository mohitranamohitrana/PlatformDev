# [Apex Basics for Admins](https://trailhead.salesforce.com/content/learn/modules/apex-basics-for-admins)

## Variables
Think of a variable as a container for data. You can give it a name to describe what’s in it. You can physically label it with a unique name and add things to the container. Once the container has everything you want in it, the container can be put away until it’s needed.

` String f = 'Melissa';`

## Common Data Types

Data Type             -- Description and Example

- Integer                --A positive or negative number that doesn’t have a decimal point.   

   `Integer num = 12;`


- Decimal             --  A positive or negative number that has a decimal point.

   `Decimal num = 12.22222;`


- String              -- A series of characters surrounded by single quotes. This can include any text as short as one letter to sentences.

   `String whatAmI = 'A String';`


- Boolean             -- Typically either true or false. In Apex, null (empty) is also a valid value. Boolean is commonly used with checkboxes.

  `Boolean doSomething = False;`


- ID (Salesforce ID)  -- Any valid 18-character Salesforce record ID.

   `Id contactId = '00300000003T2PGAA0';`



  Apex is a strongly-typed language, meaning that each time you declare (create) a variable, _you set its data type, its name, and optionally, its initial value._

  `Integer i = 2;`

  When you initialize a variable (assign it an initial value), the value you assign must match the variable’s data type. If you choose not to assign a value within the variable declaration statement, the value of the variable is null.

  
![Screenshot 2024-02-12 122855](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/eed7e74b-e1a7-4065-9dfd-52576faaeca2)


  ## Syntax

  The way that text and punctuation are arranged to create a programming language is called syntax. Here are some syntax rules for Apex code. 

  1. The first thing you may have noticed is that Apex statements end with a semicolon.
     ```java
     String whatTimeIsIt;
     ```
  3. Apex strings use single quotation marks to separate literal text from surrounding code. Numbers and Boolean (true or false) values don’t need quotes.
     ```java
      String whatTimeIsIt = 'It is Tea Time!';
      Integer sugarCount = 2;
      Boolean needsSugar = false;
     ```

## Collections
A collection is a type of variable that can store multiple items
     
### Lists
  ![Screenshot 2024-02-28 214836](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/ccf16ca5-b11b-43dc-9fa3-b015701789e8)
 
## Declare a List with a Set Size  
If we know exactly how long our list needs to be, we can set the size when we declare the list. We do this by including the size in brackets, [ ], after the data type, like this: 

![Screenshot 2024-02-28 215044](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/ac38b095-407d-49be-994a-cdc43884b0e6)

```java
String[] groceries = new String[4];
System.debug('Initialized groceries: ' + groceries);
  
System.debug('Item 0: ' + groceries[0]);
```

## Initialize a List

1. Declare and initialize a list
  ```java
//Sets the first item in the list to 'Tea'
List<String> groceries = new List<String>{'Tea'};
```
2. Declare an empty list and add values later
 ```java
List<String> groceries = new List<String>();
groceries.add('Tea');
```


```java
//Create the groceries list
List<String> groceries = new List<String>();
  
//The output for this statement is null
System.debug('Groceries: ' + groceries);
  
//Use the add method to add an element to the list
groceries.add('Tea');
groceries.add('Sugar');
groceries.add('Honey');
groceries.add(2, 'Milk');
  
//The output for this statement is Tea, Sugar, Milk, Honey
System.debug('Groceries: ' + groceries);
```

![Screenshot 2024-02-28 220509](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/75ea7a72-1732-471f-995e-1cd05835375b)

![Screenshot 2024-02-12 132649](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/1e42e747-cbfe-4ed1-a615-ab218e322791)

## Demystifying Lists
```java
String[] groceries = new String[4];
System.debug('Groceries: ' + groceries);
  
groceries.add('Tea');
groceries.add('Sugar');
System.debug('Added 2 items: ' + groceries);
  
groceries.add(1, 'Honey');
System.debug('Added Honey in index 1: ' + groceries);
  
System.debug('Item 0: ' + groceries[0]);
```
![Screenshot 2024-02-29 143642](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/dcbd0623-af3f-4f05-bafb-3dec6b02cce9)


## Comparison Operators

![Screenshot 2024-02-12 133237](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/21134d60-eabc-4641-ad53-cef475635787)

## Conditional Statements

### If-Else Statements

```java
if(condition is true) {
    //do this
} else {
    //do this
}
```

Line 1 defines the condition (written in parenthesis).
Line 2 contains the code to run if the condition on line 1 is true.
Line 3 introduces the second option, the else option.
Line 4 contains the code to run if the condition on line 1 is false.

```java
String waterLevel = 'full'; /*This variable keeps track of the water level status: full or empty*/
  
if(waterLevel == 'empty') {
    System.debug('Fill the tea kettle');
    waterLevel = 'full'; /*Once the tea kettle is filled the variable is changed to full*/
} else {
    System.debug('The tea kettle is full');
}
```




## If-Else If Statements

```java
String waterLevel = 'half';
  
if(waterLevel == 'empty') {
    System.debug('Fill the tea kettle');
    waterLevel = 'full';
} else if(waterLevel == 'half') {
    System.debug('Fill the tea kettle');
    waterLevel = 'full';
} else { /*This statement only runs if line 3 and line 6 result in false.*/
    System.debug('The tea kettle is full');
}
```


## Switch Statements

A more efficient alternative to an if-else statement is a switch statement. A switch statement specifies a set of values and tests an expression to determine whether it matches one of those values. Here is how it looks:


```java
switch on expression {
    when value1 {
        //code block 1
    }
    when value2 {
        //code block 2
    }
    when else { //if none of the previous values apply
        //code block 3
    }
}
```




In a switch statement, you can have one or more values after the when reserved word. 


```java
switch on expression {
    when value1 { //single value
        //code block 1
    }
    when value2, value3 { //multiple values
        //code block 2
    }
}
```



```java
String waterLevel = 'empty';
  
//option 1 using a single value
switch on waterLevel {
    when 'empty' {
        System.debug('Fill the tea kettle');
    }
    when 'half' {
        System.debug('Fill the tea kettle');
    }
    when 'full' {
        System.debug('The tea kettle is full');
    }
    when else {
        System.debug('Error!');
    }
}
  
//option 2 using multiple values
switch on waterLevel {
    when 'empty', 'half' { //when waterLevel is either empty or half
        System.debug('Fill the tea kettle');
    }
    when 'full' {
        System.debug('The tea kettle is full');
    }
    when else {
        System.debug('Error!');
    }
}
```





## Logical Operators

![Screenshot 2024-02-12 161539](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/0ba6be68-9a79-495a-b631-84693ce23b81)

![Screenshot 2024-02-12 161849](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/9e54f3b4-d5af-4f69-97ad-2a1a6321e875)



```java
String waterLevel = 'half';
  
if(waterLevel == 'empty') {
    System.debug('Fill the tea kettle');
    waterLevel = 'full';
} else if(waterLevel == 'half') {
    System.debug('Fill the tea kettle');
    waterLevel = 'full';
} else { //This statement only runs if line 3 and line 6 result in false.
    System.debug('The tea kettle is full');
}
```



```java
String waterLevel = 'half';
  
if(waterLevel == 'empty' || waterLevel == 'half') {
    System.debug('Fill the tea kettle');
    waterLevel = 'full';
} else { //This statement only runs if line 3 false.
    System.debug('The tea kettle is full');
}
```



## While 
The while loop starts with verifying if a condition has been met. If the condition is true, it does something. If it’s false, the loop stops.

![Screenshot 2024-02-12 204946](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/718d6c38-163b-4e52-a6b7-4925699fa7ea)

```java
While(condition) {
    //run this block of code
}
```


```java
//Declare an Integer variable called totalGuests and set it to 100
Integer totalGuests = 100;
  
//Declare an Integer variable called totalAmountSugar and set it to 159 (number of teaspoons in a bag of sugar).
Integer totalAmountSugar = 159;
  
//Declare an Integer variable called totalAmountTea and set it to 35 (number of teabags).
Integer totalAmountTea = 35;
  
//Loop: Add a teaspoon of sugar and one tea bag to a tea cup. Serve until there is no sugar or tea left.
  
While(totalGuests > 0) {
    System.debug(totalGuests + ' Guests Remaining');
    //check ingredients
    if(totalAmountSugar == 0 || totalAmountTea == 0) {
        System.debug('Out of ingredients! Sugar: ' + totalAmountSugar + ' Tea: ' + totalAmountTea);
        break; //ends the While loop
    }
  
    //add sugar
    totalAmountSugar--;
  
    //add tea
    totalAmountTea--;
  
    //guest served
    totalGuests--;
}
```



No, that -- sign is not a typo. It’s called a post-decrement operator. It's a shorthand way of saying, “Subtract one number from this value.” If totalAmountSugar is equal to 159, decrement it so that now the value of totalAmountSugar is equal to 158. The Post Increment Operator, ++, does the opposite, adding one number to the value.

What exactly is going on here? Remember, we have one main goal: serve tea to 100 guests. Each time we serve a guest, a serving of each ingredient (totalAmountSugar and totalAmountTea) and a guest (totalGuests) are deducted. When the totalAmountSugar or the totalAmountTea gets to 0 (line 15) OR the totalGuests gets to 0 (line 12) the loop stops and no one else is served. 

## Do While Loops

A do-while loop allows the code to do something once before the condition is tested.

The do-while loop starts with doing a task once. Next, a condition is verified. If the condition is true, it runs the task again. If it’s false, the loop stops.

![Screenshot 2024-02-12 204953](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/45fd48f0-9783-494e-9cf0-1c3f844ba633)


```java
Do {
    //run this block of code
} while(condition);
```
```java
//Declare an Integer variable called totalGuests and set it to 100
Integer totalGuests = 100;
  
//Declare an Integer variable called totalAmountSugar and set it to 159 (number of teaspoons in a bag of sugar).
Integer totalAmountSugar = 159;
  
//Declare an Integer variable called totalAmountTea and set it to 35 (number of teabags).
Integer totalAmountTea = 35;
  
do {
    //deduct sugar serving
    totalAmountSugar--;
  
    //deduct tea serving
    totalAmountTea--;
  
    //deduct guest
    totalGuests--;
  
    System.debug(totalGuests + ' Guests Remaining!');
  
    //check ingredients
    if(totalAmountSugar == 0 || totalAmountTea == 0) {
        System.debug('Out of ingredients!');
        break; //ends the While loop
    }
  
} while(totalGuests > 0);
```






























     
     

