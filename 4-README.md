# Ex.No:4(A) EXCEPTION HANDLING

## QUESTION:
You wrote a program that stores some input strings into a String array and prints each string in uppercase.
However, you're getting a NullPointerException.
What should you check in your array before calling .toUpperCase() on a element?



## AIM:
To write a Java program that demonstrates a NullPointerException when calling .toUpperCase() on a null string, and to show how to handle it safely.

## ALGORITHM :
1. Read a string input from the user.

2. If the user types "null" (case-insensitive), assign the variable str to null; otherwise assign the input string.

3. Use a try block to call str.toUpperCase().

4. If str is null, a NullPointerException will occur and be caught in the catch block.

5. Print "Null element" when the exception is caught.

6. Close the scanner.



## PROGRAM:
 ```
/*
Program to implement a Exception Handling using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class NullPointerArrayExample {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        String input = sc.nextLine();
        String str = input.equalsIgnoreCase("null") ? null : input;

        try {
            System.out.println(str.toUpperCase());
        } catch (NullPointerException e) {
            System.out.println("Null element");
        }

        sc.close();
    }
}
```


## OUTPUT:
<img width="624" height="359" alt="image" src="https://github.com/user-attachments/assets/8c3a3da5-a663-4aa0-8433-b5ca5dbd4108" />


## RESULT:
Therefore the program successfully demonstrates how a NullPointerException occurs when calling .toUpperCase() on a null value.




# Ex.No:4(B)  IMPLEMENT SOLID PRINCIPLES IN JAVA PROGRAM 

## QUESTION:
At an international airport, only one Radar Control Tower exists. This tower is responsible for handling all flight communications regardless of how many flights are coming in. Each incoming flight must contact this tower to register its approach.

To ensure safety and consistency, all flights must communicate with the same instance of the tower. If multiple towers are created, it may lead to inconsistent instructions — a huge risk in aviation.

Your task is to simulate this system using the Singleton pattern.

## AIM:
To simulate an airport radar communication system using the Singleton pattern, ensuring that all incoming flights register through a single shared instance of the RadarControlTower.

## ALGORITHM :
1. Create a class RadarControlTower with a private static instance variable and  private constructor to prevent multiple object creation.

2. A static getInstance() method that creates the object only once and returns the same instance each time.

3. A registerFlight() method to store flight names and return the count.

4. Read the number of incoming flights.

5. For each flight, read the flight name.

6. Get the Singleton instance using RadarControlTower.getInstance().

7. Register the flight and print the updated total.

8. Ensure every flight interacts with the same RadarControlTower instance.





## PROGRAM:
 ```
/*
Program to implement a SOLID Principles in Java Program
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.*;

class RadarControlTower {
    private static RadarControlTower instance = null;
    private List<String> flights;
    private RadarControlTower() {
        flights = new ArrayList<>();
    }
    public static RadarControlTower getInstance() {
        if (instance == null) {
            instance = new RadarControlTower();
        }
        return instance;
    }
    public int registerFlight(String flightName) {
        flights.add(flightName);
        return flights.size();
    }
}

public class prog {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        sc.nextLine();
        for (int i = 0; i < n; i++) {
            String flight = sc.nextLine();
            RadarControlTower tower = RadarControlTower.getInstance();
            int total = tower.registerFlight(flight);
            System.out.println(flight + " registered with Radar Control Tower. Total Flights: " + total);
        }
    }
}
```


## OUTPUT:
<img width="1208" height="379" alt="image" src="https://github.com/user-attachments/assets/5fb14572-34c6-451b-a4fd-0df6aee4fc3c" />



## RESULT:
Therefore the program successfully ensures that all flights communicate with a single RadarControlTower instance using the Singleton pattern.





# Ex.No:4(C)  COMPOSITION IN JAVA

## QUESTION:
A Department contains Professor objects, but professors can exist independently.
If no inputs gets passed, print "No professors assigned."

## AIM:
To write a Java program demonstrating aggregation, where a Department contains multiple Professor objects, but professors can exist independently. If no professors are assigned, the program should display "No professors assigned.".

## ALGORITHM :
1. Create a Professor class with a name attribute and a constructor to initialize it.

2. Create a Department class with a department name,an array of Professor objects,a counter to track assigned professors.

3. Implement addProfessor() to store a professor in the array.

4. Implement showProfessors() which prints the department name,checks whether any professors are assigned, prints "No professors assigned." if the count is zero,  otherwise prints the list of professors.

5. Read the number of professors.

6. Create professor objects only if input is provided.

7. Read department name (with fallback default).

8. Create a Department object and add professor objects into it.

9. Call showProfessors() to display the results.





## PROGRAM:
 ```
/*
Program to implement a Composition Concepts in Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.*;

class Professor {
    String name;
    Professor(String name) {
        this.name = name;
    }
}

class Department {
    String name;
    Professor[] professors;
    int count = 0;

    Department(String name, int n) {
        this.name = name;
        professors = new Professor[n];
    }

    void addProfessor(Professor p) {
        professors[count++] = p;
    }

    void showProfessors() {
        System.out.println("Department: " + name);
        if (count == 0) {
            System.out.println("No professors assigned.");
        } else {
            for (int i = 0; i < count; i++) {
                System.out.println("- " + professors[i].name);
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        sc.nextLine(); // consume newline

        Professor[] profs = new Professor[n];
        for (int i = 0; i < n; i++) {
            if (sc.hasNextLine()) {
                profs[i] = new Professor(sc.nextLine());
            }
        }

        String deptName = "Computer Science";
        if (sc.hasNextLine()) {
            deptName = sc.nextLine().replace("Department: ", "");
        }

        Department dept = new Department(deptName, n);
        for (Professor p : profs) {
            dept.addProfessor(p);
        }

        dept.showProfessors();
        sc.close();
    }
}
```


