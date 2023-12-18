---
title: HashMaps, HashSets, Collections, SQL Student Lessons
description: by Tirth T, Haseeb B, Sreeja G, Ekam K, Drew R, Adan R
week: 16
categories: [Java, Tri 2]
type: ccc
tags: [Notebook, Java, Collections, Lesson]
---
## Collections

### What are collections?
Collections are any group of individual objects that are represented as a single unit is known as a Java Collection of Objects. In Java, a separate framework named the “Collection Framework” has been defined in JDK 1.2 which holds all the Java Collection Classes and Interface in it. It works as an interface that defines the highest-level of shared collection behavior, and extends Iterable which allows usage of ForEach loop.
### Types of Collections

- **List:**  
    - Ordered collection
    - Allows duplicate elements
    - Example: **ArrayList** and **LinkedList**

- **Set:**  
    - Unordered collection 
    - No duplicates
    - Example: **HashSet** and **TreeSet**

- **Map:**  
    - Key-pair values
    - Each key must be unique
    - Example: **HashMap** and **TreeMap**

- **Queue:**  
    - Follows First-In-First-Out order
    - Example: **LinkedList** and **PriorityQueue**

- **Deque:**  
    - Double ended queue
    - Insertion and removal at both ends
    - Example: **ArrayDeque**

### Popcorn Hack!
Come up with a real world example in which collections are used! Write your answer below:

Students standing line to leave a classroom, the first people in the line get to leave first.

## HashMaps 

#### What are they? 

Hash Maps are a **data structure** with keys and values; very similar to a Python dictionary. The keys in Hash Maps have a single value assigned to them, which can be accessed by calling the key: 

```
import java.util.HashMap;  //Hashmaps are part of the java.util package

public class PlanetDistances {
    public static void main(String[] args) {

        HashMap<String, Double> hashMap = new HashMap<>();

        // key-value pairs, where the key is the planet (a string) and the value is the double assigned to each key
        hashMap.put("Mercury", 0.39);
        hashMap.put("Venus", 0.72); //adding an element
        hashMap.put("Earth", 1.00);
        hashMap.remove("Earth", 1.00); //removing an element

        // the value 0.39 can be accessed by calling the key "Mercury"
        double value = hashMap.get("Mercury");
        boolean exists = hashMap.containsKey("Mercury"); //you can also check if a key exists
        System.out.println("Mercury is " + value + " astronomical units away from the Sun");
    }
}

PlanetDistances.main(null);
```
