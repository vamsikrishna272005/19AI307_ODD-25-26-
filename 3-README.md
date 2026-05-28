# Ex.No:3(A) INHERITANCE AND AGGREGATION

## QUESTION:
A jewelry store tracks gold rates for different types of customers. The base class is Customer with attributes like customerId, name, and purchaseWeight (in grams). There are two types of customers: RegularCustomer and PremiumCustomer. RegularCustomer gets a fixed discount of 2% on the gold rate per gram. PremiumCustomer gets a 5% discount plus a special cashback. The base gold rate per gram is input at runtime. For each customer, calculate the final price they pay:

       
       
      finalPrice = purchaseWeight * (goldRatePerGram - discount)


For PremiumCustomer, additionally show cashback amount (which is 1% of the final price).

## AIM:
To build an inheritance-based Java program that calculates the final price of gold for different types of customers (Regular and Premium), applying respective discounts and showing cashback for premium customers.

## ALGORITHM :
1. Create a base class Customer with attributes: customerId, name, purchaseWeight, and goldRatePerGram.

2. Create method getDiscountRate() in base class returning 0 (default).

3. Create method calculateFinalPrice() that:

        calculates discount per gram → discountAmount = goldRatePerGram * (discountRate/100)

        calculates effective rate → effectiveRate = goldRatePerGram - discountAmount

  returns → finalPrice = purchaseWeight * effectiveRate

4. Override display() in base class to show general customer details.

5. Create child class RegularCustomer:

       Override getDiscountRate() to return 2%.

       Override display() to show customer type as Regular.

6. Create child class PremiumCustomer:

       Override getDiscountRate() to return 5%.

7.  Add calculateCashback() → returns 1% of final price.

8.  Override display() to show final price + cashback.

9.  Call display() to show the complete bill with discounts.





## PROGRAM:
 ```
/*
Program to implement a Inheritance and Aggregation using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;
import java.text.DecimalFormat;

class Customer {
    String customerId, name;
    double purchaseWeight, goldRatePerGram;

    Customer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        this.customerId = customerId;
        this.name = name;
        this.purchaseWeight = purchaseWeight;
        this.goldRatePerGram = goldRatePerGram;
    }

    double getDiscountRate() {
        return 0;
    }

    double calculateFinalPrice() {
        double discountAmount = goldRatePerGram * getDiscountRate() / 100;
        double effectiveRate = goldRatePerGram - discountAmount;
        return purchaseWeight * effectiveRate;
    }

    void display() {
        DecimalFormat df = new DecimalFormat("0.00");
        System.out.println("Customer ID: " + customerId);
        System.out.println("Name: " + name);
        System.out.println("Customer Type: General");
        System.out.println("Purchase Weight: " + purchaseWeight + " grams");
        System.out.println("Gold Rate per Gram: " + goldRatePerGram);
        System.out.println("Discount: " + getDiscountRate() + "%");
        System.out.println("Final Price: " + df.format(calculateFinalPrice()));
        
    }
}

class RegularCustomer extends Customer {

    RegularCustomer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        super(customerId, name, purchaseWeight, goldRatePerGram);
    }

    @Override
    double getDiscountRate() {
        return 2.0;
    }

    @Override
    void display() {
        DecimalFormat df = new DecimalFormat("0.00");
        System.out.println("Customer ID: " + customerId);
        System.out.println("Name: " + name);
        System.out.println("Customer Type: Regular");
        System.out.println("Purchase Weight: " + purchaseWeight + " grams");
        System.out.println("Gold Rate per Gram: " + goldRatePerGram);
        System.out.println("Discount: 2%");
        System.out.println("Final Price: " + df.format(calculateFinalPrice()));
       
    }
}

class PremiumCustomer extends Customer {

    PremiumCustomer(String customerId, String name, double purchaseWeight, double goldRatePerGram) {
        super(customerId, name, purchaseWeight, goldRatePerGram);
    }

    @Override
    double getDiscountRate() {
        return 5.0;
    }

    double calculateCashback() {
        return calculateFinalPrice() * 0.01;
    }

    @Override
    void display() {
        DecimalFormat df = new DecimalFormat("0.00");
        System.out.println("Customer ID: " + customerId);
        System.out.println("Name: " + name);
        System.out.println("Customer Type: Premium");
        System.out.println("Purchase Weight: " + purchaseWeight + " grams");
        System.out.println("Gold Rate per Gram: " + goldRatePerGram);
        System.out.println("Discount: 5%");
        System.out.println("Final Price: " + df.format(calculateFinalPrice()));
        System.out.println("Cashback: " + df.format(calculateCashback()));
        
    }
}

public class GoldRateSystem {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input 1
        String type1 = sc.next();
        Customer cust1;
        if (type1.equalsIgnoreCase("Regular")) {
            cust1 = new RegularCustomer(sc.next(), sc.next(), sc.nextDouble(), sc.nextDouble());
        } else {
            cust1 = new PremiumCustomer(sc.next(), sc.next(), sc.nextDouble(), sc.nextDouble());
        }

        
        cust1.display();
     

        sc.close();
    }
}
```




