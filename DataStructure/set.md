# Set

Set 是一种用于保存不重复元素的数据结构。常被用作测试归属性，故其查找的性能十分重要。

## 编程实现

### Java

Set 与 Collection 具有安全一样的接口，通常有`HashSet`, `TreeSet` 或 `LinkedHashSet`三种实现。`HashSet`基于散列函数实现，无序，查询速度最快；`TreeSet`基于红-黑树实现，有序。

```
Set<String> hash = new HashSet<String>();
hash.add("billryan");
hash.contains("billryan");
```

在不允许重复元素时可当做哈希表来用。

##HashSet
[HashSet](http://www.tutorialspoint.com/java/java_hashset_class.htm)
HashSet extends AbstractSet and implements the Set interface. It creates a collection that uses a hash table for storage.

A hash table stores information by using a mechanism called hashing. In hashing, the informational content of a key is used to determine a unique value, called its hash code.

The hash code is then used as the index at which the data associated with the key is stored. The transformation of the key into its hash code is performed automatically.

```java
import java.util.*;

public class HashSetDemo {

   public static void main(String args[]) {
      // create a hash set
      HashSet hs = new HashSet();
      // add elements to the hash set
      hs.add("B");
      hs.add("A");
      hs.add("D");
      hs.add("E");
      hs.add("C");
      hs.add("F");
      System.out.println(hs);
   }
}
```
This would produce the following result:
[D, E, F, A, B, C]


