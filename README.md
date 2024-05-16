# Trie project   
   
   
### Objective

In this project, our objective is to understand how to use Hashing with Open Addressing technique.


### Concepts

|Concept|	Resources|
|-------|----------|
|Open Addressing concept|[Open Addressing](https://www.scaler.com/topics/data-structures/open-addressing/)|



   
### Problem
   
   
Create an `insert` method to create the below `Trie`:   

Figure 1   

   
### Implementation   

In Node class
- Create a `children` array of type **Node** with a fixed size **26**.
- Create an `isEndOfWord` attribute of type **boolean**.



In Trie class 
- Create an insert method.

In Main
- Create a Trie.
- Insert the below words to the trie:
  Red, Real, Rest, Ready.
  Tea, text, term, team.


  




```java

public class OpenAddressingHashTable {
    private int[] arr;
    private int capacity;
    private int size;

    public OpenAddressingHashTable(int capacity) {
        this.capacity = capacity;
        this.arr = new int[capacity];
        this.size = 0;
    }

    public boolean insert(int key) {
        if (size == capacity)
            return false;

        int index = hash(key);

        while (arr[index] != 0 && arr[index] != -1) {
            index = (index + 1) % capacity;
        }

        arr[index] = key;
        size++;
        return true;
    }

    public boolean search(int key) {
        int index = hash(key);

        while (arr[index] != 0) {
            if (arr[index] == key)
                return true;

            index = (index + 1) % capacity;
        }

        return false;
    }

    public boolean delete(int key) {

         /* write your code here */
    }

    private int hash(int key) {
        return key % capacity;
    }

    public static void main(String[] args) {

        OpenAddressingHashTable hashTable = new OpenAddressingHashTable(10);

        hashTable.insert(5);
        hashTable.insert(15);
        hashTable.insert(25);
        hashTable.insert(35);

        System.out.println("Search 15: " + hashTable.search(15));

        System.out.println("Search 20: " + hashTable.search(20));
    }
}
```