## OUTPUT:
<img width="884" height="700" alt="image" src="https://github.com/user-attachments/assets/bc4bc233-2418-404a-88cc-490c1d83bc24" />



## RESULT:
Therefore the program successfully applies different discount rules for regular and premium customers.





# Ex.No:3(b) POLYMORPHISM

## QUESTION:
Write a Java program to create a class Vehicle with a method called speedUp(). Create two subclasses Car and Bicycle. Override the speedUp() method in each subclass to increase the vehicle's speed differently.

## AIM:
To create a Java program demonstrating method overriding by defining a base class Vehicle with a speedUp() method and overriding it in subclasses Car and Bicycle to increase speed differently.

## ALGORITHM :
1. Create a parent class Vehicle with an integer variable speed and a method speedUp(int increment) that increases speed normally.

2. Create a subclass Car that overrides speedUp() to increase speed by double the increment.

3. Create a subclass Bicycle that overrides speedUp() to increase speed normally (same as parent but customized message).

4. Read vehicle type and increment value from user.

5. Based on the type, create an object of Car, Bicycle, or Vehicle.

6. Call the speedUp(increment) method to show polymorphic behavior.




## PROGRAM:
 ```
/*
Program to implement a Polymorphism using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
```

## SOURCE CODE:
```
import java.util.Scanner;

// Parent class
class Vehicle {
    int speed = 0;

    void speedUp(int increment) {
        speed += increment;
        System.out.println("Vehicle speed increased to: " + speed + " km/h");
    }
}


class Car extends Vehicle {
    @Override
    void speedUp(int increment) {
        speed += increment * 2;
        System.out.println("Car speed increased to: " + speed + " km/h");
    }
}


class Bicycle extends Vehicle {
    @Override
    void speedUp(int increment) {
        speed += increment;
        System.out.println("Bicycle speed increased to: " + speed + " km/h");
    }
}


public class TestVehicles {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String type = sc.nextLine().toLowerCase();
        int increment = sc.nextInt();

        Vehicle vehicle;
        if (type.equals("car")) {
            vehicle = new Car();
        } else if (type.equals("bicycle")) {
            vehicle = new Bicycle();
        } else {
            vehicle = new Vehicle();
        }

        vehicle.speedUp(increment);
    }
}
```






## OUTPUT:
<img width="921" height="437" alt="image" src="https://github.com/user-attachments/assets/5c317382-efe2-4ec9-a2cf-67b2d4db68b4" />



## RESULT:
Therefore the  program successfully demonstrates method overriding by applying different speed increase behaviors for car and bicycle.





# Ex.No:3(C) ABSTRACTION

## QUESTION:
In a secret intelligence facility, encrypted messages are stored as arrays of characters. Each type of agent has a different way to decode these messages. Define an abstract class Decoder with a method decodeMessage(String[] fragments).
There are two types of agents:

   AlphaAgent: Extracts a meaningful string by rearranging the fragments based on even indices first, then odd indices, and then reversing the final result.

   BetaAgent: Picks all fragments that start and end with the same letter, joins them with -, and removes all vowels from the resulting string.


## AIM:
To create an abstract class Decoder with an abstract method decodeMessage(), and implement two subclasses, AlphaAgent and BetaAgent, each with a unique decoding technique for encrypted message fragments.

## ALGORITHM :
1. Create an abstract class Decoder containing an abstract method decodeMessage(String[] fragments).

2. Create subclass AlphaAgent implementing decodeMessage() by collecting fragments at even indices,then collecting fragments at odd indices,reversing the combined list.

