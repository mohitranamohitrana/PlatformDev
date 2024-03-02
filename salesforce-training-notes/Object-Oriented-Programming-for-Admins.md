# Object-Oriented Programming for Admins

1. The `void` keyword in Java is a reserved type used to specify that a method does not return any data type.
2. the return statement is used for returning a value when the execution of the block is completed. 

## Classes 

A class is a blueprint. Objects are based on classes. A class defines a set of characteristics and behaviors that are common to all objects of that class.

![Screenshot 2024-02-13 121345](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/2484139b-bbe6-4c1a-ade8-21ffefed0675)

![Screenshot 2024-02-13 121416](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/9f8561b6-d029-4b13-a63b-152928446515)

## Methods

Methods are defined within a class. A method describes the behaviors inherited by objects of that class. A class can have one or more methods. The Flower class has three methods (behaviors): grow, pollinate, and wilt.

![Screenshot 2024-02-13 122237](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/ee3e40e4-0407-40ce-bd08-82e7e1e82894)

 A parameter is a variable that serves as a placeholder, waiting to receive a value. Parameters are declared similarly to a variable, with a data type followed by the parameter name. 

![Screenshot 2024-02-28 231318](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/61cdeaea-f49d-4665-b578-af03609076c5)

```java
wilt(4);
public static void wilt(Integer numberOfPetals){
    system.debug(numberOfPetals);
}
```

## Return Types

![Screenshot 2024-02-28 231651](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/27f8f551-6cc0-46b0-9d3e-826618a9734e)

```java
public static Integer wilt(Integer numberOfPetals){
    if(numberOfPetals >= 1){
        numberOfPetals--;
    }
  
    return numberOfPetals;
}
```
 Line 6 uses the return statement, followed by the numberOfPetals variable name, to return the resulting numberOfPetals value.

## Objects

Remember that the Flower class is a blueprint for creating flowers. It has color, height, maxHeight, and numberOfPetals variables. These variables are equal to null (no value), but they can have default values.

An object is an instance of a class. In the same way that kids inherit genetic traits, such as eye color and height, from their parents, objects inherit variables and methods from their classes.

![Screenshot 2024-02-28 232058](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/e5c17608-58b1-4f55-b567-e878ff2a9c24)


The tulip object is an instance of the Flower class. Each of the three flower objects is a specific flower based on the Flower class. To create an instance named tulip, based on the Flower class, use this syntax:

`Flower tulip = new Flower();`

You can use dot notation to call an object's methods. Just add .method(); after the object name. For example:

`tulip.grow();`

##  sObject

An sObject is an Apex data type that corresponds to a Salesforce object (sObject) in an org. sObjects are complex data types that hold multiple values in one variable. They hold a single record of data from a Salesforce object, such as an Account, a Contact, or an Opportunity. Remember from Apex Basics for Admins that variables are like containers. Most variables hold one piece of information. sObjects are containers that hold other containers. The containers within the sObject container may be of different data types, such as string, date, integer or Boolean.

![Screenshot 2024-02-15 153028](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/9a9eea9d-6fc7-43c0-bba0-89b8c63f4793)

```java
public class NewAccounts {
    public static void sObjectsInsert(){
        Account store = new Account();
        store.Name = 'The Tea Factory';
        store.AccountNumber = '356281';
        store.Phone = '555-0158';
        insert store;
    }
}
```

1. Click Debug | Open Execute Anonymous Window.
2. `NewAccounts.sObjectsInsert();`



### Use a Loop to Create Multiple Records

```java
  public class NewAccounts {
    public static void sObjectsInsert(Integer value){
        Integer counter = 1;
        //create a list to add our accounts
        List<Account> teaFactoryAccounts = new List<Account>();
        while(counter <= value){
            //display the current counter value
            System.debug('Counter Value before Incrementing ' + counter);
            //create a new account
            Account store = new Account();
            store.Name = 'The Tea Factory ' + counter;
            store.AccountNumber = '35629' + counter;
            teaFactoryAccounts.add(store);
            System.debug(teaFactoryAccounts);
            //increment the counter
            counter = counter + 1;
            System.debug('Counter Value after incrementing ' + counter);
        }
        System.debug('Size of Account List: ' + teaFactoryAccounts.size() );
        System.debug('Elements in Account List: ' + teaFactoryAccounts);
        //insert all of the accounts in the list
        insert teaFactoryAccounts;
    }
}
```


