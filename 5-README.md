# Ex.No:5(A) INPUTSTREAMREADER 

## QUESTION:
Write a program to demonstrate chaining of streams (BufferedReader on top of InputStreamReader on top of System.in)

## AIM:
To write a Java program that demonstrates stream chaining by placing a BufferedReader on top of an InputStreamReader, which in turn wraps System.in, and then reading user input using this chained stream.

## ALGORITHM :
1. Create a BufferedReader object by chaining:

2. System.in → InputStreamReader → BufferedReader.

3. Inside a try block Use readLine() to read the user's name.

4. Use readLine() again to read the user's age.

5. Print the collected details.

6. Catch any IOException and display an appropriate error message.



## PROGRAM:
 ```
/*
Program to implement a InputStreamReader using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class ChainingStreamsExample {
    public static void main(String[] args) {
        // Chaining: System.in -> InputStreamReader -> BufferedReader
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        try {
            String name = br.readLine();
            String age = br.readLine();
            System.out.println("--- User Details ---");
            System.out.println("Name: " + name);
            System.out.println("Age: " + age);
        } catch (IOException e) {
            System.out.println("An error occurred: " + e.getMessage());
        }
    }
}
```


## OUTPUT:
<img width="827" height="557" alt="image" src="https://github.com/user-attachments/assets/b647d19d-16b6-48c7-8343-acca2fb720ec" />


## RESULT:
Therefore the program successfully demonstrates chaining of input streams by reading user data through a BufferedReader wrapped over an InputStreamReader.





# Ex.No:5(B) SERIALIZATION AND DESERIALIZATION 

## QUESTION:
Write a Java program to serialize a collection of objects (like ArrayList<Student>) into a file.

## AIM:
To write a Java program that serializes a collection of Student objects (ArrayList<Student>) into a file and deserializes it back, demonstrating object persistence using Java Serialization.

## ALGORITHM :
1. Create a Student class and implement the Serializable interface.

2. Store id, name, and marks as attributes and override toString() for readable output.

3. Read the number of students from the user.

4. For each student, read id, name, and marks and add them to an ArrayList<Student>.

5. Implement serializeStudents() to create an ObjectOutputStream over a FileOutputStream.

6.  Write the list of students into the file.

7. Implement deserializeStudents() to create an ObjectInputStream over a FileInputStream, read the list back into memory.

8. Print the deserialized student objects to verify successful serialization and deserialization.

9. Close the scanner.



## PROGRAM:
 ```
/*
Program to implement a Serialization and Deserialization using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.io.*;
import java.util.*;

// Student class must implement Serializable
class Student implements Serializable {
    private static final long serialVersionUID = 1L;

    private int id;
    private String name;
    private double marks;

    public Student(int id, String name, double marks) {
        this.id = id;
        this.name = name;
        this.marks = marks;
    }

    @Override
    public String toString() {
        return "Student{id=" + id + ", name='" + name + "', marks=" + marks + "}";
    }
}

public class StudentSerializationUserInput {

    // Serialize list of students
    public static void serializeStudents(List<Student> students, String fileName) {
        try (ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(fileName))) {
            oos.writeObject(students);
            System.out.println("Students serialized successfully into: " + fileName);
        } catch (IOException e) {
            System.out.println("Error during serialization: " + e.getMessage());
        }
    }

    // Deserialize list of students
    @SuppressWarnings("unchecked")
    public static List<Student> deserializeStudents(String fileName) {
        List<Student> students = null;
        try (ObjectInputStream ois = new ObjectInputStream(new FileInputStream(fileName))) {
            students = (List<Student>) ois.readObject();
            System.out.println("Students deserialized successfully from: " + fileName);
        } catch (IOException | ClassNotFoundException e) {
            System.out.println("Error during deserialization: " + e.getMessage());
        }
        return students;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        List<Student> students = new ArrayList<>();

        int n = scanner.nextInt();
        scanner.nextLine(); // consume newline

        for (int i = 0; i < n; i++) {
            int id = scanner.nextInt();
            scanner.nextLine();
            String name = scanner.nextLine();
            double marks = scanner.nextDouble();
            if (i < n - 1) scanner.nextLine(); // consume newline
            students.add(new Student(id, name, marks));
        }

        String fileName = "students.dat";
        serializeStudents(students, fileName);

        List<Student> deserializedStudents = deserializeStudents(fileName);

        if (deserializedStudents != null) {
            System.out.println("\nDeserialized Students:");
            for (Student s : deserializedStudents) {
                System.out.println(s);
            }
        }

        scanner.close();
    }
}
```