## OUTPUT:
<img width="828" height="292" alt="image" src="https://github.com/user-attachments/assets/4e69935f-7724-441c-b2cb-952384232733" />



## RESULT:
Therefore the program successfully demonstrates aggregation by associating independent Professor objects with a Department.




# Ex.No:4(D) DESIGN PATTERN -- ABSTRACT FACTORY

## QUESTION:
Create a program that sends different types of notifications: "email", "sms", and "push". Use the Factory Pattern to generate the appropriate notification sender and call its notifyUser() method.

## AIM:
To develop a Java program that uses the Factory Pattern to generate different types of notifications—Email, SMS, and Push—and call the appropriate notifyUser() method based on user input.

## ALGORITHM :
1. Define a Notification interface with a method notifyUser().

2. Implement three classes EmailNotification, SMSNotification, and PushNotification, each overriding notifyUser() with specific behavior.

3. Create a NotificationFactory class containing a method createNotification(String type) that:

4. Returns an EmailNotification object when type is "email".

5. Returns an SMSNotification object when type is "sms".

6. Returns a PushNotification object when type is "push".

7. Returns null for invalid types.

8. Create a NotificationFactory object.

9. Read user input in a loop until "exit" is entered.

10. Use the factory to create the correct notification object.

11. If the object is valid, call notifyUser(); otherwise print an error message.

12. Close the scanner after exiting the loop.





## PROGRAM:
 ```
/*
Program to implement a Abstract Factory Pattern using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

interface Notification {
    void notifyUser();
}

class EmailNotification implements Notification {
    public void notifyUser() {
        System.out.println("Sending Email Notification");
    }
}

class SMSNotification implements Notification {
    public void notifyUser() {
        System.out.println("Sending SMS Notification");
    }
}

class PushNotification implements Notification {
    public void notifyUser() {
        System.out.println("Sending Push Notification");
    }
}

class NotificationFactory {
    public Notification createNotification(String type) {
        if (type == null) return null;
        if (type.equalsIgnoreCase("email")) return new EmailNotification();
        else if (type.equalsIgnoreCase("sms")) return new SMSNotification();
        else if (type.equalsIgnoreCase("push")) return new PushNotification();
        return null;
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        NotificationFactory factory = new NotificationFactory();
        while (true) {
            String input = sc.nextLine();
            if (input.equalsIgnoreCase("exit")) break;
            Notification n = factory.createNotification(input);
            if (n != null) n.notifyUser();
            else System.out.println("Invalid notification type: " + input);
        }
        sc.close();
    }
}
```





## OUTPUT:
<img width="943" height="423" alt="image" src="https://github.com/user-attachments/assets/4bf885fa-c016-47dd-bfe0-edf37e8a39e5" />


## RESULT:
Therefore the program successfully creates and sends the appropriate notification type using the Factory Pattern.




# Ex.No:4(E) DESIGN PATTERN  ---- MEDIATOR PATTERN

## QUESTION:
Create a ChatRoom class (mediator) and two users (colleagues) who send and receive messages through it. No direct communication allowed.

## AIM:
Implement the Mediator pattern using a ChatRoom class to manage communication between User objects, preventing direct interaction.

## ALGORITHM :
1. Create a ChatRoom class that holds a collection of users, registers users using registerUser(), delivers messages using sendMessage(from, to, message).

2. Create a User class containing a user name, a reference to the ChatRoom mediator, a send() method that passes messages to the chat room, a receive() method to display incoming messages.

3. Read two user names and create User objects, automatically registering them with the chat room.

4. Read the number of chat exchanges.

5. For each exchange read sender, receiver, and message, call the corresponding user’s send() method.

6. Ensure all communication happens only through the mediator (ChatRoom), not directly between users.




## PROGRAM:
 ```
/*
Program to implement a  Pattern using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.*;

class ChatRoom {
    private Map<String, User> users = new HashMap<>();

    public void registerUser(User user) {
        users.put(user.getName(), user);
    }

    public void sendMessage(String from, String to, String message) {
        User receiver = users.get(to);
        if (receiver != null) {
            receiver.receive(from, message);
        } else {
            System.out.println("User " + to + " not found");
        }
    }
}

class User {
    private String name;
    private ChatRoom chatRoom;

    public User(String name, ChatRoom chatRoom) {
        this.name = name;
        this.chatRoom = chatRoom;
        chatRoom.registerUser(this);
    }

    public String getName() {
        return name;
    }

    public void send(String to, String message) {
        chatRoom.sendMessage(name, to, message);
    }

    public void receive(String from, String message) {
        System.out.println(from + " to " + name + ": " + message);
    }
}

public class ChatApp {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        ChatRoom room = new ChatRoom();
        User user1 = new User(sc.nextLine(), room); 
        User user2 = new User(sc.nextLine(), room);

        int n = Integer.parseInt(sc.nextLine());
        for (int i = 0; i < n; i++) {
            String sender = sc.nextLine();
            String receiver = sc.nextLine();
            String message = sc.nextLine();

            if (sender.equals(user1.getName())) {
                user1.send(receiver, message);
            } else if (sender.equals(user2.getName())) {
                user2.send(receiver, message);
            } else {
                System.out.println("Unknown sender");
            }
        }

        sc.close();
    }
}
```


## OUTPUT:
<img width="1143" height="846" alt="image" src="https://github.com/user-attachments/assets/e6ccf91b-1c65-4d94-bfdc-ddf4f68b9ad1" />



## RESULT:
Therefore the program successfully demonstrates message exchange using the Mediator Pattern, with all user communication routed through the ChatRoom.