3. Joining all fragments into one decoded string.

4. Create subclass BetaAgent implementing decodeMessage() by selecting fragments whose first and last characters match (case-insensitive).

5. Joining selected fragments using -.

6. Removing all vowels from the final combined string.

7. Read number of fragments and store them in a string array.

8. Read agent type (1 = AlphaAgent, 2 = BetaAgent).

9. Create the corresponding agent object.

10. Call decodeMessage() and print the decoded output.





## PROGRAM:
 ```
/*
Program to implement a Abstraction using Java
Developed by: VAmsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:

```
import java.util.*;

abstract class Decoder {
    abstract String decodeMessage(String[] fragments);
}


class AlphaAgent extends Decoder {
    @Override
    String decodeMessage(String[] fragments) {
        List<String> ordered = new ArrayList<>();
        
        for (int i = 0; i < fragments.length; i += 2) {
            ordered.add(fragments[i]);
        }
       
        for (int i = 1; i < fragments.length; i += 2) {
            ordered.add(fragments[i]);
        }
       
        Collections.reverse(ordered);
        
        StringBuilder result = new StringBuilder();
        for (String s : ordered) {
            result.append(s);
        }
        return result.toString();
    }
}


class BetaAgent extends Decoder {
    @Override
    String decodeMessage(String[] fragments) {
        List<String> selected = new ArrayList<>();
        for (String f : fragments) {
            if (!f.isEmpty()) {
                char first = Character.toLowerCase(f.charAt(0));
                char last = Character.toLowerCase(f.charAt(f.length() - 1));
                if (first == last) {
                    selected.add(f);
                }
            }
        }

        String joined = String.join("-", selected);
        return joined.replaceAll("[AEIOUaeiou]", "");
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = Integer.parseInt(sc.nextLine().trim());
        String[] fragments = new String[n];
        for (int i = 0; i < n; i++) {
            fragments[i] = sc.nextLine().trim();
        }
        int type = Integer.parseInt(sc.nextLine().trim());

        Decoder agent;
        if (type == 1)
            agent = new AlphaAgent();
        else
            agent = new BetaAgent();

        System.out.println(agent.decodeMessage(fragments));
        sc.close();
    }
}
```





## OUTPUT:
<img width="791" height="586" alt="image" src="https://github.com/user-attachments/assets/8e5ac67e-a125-4db4-b804-52e16025fa7e" />



## RESULT:
Therefore the program successfully decodes messages using the rules defined for AlphaAgent and BetaAgent.





# Ex.No:3(D)    INTERFACE 

## QUESTION:
You’re developing a multi-console gaming platform that supports different controllers. Each controller has its own way of mapping buttons for actions like Jump, Shoot, and Pause.

To unify this behavior, you're asked to design a system using Java Interfaces. The interface will standardize the controls, and each controller will implement them differently.

Your Task:
Create an interface GameController with methods:

jump()
shoot()
pause()
Implement three controller types:

PlayBoxController
XCubeController
RetroFunController

## AIM:
To design a unified controller system using Java Interfaces where different gaming consoles implement their own button mappings for actions like Jump, Shoot, and Pause.

## ALGORITHM :
1. Define an interface GameController with methods :jump(),shoot(),pause()

2. Create class PlayBoxController implementing the interface and defining console-specific button actions.

3. Create class XCubeController implementing the interface with its own button mapping.

4. Create class RetroFunController implementing the interface using classic button controls.

5. Create one controller object at a time.

6. Call the three methods (jump, shoot, pause) to demonstrate polymorphism.




## PROGRAM:
 ```
