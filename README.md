## Different ways to create objects in Java:
### 1. Using new keyword:
By using this method we can call any constructor (no argument or parameterized constructors).

ex. 
```
GFG obj = new GFG();
```

### 2. Using new instance:

If we know the name of the class & if it has a public default constructor.

ex.
```
Class cls = Class.forName("GFG"); //actually loads the Class in Java but doesn’t create any Object
GFG obj = (GFG)cls.newInstance(); //Creating object
```

### 3. Using clone() method:
Whenever clone() is called on any object, the JVM actually creates a new object and copies all content of the previous object into it. 

Creating an object using the clone method does not invoke any constructor.

Here we are creating the clone of an existing Object and not any new Object.

Class need to implement Cloneable Interface otherwise it will throw CloneNotSupportedException.

ex.
```
// Implementing Cloneable interface 
class GFG implements Cloneable { 
  
    @Override
    protected Object clone() 
        throws CloneNotSupportedException 
    { 
        // Super() keyword refers to parent class 
        return super.clone(); 
    } 
    //other line of code
}

GFG obj1 = new GFG();
GFG obj2 = (GFG)obj1.clone(); 
```


### 4. Using deserialization:
Whenever we serialize and then deserialize an object, JVM creates a separate object.
In deserialization, JVM doesn’t use any constructor to create the object.
To deserialize an object we need to implement the Serializable interface in the class.

#### Serialization: (object -> byte Stream)
Serialization in Java is the process of converting an object's state into a byte stream, which can then be used to save the object or transmit it over a network

Serialization is useful for saving data, transmitting information, and storing objects in a database. It's often used in Hibernate, JMS, JPA, and EJB

Serialization and deserialization can have security implications, so it's important to be careful with serialized objects from untrusted sources.

To avoid compromising a class, you can mark fields that contain sensitive data as private transient.

Some objects, such as threads, sockets, and file handles, cannot be serialized.

#### Deserialization:(byte Stream -> object)
Deserialization is the process of reconstructing the object from the serialized state. It is the reverse operation of serialization.

ex.
```
class GFG implements Serializable { 
    //code
}

GFG d = new GFG("GeeksForGeeks"); 
FileOutputStream f = new FileOutputStream("file.txt"); 
ObjectOutputStream oos  = new ObjectOutputStream(f); 
oos.writeObject(d); 
oos.close(); 
// Freeing up memory resources 
f.close(); 
           
FileInputStream f = new FileInputStream("file.txt"); 
ObjectInputStream oos = new ObjectInputStream(f); 
GFG d = (DeserializationExample)oos.readObject(); 
```


### 5. Using newInstance() method of Constructor class:
There is one newInstance() method in the java.lang.reflect.Constructor class which we can use to create objects.

It can also call the parameterized constructor, and private constructor by using this newInstance() method.

Both newInstance() methods are known as reflective ways to create objects.

In fact newInstance() method of Class internally uses newInstance() method of Constructor class. 
ex.
```
Constructor<GFG> constructor = GFG.class.getDeclaredConstructor(); 
GFG r = constructor.newInstance(); 
```



## Design Patterns:
Reusable solution for common problems in software design.

Refer to structured approaches involving objects and classes that aim to solve recurring design issues within specific contexts.

These patterns offer reusable, general solutions to common problems encountered in software development, representing established best practices

### There are three types of Design Patterns:

### 1. Creational Design Pattern
Focus on the process of creating objects. 

Aim to enhance flexibility and efficiency in object creation, allowing systems to remain independent of how their objects are constructed, composed, and represented.

ex. Factory, Singleton, Prototype, Builder

### 2. Structural Design Pattern
Focus on how classes and objects are arranged to create larger, more complex structures in software development. 

They help organize relationships between objects, making systems more flexible, reusable, and maintainable.

ex. Adapter, Proxy, Bridge

### 3. Behavioural Design Pattern
Focus on how objects and classes interact and communicate in software development. 

They emphasize the collaboration between objects to effectively accomplish tasks and responsibilities, making the system more manageable and adaptable

ex. Interpreter, template, iterator

#### Note: Scope of these design pattern can be Class/Object







