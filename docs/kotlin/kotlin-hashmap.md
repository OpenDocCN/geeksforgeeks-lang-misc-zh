# 库根散列图

> 哎哎哎:# t0]https://www . geeksforgeeks . org/kot Lin-hashmap/

[Kotlin](https://www.geeksforgeeks.org/introduction-to-kotlin/) HashMap 是一个包含对象对的集合。基于 Kotlin 哈希表的 MutableMap 接口的实现。它以键和值对的形式存储数据。映射键是唯一的，并且映射只为每个键保存一个值。表示为 *HashMap <键、值>* 或 *HashMap < K、V >* 。

HashMap 的基于哈希表的实现不保证集合的**键**、**值**和**条目**的指定数据的顺序。

### Kotlin HashMap 类的构造函数–

Kotlin HashMap 提供了 4 个构造函数和访问修饰符，每个都是公共的:

*   **HashMap() :** 默认构造函数构造一个空的 HashMap 实例。*   **HashMap(initialCapacity: Int，loadFactor: Float = 0f) :** 用于构造指定容量的 HashMap。如果没有使用初始容量和负载系数，那么两者都将被忽略。*   **HashMap(initial capacity:Int):**用于构造指定容量的 HashMap。如果初始容量没有被使用，那么它将被忽略。*   **HashMap(original: Map <out K, V> ) :** It creates instance of HashMap with same mappings as specified map.

    ### 哈希映射函数的使用–

    **使用函数 hashmap()的 Kotlin 程序，HashMap(原文:Map)，遍历 HashMap，HashMap . get()–**

    ```kt
    fun main(args: Array<String>) {
        //A simple example of HashMap class define
        // with empty "HashMap of <String, Int>"
        var hashMap : HashMap<String, Int>
                = HashMap<String, Int> ()

        //printing the Empty hashMap
        printHashMap(hashMap)

        //adding elements to the hashMap using
        // put() function
        hashMap.put("IronMan" , 3000)
        hashMap.put("Thor" , 100)
        hashMap.put("SpiderMan" , 1100)
        hashMap.put("NickFury" , 1200)
        hashMap.put("HawkEye" , 1300)

        //printing the non-Empty hashMap
        printHashMap(hashMap)
        //using the overloaded print function of
        //Kotlin language to get the same results
        println("hashMap : " + hashMap + "\n")

        //hashMap traversal using a for loop
        for(key in hashMap.keys){
            println("Element at key $key : ${hashMap[key]}")
        }

        //creating another hashMap object with
        // the previous version of hashMap object
        var secondHashMap : HashMap<String, Int>
                = HashMap<String, Int> (hashMap)

        println("\n" + "Second HashMap : ")
        for(key in secondHashMap.keys){
            //using hashMap.get() function to fetch the values
            println("Element at key $key : ${hashMap.get(key)}")
        }

        //this will clear the whole map and make it empty
        println("hashMap.clear()")
        hashMap.clear()

        println("After Clearing : " + hashMap)

    }

    //function to print the hashMap
    fun printHashMap(hashMap : HashMap<String, Int>){
        // isEmpty() function to check whether
        // the hashMap is empty or not
        if(hashMap.isEmpty()){
            println("hashMap is empty")
        }else{
            println("hashMap : " + hashMap)
        }
    }
    ```

    **输出:**

    ```kt
    hashMap is empty : {}

    hashMap : {Thor=100, HawkEye=1300, NickFury=1200, IronMan=3000, SpiderMan=1100}
    hashMap : {Thor=100, HawkEye=1300, NickFury=1200, IronMan=3000, SpiderMan=1100}

    Element at key Thor : 100
    Element at key HawkEye : 1300
    Element at key NickFury : 1200
    Element at key IronMan : 3000
    Element at key SpiderMan : 1100

    secondHashMap : 
    Element at key Thor : 100
    Element at key HawkEye : 1300
    Element at key IronMan : 3000
    Element at key NickFury : 1200
    Element at key SpiderMan : 1100

    hashMap.clear()
    After Clearing : {}

    ```

    **使用 HashMap 初始容量的 Kotlin 程序，HashMap . size–**

    ```kt
    fun main(args: Array<String>) {
        //HashMap can also be initialize
        // with its initial capacity.
        //The capacity can be changed by
        // adding and replacing its element.
        var hashMap : HashMap<String, Int>
                = HashMap<String, Int> (4)

        //adding elements to the hashMap using put() function
        hashMap.put("IronMan" , 3000)
        hashMap.put("Thor" , 100)
        hashMap.put("SpiderMan" , 1100)
        hashMap.put("NickFury" , 1200)

        for(key in hashMap.keys) {
            println("Element at key $key : ${hashMap[key]}")
        }
        //returns the size of hashMap
        println("\n" + "hashMap.size : " + hashMap.size )

        //adding a new element in the hashMap
        hashMap["BlackWidow"] = 1000;
        println("hashMap.size : " + hashMap.size + "\n")

        for(key in hashMap.keys) {
            println("Element at key $key : ${hashMap[key]}")
        }
    }
    ```

    **输出:**

    ```kt
    Element at key Thor : 100
    Element at key IronMan : 3000
    Element at key NickFury : 1200
    Element at key SpiderMan : 1100

    hashMap.size : 4
    hashMap.size : 5

    Element at key Thor : 100
    Element at key BlackWidow : 1000
    Element at key IronMan : 3000
    Element at key NickFury : 1200
    Element at key SpiderMan : 1100

    ```

    **使用函数 HashMap.get(key)、HashMap.replace()、hashmap . put()–**的 Kotlin 程序

    ```kt
    fun main(args: Array<String>) {
        var hashMap : HashMap<String, Int> 
                = HashMap<String, Int> ()

        //adding elements to the hashMap 
        // using put() function
        hashMap.put("IronMan" , 3000)
        hashMap.put("Thor" , 100)
        hashMap.put("SpiderMan" , 1100)
        hashMap.put("Cap" , 1200)

        for(key in hashMap.keys) {
            println("Element at key $key : ${hashMap[key]}")
        }

        //the hashMap's elements can be accessed like this
        println("\nhashMap[\"IronMan\"] : "
                + hashMap["IronMan"])
        hashMap["Thor"] = 2000
        println("hashMap.get(\"Thor\") : " 
                + hashMap.get("Thor") + "\n")

        //replacing some values
        hashMap.replace("Cap" , 999);
        hashMap.put("Thor" , 2000);

        println("hashMap.replace(\"Cap\" , 999)" +
                " hashMap.replace(\"Thor\" , 2000)) :")

        for(key in hashMap.keys) {
            println("Element at key $key : ${hashMap[key]}")
        }
    }
    ```

    **输出:**

    ```kt
    Element at key Thor : 100
    Element at key Cap : 1200
    Element at key IronMan : 3000
    Element at key SpiderMan : 1100

    hashMap["IronMan"] : 3000
    hashMap.get("Thor") : 2000

    hashMap.replace("Cap", 999) hashMap.replace("Thor", 2000)) :
    Element at key Thor : 2000
    Element at key Cap : 999
    Element at key IronMan : 3000
    Element at key SpiderMan : 1100

    ```

    ### 哈希映射的时间复杂性–

    Kotlin HashMap 为 get 和 put 这样的基本操作提供了恒定的时间或 O(1)复杂度，如果 hash 函数被正确编写并且它适当地分散了元素。在 HashMap 中搜索的情况下，containsKey()只是一个丢弃检索值的 get()，它是 O(1)(假设哈希函数正常工作)。

    ### Kotlin HashMap 类的其他一些函数–

    *   **布尔 containsKey(Key: K):** 如果映射包含指定的 key，则返回 true。*   **布尔值包含值(值:V):** 如果映射将一个或多个键映射到指定值，则返回真。*   **void clear():** 从地图中移除所有元素。*   **移除(键:K):** 从地图

    移除指定键及其对应值