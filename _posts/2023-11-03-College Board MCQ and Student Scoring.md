---
layout: post
title: Week 4 | FRQ Overview
description: Reviewing the 2015 CSA FRQ
courses: { csa: { week: 4 } }
type: hacks
---

# Question 4
## Part A - NumberGroup interface

```java
public interface NumberGroup
{
     public boolean contains(int num);
}
```

This is an interface named `NumberGroup` with a single method `contains(int num)`. Classes that implement this interface are expected to provide an implementation for the `contains` method, which checks if a given number `num` is contained within the group.

## Part B - Range class

```java
public class Range implements NumberGroup
{
    private int[] list;

    public Range(int min, int max)
    {
        list = new int[Math.abs(max - min + 1)];
        for(int i = 0; i < list.length; i++)
            list[i] = min + i;
    }

    public boolean contains(int num)
    {
        for(int n : list)
            if(num == n)
                return true;
        return false;
    }
}
```

This class `Range` implements the `NumberGroup` interface. It represents a range of consecutive integers between `min` and `max` (inclusive). The `contains` method checks if a given number `num` is within the range by iterating through the `list` of integers and returning `true` if it finds a match and `false` otherwise.

## Part C - `contains` method

```java
public boolean contains(int num)
{
    for(NumberGroup n : groupList)
        if(n.contains(num))
            return true;
    return false;
}
```

This method is part of a class that manages a collection of `NumberGroup` objects. It checks if a given number `num` is contained in any of the `NumberGroup` objects stored in the `groupList`. It iterates through the `groupList` and uses the `contains` method of each `NumberGroup` to determine if `num` is contained within any of them. If it finds a match in any of the groups, it returns `true`; otherwise, it returns `false`.

# Original Code
```java
// Question 4

// Part A
public interface NumberGroup
{
     public boolean contains(int num);
}

// Part B
public class Range implements NumberGroup
{
   private int[] list;

   public Range(int min, int max)
   {
      list = a new int[Math.abs(max - min + 1)];
      for(int i = 0; i < list.length; i++)
          list[i] = min + i;
   }

   public boolean contains(int num)
   {
      for(int n: list)
         if(num == n)
            return true;
      return false;
   }
}

// Part C
public boolean contains(int num)
{
   for(NumberGroup n : groupList)
      if(n.contains(num))
         return true;
   return false;
}
```
# Scoring Guidelines
![image](https://github.com/raunak2007/csa-pages/assets/41299387/ca9b3627-4568-47c5-b3b0-752ae873c9a1)
# Diagram to visualize logic of the `contains` method
![image](https://github.com/raunak2007/csa-pages/assets/41299387/2bf865f2-ac50-4f38-abfc-eb1bbfc2c755)