/*
Program to implement a Interface using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.*;

interface GameController {
    void jump();
    void shoot();
    void pause();
}

class PlayBoxController implements GameController {
    public void jump() {
        System.out.println("PlayBox: Press X to Jump!");
    }
    public void shoot() {
        System.out.println("PlayBox: Press R2 to Shoot!");
    }
    public void pause() {
        System.out.println("PlayBox: Press Start to Pause.");
    }
}

class XCubeController implements GameController {
    public void jump() {
        System.out.println("X-Cube: Press A to Jump!");
    }
    public void shoot() {
        System.out.println("X-Cube: Press RT to Shoot!");
    }
    public void pause() {
        System.out.println("X-Cube: Press Menu to Pause.");
    }
}

class RetroFunController implements GameController {
    public void jump() {
        System.out.println("RetroFun: Use Up Arrow to Jump!");
    }
    public void shoot() {
        System.out.println("RetroFun: Press B to Shoot!");
    }
    public void pause() {
        System.out.println("RetroFun: Press P to Pause.");
    }
}

public class GameInputSimulator {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String controllerType = sc.nextLine().toLowerCase();
        String action = sc.nextLine().toLowerCase();

        GameController controller;

        switch (controllerType) {
            case "playbox":
                controller = new PlayBoxController();
                break;
            case "xcube":
                controller = new XCubeController();
                break;
            case "retro":
                controller = new RetroFunController();
                break;
            default:
                System.out.println("Unsupported controller!");
                return;
        }

        switch (action) {
            case "jump":
                controller.jump();
                break;
            case "shoot":
                controller.shoot();
                break;
            case "pause":
                controller.pause();
                break;
            default:
                System.out.println("Unknown action!");
        }
    }
}

```




## OUTPUT:
<img width="821" height="293" alt="image" src="https://github.com/user-attachments/assets/77adba3b-7948-47f4-a6ed-f87b7e0eb83b" />


## RESULT:
Therefore the program successfully unifies different gaming controllers using a common interface.




# Ex.No:3(E) ENUM

## QUESTION:
Write a Java program to define an enum named GameLevel with three constants: EASY, MEDIUM, and HARD.

## AIM:
To write a Java program that defines an enum named GameLevel with constants EASY, MEDIUM, and HARD, and allows the user to select a game level.

## ALGORITHM :
1. Define an enum GameLevel with constants: EASY, MEDIUM, HARD.

2. Read user input as a string and convert it to uppercase.

3. Use GameLevel.valueOf() to match the input with an enum constant.

4. If the value matches, print the selected game level.

5. If no match is found, catch IllegalArgumentException and show an error message.

6. Close the scanner in the finally block.




## PROGRAM:
 ```
/*
Program to implement a InnerClass using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

enum GameLevel {
    EASY, MEDIUM, HARD;
}

public class Game {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String userInput = scanner.nextLine().toUpperCase();

        try {
            GameLevel level = GameLevel.valueOf(userInput);
            System.out.println("You selected game level: " + level);
        } catch (IllegalArgumentException e) {
            System.out.println("Invalid game level entered.");
        } finally {
            scanner.close();
        }
    }
}

```




## OUTPUT:
<img width="815" height="326" alt="image" src="https://github.com/user-attachments/assets/fe75fd02-00e4-4672-8233-93e35f565e9f" />



## RESULT:
Therefore the program successfully reads a game level from the user and maps it to the corresponding enum constant.





# Ex.No:3(F) WRAPPER CLASS

## QUESTION:
Write a Java program to check if a number is prime using wrapper classes. 

## AIM:
To write a Java program that checks whether a given number is prime by using the Integer wrapper class for parsing and handling the input.

## ALGORITHM :
1. Read input from the user as a string.

2. Use the Integer.parseInt() method (wrapper class) to convert the input into an integer.

3. If parsing fails, catch NumberFormatException and display an error message.

4. If the number is less than or equal to 1, it is not prime.

5. If any divisor divides the number completely, mark it as not prime.

6. After checking, print whether the number is prime or not.

7. Close the scanner.




## PROGRAM:
 ```
/*
Program to implement a InnerClass using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class PrimeChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        
        String input = scanner.nextLine();

        try {
            Integer number = Integer.parseInt(input); // Using Integer wrapper class

            if (number <= 1) {
                System.out.println(number + " is not a prime number.");
            } else {
                boolean isPrime = true;
                for (int i = 2; i <= Math.sqrt(number); i++) {
                    if (number % i == 0) {
                        isPrime = false;
                        break;
                    }
                }

                if (isPrime) {
                    System.out.println(number + " is a prime number.");
                } else {
                    System.out.println(number + " is not a prime number.");
                }
            }

        } catch (NumberFormatException e) {
            System.out.println("Invalid input. Please enter a valid integer.");
        }

        scanner.close();
    }
}
```






## OUTPUT:
<img width="893" height="258" alt="image" src="https://github.com/user-attachments/assets/2cfce946-0ad1-43c0-a0b9-9f1d4d27a34b" />



## RESULT:
Therefore the program successfully checks if the input number is a prime using the Integer wrapper class.







