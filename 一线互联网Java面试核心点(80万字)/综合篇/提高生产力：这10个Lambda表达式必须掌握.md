# 提高生产力：这10个Lambda表达式必须掌握


### 使用Lambda表达式进行集合遍历
❌ 未使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
for (String fruit : list) {
    System.out.println(fruit);
}
```
✅ 使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
list.forEach(fruit -> System.out.println(fruit));
```

### 使用Lambda表达式进行排序
❌  未使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
Collections.sort(list, new Comparator() {
    public int compare(String s1, String s2) {
        return s1.compareTo(s2);
    }
});
```
✅ 使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
Collections.sort(list, (s1, s2) -> s1.compareTo(s2));
```

### 使用Lambda表达式进行过滤
❌  未使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
List filteredList = new ArrayList();
for (String fruit : list) {
    if (fruit.startsWith("a")) {
        filteredList.add(fruit);
    }
}
```
✅ 使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
List filteredList = list.stream().filter(fruit -> fruit.startsWith("a"))
								.collect(Collectors.toList());
```

### 使用Lambda表达式进行映射
❌  未使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
List lengths = new ArrayList();
for (String fruit : list) {
    lengths.add(fruit.length());
}
```
✅ 使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
List lengths = list.stream()
                	.map(fruit -> fruit.length())
                	.collect(Collectors.toList());
```

### 使用Lambda表达式进行归约
❌  未使用Lambda表达式：
```java
List list = Arrays.asList(1, 2, 3, 4, 5);
int sum = 0;
for (int i : list) {
	sum += i;
}
```
✅ 使用Lambda表达式：
```java
List list = Arrays.asList(1, 2, 3, 4, 5);
int sum = list.stream().reduce(0, (a, b) -> a + b);
```

### 使用Lambda表达式进行分组
❌  未使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
Map<Integer, List> grouped = new HashMap<Integer, List>();
for (String fruit : list) {
    int length = fruit.length();
    if (!grouped.containsKey(length)) {
        grouped.put(length, new ArrayList());
    }
    grouped.get(length).add(fruit);
}
```
✅ 使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
Map<Integer, List> grouped = list.stream()
				.collect(Collectors.groupingBy(fruit -> fruit.length()));
```

### 使用Lambda表达式进行函数式接口的实现
❌  未使用Lambda表达式：
```java
public interface MyInterface {
    public void doSomething(String input); 
}

MyInterface myObject = new MyInterface() {
	public void doSomething(String input) {
		System.out.println(input);
	}
};

myObject.doSomething("Hello World");

```
✅ 使用Lambda表达式：
```java
MyInterface myObject = input -> System.out.println(input);
myObject.doSomething("Hello World");
```

### 使用Lambda表达式进行线程的创建
❌  未使用Lambda表达式：
```java
Thread thread = new Thread(new Runnable() {
    public void run() {
    	System.out.println("Thread is running.");
    }
});
thread.start();
```
✅ 使用Lambda表达式：
```java
Thread thread = new Thread(() -> System.out.println("Thread is running."));
thread.start();
```

### 使用Lambda表达式进行Optional的操作
❌  未使用Lambda表达式：
```java
String str = "Hello World";
if (str != null) {
	System.out.println(str.toUpperCase());
}
```
✅ 使用Lambda表达式：
```java
Optional str = Optional.ofNullable("Hello World");
str.map(String::toUpperCase)
	.ifPresent(System.out::println);
```

### 使用Lambda表达式进行Stream的流水线操作
❌  未使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
List filteredList = new ArrayList();
for (String fruit : list) {
    if (fruit.startsWith("a")) {
        filteredList.add(fruit.toUpperCase());
    }
}
Collections.sort(filteredList);
```
✅ 使用Lambda表达式：
```java
List list = Arrays.asList("apple", "banana", "orange");
List filteredList = list.stream().filter(fruit -> fruit.startsWith("a"))
								.map(String::toUpperCase)
								.sorted()
								.collect(Collectors.toList());
```



> 原文: <https://www.yuque.com/tulingzhouyu/db22bv/lzl8ff6f3wg3nar4>