1. Click Debug | Open Execute Anonymous Window.
2. `NewAccounts.sObjectsInsert(3);`



## Sets

 Unlike a list, a set maintains no particular order for its elements. Because the elements are unordered, a set can't have any duplicates.

 ```java
public class Tea{
    public static void orderTea(){
        Set<String> teaTypes = new Set <String>();
        teaTypes.add('Black');
        teaTypes.add('White');
        teaTypes.add('Herbal');
        system.debug(teaTypes);
    }
}
```

1. Click Debug | Open Execute Anonymous Window.
2. `Tea.orderTea();`

### Add a Duplicate Value to a Set

```java
public static void orderTea(){
    Set<String> teaTypes = new Set <String>{'Black', 'White', 'Herbal'};
    system.debug(teaTypes);
    teaTypes.add('Green');
    teaTypes.add('Black');
    system.debug(teaTypes);
}
```

1. Click Debug | Open Execute Anonymous Window.
2. `Tea.orderTea();`


## Maps

Each item in a map has two parts: a key and a value, known as a key-value pair. Keys and values can be any data type. Although each key is unique, values can be repeated within a map

![Screenshot 2024-02-15 232046](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/188916fc-7c19-47a3-951b-2eee0a58a8ad)

![Screenshot 2024-02-15 232323](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/ecd906cf-0e8f-4cd8-b284-0dedfb87c825)

```java
public static String orderTea(){
    Map <String, String> teaTypes = new Map <String, String>();
    teaTypes.put('Black', 'Earthy');
    teaTypes.put('White', 'Sweet');
    teaTypes.put('Herbal', 'Sweet');
    String flavorProfile = teaTypes.get('Herbal');
    System.debug('The flavorProfile of Herbal is: ' + flavorProfile);
    return flavorProfile;
}
```
![Screenshot 2024-02-28 233423](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/94a7c849-6ad1-4f83-b75a-fb20b82f926b)



## Traditional For Loop


![Screenshot 2024-02-15 233511](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/d7c98f07-de0f-44bd-a2f7-cecc9d66ed60)

![Screenshot 2024-02-15 233541](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/10a5380b-ac74-4be4-a6bb-1c90195b573b)


So, if `while` and` do-while` loops do the same thing as `for` loops, why do we use `for` loops at all? Two reasons: 

For loops are used when you know how many times the loop should run. If you want the loop to stop based on a condition other than the number of times it runs you should use the while loop.
For loops are more concise because they keep the three parts—the variable, the condition, and the increment—together in one statement.


### While Loop

```java
Integer i = 0;
while (i < 5){
    System.debug('The number is ' + i);
    i++;
}
```

### For Loop

```java
for(Integer i = 0; i < 5; i++){
    System.debug('The number is ' + i );
}
```
The for loop code is more compact. It does the same thing as the while loop, but does it with three lines of code instead of five. Two more lines of code may sound like a small difference now, but when your org has thousands of lines of code, each additional line matters.


## List or Set Iteration For Loops

The syntax for an iteration for loop is a little different than the traditional for loop syntax. When you declare an iteration for loop, the data type of the variable must match the data type of the list or set.

```java
for (data_type variable_name : list_name or set_name){
    // Loop body
}
```

### Write an Iteration For Loop

`for (String t : tea) `
This statement does two things before the loop begins.

Declares the t variable with the string data type (which matches the data type of the list).
Specifies the tea list as the list that the loop iterates through.


```java
List <String> tea = new List<String>{'Black Tea', 'Green Tea', 'Chai Tea'};
for(String t : tea){
    System.debug('We have ' + t);
}
```

![Screenshot 2024-02-28 234046](https://github.com/mohitranamohitrana/platformADVANCEDcopy/assets/152870513/93896d8f-f9e7-4099-b903-2c7672d4a9ba)









