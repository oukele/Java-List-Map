#### Java 集合框架

|    接口     |                           接口描述                           |
| :---------: | :----------------------------------------------------------: |
| Collection  | Collection 是最基本的集合接口，一个Collection 代表一组 Object, 即Collection 的元素，Java 不提供直接继承Collection的类，只提供继承自Collection的类，只提供继承于的子接口（List、Set）。Collection 接口存储一组不唯一，无序的对象。 |
|    List     | List接口是一个有序的 Collection，使用此接口能够精确的控制每个元素插入的位置，能够通过索引(元素在List中位置，类似于数组的下标)来访问List中的元素，第一个元素的索引为 0，而且允许有相同的元素。List接口存储一组不唯一，有序（插入顺序）的对象。 |
|     Set     | Set 具有与 Collection 完全一样的接口，只是行为上不同，Set 不保存重复的元素。Set 接口存储一组唯一，无序的对象。 |
|  SortedSet  |                  继承于Set保存有序的集合。                   |
|     Map     | Map 接口存储一组键值对象，提供key（键）到value（值）的映射。 |
|  Map Entry  |  描述在一个Map中的一个元素（键/值对）。是一个Map的内部类。   |
|  SorteMap   |             继承于 Map，使 Key 保持在升序排列。              |
| Enumeration | 这是一个传统的接口和定义的方法，通过它可以枚举（一次获得一个）对象集合中的元素。这个传统接口已被迭代器取代。 |

#### Set 和 List 的区别

+ Set 接口 实例存储的是无序的，不重复的数据。List接口实例存储的是有序的，可以重复的元素。
+ Set检索效率低下，删除和插入效率高，插入和删除不会引起元素位置改变 <实现类有 HashSet ,TreeSet>。
+ List 和 数组类似，可以动态增长，根据实际存储的数据长度自动增长List的长度。查找元素效率高，插入删除效率低，因为会引起其他元素位置改变 <实现类有ArrayList,LinkedList,Vector >。

#### 集合实现类

|   类名    |                            类描述                            |
| :-------: | :----------------------------------------------------------: |
| ArrayList | 该类也是实现了List的接口，实现了可变大小的数组，随机访问和遍历元素，随机访问和遍历元素时，提供更好的性能。该类也是非同步的，在多线程的情况下不要使用。ArrayList增长当前长度的50%，插入删除效率低。 |
|  HashSet  | 该类实现了Set接口，不允许出现重复元素，不保证集合中元素的顺序，允许包含值为null的元素，但最多只能一个。 |
|  TreeSet  |           该类实现了Set接口，可以实现排序等功能。            |
|  HashMap  | HashMap 是一个散列表，它存储的内容是键值对(key-value)映射。<该类实现了Map接口，根据键的HashCode值存储数据，具有很快的访问速度，最多允许一条记录的键为null，不支持线程同步。 |
|  TreeMap  |              继承了AbstractMap，并且使用一颗树               |

#### 实例

##### 遍历 ArrayList

~~~ java
  List<String> list = new ArrayList<>();
        list.add("Hello");
        list.add("World");
        list.add("AAAAAAAAAA");
        //第一种遍历方法使用foreach遍历List
        for (String str : list) {            //也可以改写for(int i=0;i<list.size();i++)这种形式
            System.out.println(str);
        }
        //第二种遍历，把链表变为数组相关的内容进行遍历
        String[] strArray=new String[list.size()];
        list.toArray(strArray);
        for(int i=0;i<strArray.length;i++) //这里也可以改写为  foreach(String str:strArray)这种形式
        {
            System.out.println(strArray[i]);
        }
        //第三种遍历 使用迭代器进行相关遍历
        Iterator<String> ite=list.iterator();
        while(ite.hasNext())//判断下一个元素之后有值
        {
            System.out.println(ite.next());
        }
~~~

##### 遍历Map

~~~ java
 Map<String, String> map = new HashMap<String, String>();
      map.put("1", "value1");
      map.put("2", "value2");
      map.put("3", "value3");
      
      //第一种：普遍使用，二次取值
      System.out.println("通过Map.keySet遍历key和value：");
      for (String key : map.keySet()) {
       System.out.println("key= "+ key + " and value= " + map.get(key));
      }
      
      //第二种
      System.out.println("通过Map.entrySet使用iterator遍历key和value：");
      Iterator<Map.Entry<String, String>> it = map.entrySet().iterator();
      while (it.hasNext()) {
       Map.Entry<String, String> entry = it.next();
       System.out.println("key= " + entry.getKey() + " and value= " + entry.getValue());
      }
      
      //第三种：推荐，尤其是容量大时
      System.out.println("通过Map.entrySet遍历key和value");
      for (Map.Entry<String, String> entry : map.entrySet()) {
       System.out.println("key= " + entry.getKey() + " and value= " + entry.getValue());
      }
    
      //第四种
      System.out.println("通过Map.values()遍历所有的value，但不能遍历key");
      for (String v : map.values()) {
       System.out.println("value= " + v);
      }
~~~

~~~ html
List 基本操作

ArrayList<String> arrayList = new ArrayList<String>();
//在指定位置插入元素
arrayList.add(2,"Kate")
// addAll(Collection<? extends String> c)添加所给集合中的所有元素
rrayList.addAll(subList)
//判断 是否 包含某个元素
arrayList.contains("Mike")
// 获取指定元素
arrayList.get(2)

LinkedList<String> linkedList = new LinkedList<String>();
// 获取指定元素
linkedList.get(2)
//获取第一个元素
linkedList.getFirst()
//获取最后一个元素
linkedList.getLast()
//获取并删除第一个元素
linkedList.pollFirst()
//获取，但不移除第一个元素
linkedList.peekFirst()
~~~

~~~html
Map 基本操作

HashMap<String, Integer> map = new HashMap<String, Integer>();
 // 向Map中添加元素
    map.put("Tom", 26);   
 // 根据Key获取Value
	map.get("Tom") 
 //移除
    map.remove("Tom");
  // Key相同的元素将被覆盖
    map.put("Tom", 20);
  // 判断是否包含某个Key
    map.containsKey("Tom")
  // 判断是否包含某个Value
    map.containsValue(26)
  // 判断map是否为空
    map.isEmpty()
   // 获取map大小 
    map.size()
   // 获取Key的集合 
    map.keySet()
   
   TreeMap<String, Integer> treeMap = new TreeMap<String, Integer>();
    // 输出内容按照key值排序
        for (Entry<String, Integer> entry : treeMap.entrySet()) {
            System.out.println("name:" + entry.getKey() + " age:"
                    + entry.getValue());
            // name:Jack age:19
            // name:Kate age:15
            // name:Tom age:26
        }
    
    LinkedHashMap<String, Integer> linkedHashMap = new LinkedHashMap<String, Integer>();
        // 向Map中添加元素
        linkedHashMap.put("Tom", 26);
        linkedHashMap.put("Jack", 18);
        linkedHashMap.put("Micky", 17);
        linkedHashMap.put("Kate", 15);
        // 保持了插入的顺序
        for (Entry<String, Integer> entry : linkedHashMap.entrySet()) {
            System.out.println("name:" + entry.getKey() + " age:"
                    + entry.getValue());
            // name:Tom age:26
            // name:Jack age:18
            // name:Micky age:17
            // name:Kate age:15
    
    
~~~