## OUTPUT:
<img width="1253" height="531" alt="image" src="https://github.com/user-attachments/assets/b017eac9-5975-417a-b46a-fa465087a91b" />



## RESULT:
Therfor the program successfully serializes an ArrayList of Student objects into a file and restores them through deserialization.






# Ex.No:5(C)  FILE HANDLING USING JAVA
## QUESTION:
Write a Java program to create a new file named example.txt.

## AIM:
To write a Java program that creates a new file named example.txt using the File class and handles any possible I/O exceptions.

## ALGORITHM :
1. Create a File object pointing to "example.txt".

2. Call the createNewFile() method to attempt creating the file.

3. If the method returns true, print that the file was created.

4. If it returns false, print that the file already exists.

5. Surround the file-creation logic with a try–catch block to handle IOException.





## PROGRAM:
 ```
/*
Program to implement a File Handling using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.io.File;
import java.io.IOException;

public class CreateNewFileExample {
    public static void main(String[] args) {
        try {
            File file = new File("example.txt");
            if (file.createNewFile()) {
                System.out.println("File created: " + file.getName());
            } else {
                System.out.println("File already exists.");
            }
        } catch (IOException e) {
            System.out.println("An error occurred: " + e.getMessage());
        }
    }
}
```

## OUTPUT:
<img width="768" height="255" alt="image" src="https://github.com/user-attachments/assets/ae4f968a-af58-4f91-8e79-baeea0fd9f29" />


## RESULT:
Therefore the program successfully creates a new file named example.txt if it does not already exist.





# Ex.No:5(D) THREAD PRIORITY

## QUESTION:
Write a Java program to implement a extending thread class

## AIM:
To write a Java program that demonstrates multithreading by creating a user-defined thread class that extends Thread and executes its own run() method.

## ALGORITHM :
1. Create a class MyThread that extends the Thread class.

2. Override the run() method to print numbers from 1 to 5.

3. In the main() method: Print a message indicating the main thread execution.

4. Create an instance of MyThread.

5. Call the start() method to begin execution in a separate thread.

6. Allow the thread to run independently from the main thread.





## PROGRAM:
 ```
/*
Program to implement a Thread Priority Concept using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
public class MyThread extends Thread {
    public void run() {
        for (int i = 1; i <= 5; i++) {
            System.out.println("Thread: " + i);
        }
       
    }

    public static void main(String[] args) {
        System.out.println("Main thread finished");
        MyThread t = new MyThread();
        t.start();
    }
}
```


## OUTPUT:
<img width="612" height="355" alt="image" src="https://github.com/user-attachments/assets/b583e00e-99ec-4ea3-b48f-e1305b42e783" />



## RESULT:
Therefore the program successfully creates a separate thread by extending Thread and executes the overridden run() method.





# Ex.No:5(E) MULTITHREADING -SYNCHRONIZATION

## QUESTION:
Maintain two int variables a and b, read their initial values from user. Use synchronized block to swap them and print swapped values.

## AIM:
To write a Java program that reads two integers from the user and swaps their values using a synchronized block to ensure thread-safe operations.

## ALGORITHM :
1. Read two integer values a and b from the user.

2. Create a lock object to use inside the synchronized block.

3. Enter the synchronized block using the lock object.

4. Swap the values of a and b using a temporary variable.

5. Exit the synchronized block once the swap is complete.

6. Print the swapped values of a and b.

7. Close the scanner.





## PROGRAM:
 ```
/*
Program to implement a Synchronization concept using Java
Developed by: Vamsi Krishna G
RegisterNumber: 212223220120
*/
```

## SOURCE CODE:
```
import java.util.Scanner;

public class SwapUsingSynchronized {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int a = sc.nextInt();
        int b = sc.nextInt();
        Object lock = new Object();

        synchronized (lock) {
            int temp = a;
            a = b;
            b = temp;
        }

        System.out.println("a = " + a);
        System.out.println("b = " + b);
        sc.close();
    }
}
```


## OUTPUT:
<img width="457" height="390" alt="image" src="https://github.com/user-attachments/assets/2fb44153-47e4-4ac3-8872-e321e221fc56" />



## RESULT:
Therefore the program successfully swaps two integers within a synchronized block, ensuring safe and controlled access.





