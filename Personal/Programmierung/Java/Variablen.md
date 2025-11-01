# Java Variablen 
- `String` - stores text, such as "Hello". String values are surrounded by double quotes
- `int` - stores integers (whole numbers), without decimals, such as 123 or -123
- `float` - stores floating point numbers, with decimals, such as 19.99 or -19.99
- `char` - stores single characters, such as 'a' or 'B'. Char values are surrounded by single quotes
- `boolean` - stores values with two states: true or false
- 
## One value to Multiple Variables
```java
int x, y, z;
x = y = z = 50;
System.out.println(x + y + z); // 150
```

### var
var cann be anything » the compieler detects the data type.
var cannt be null 

once the type is choosen it cant be changed

``` Java
var x = 5;  // x is now an int  
x = 10;     // OK - still an int  
x = 9.99;   // Error - can't assign a double to an int
```

## Variables can be widen and Narrowed 
### Widening Casting 
```java
int myInt = 9;
double myDouble = myInt; // Automatic casting: int to double

System.out.println(myInt);    // Outputs 9
System.out.println(myDouble); // Outputs 9.0
```

### Narrowing Casting 
```java
double myDouble = 9.78d;
int myInt = (int) myDouble; // Manual casting: double to int

System.out.println(myDouble); // Outputs 9.78
System.out.println(myInt);    // Outputs 9
```

#### Usage
```java
// Set the maximum possible score in the game to 500
int maxScore = 500;

// The actual score of the user
int userScore = 423;

/* Calculate the percentage of the user's score in relation to the maximum available score.
Convert userScore to double to make sure that the division is accurate */
double percentage = (double) userScore / maxScore * 100.0d;

System.out.println("User's percentage is " + percentage);
```

#Java
#Programmierung
#Personal