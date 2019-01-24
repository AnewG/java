# Java

sth about java

## Java Tutorials

[Basic](https://learnxinyminutes.com/docs/zh-cn/java-cn/)

[Introduction to Java programming, Part 1](https://www.ibm.com/developerworks/java/tutorials/j-introtojava1/index.html)

[Introduction to Java programming, Part 2](https://www.ibm.com/developerworks/java/tutorials/j-introtojava2/index.html)

[Android studio run standard Java projects](https://stackoverflow.com/questions/16626810/can-android-studio-be-used-to-run-standard-java-projects)

android_book: 9787115439789

## Structure of a java class

```
/*
  orgType  is the organization type, such as com, org, or net.
  orgName  is the name of the organization's domain, such as makotojava, oracle, or ibm.
  appName  is the name of the application, abbreviated.
  compName is the name of the component.
*/
package orgType.orgName.appName.compName;

import com.makotojava.*;

accessSpecifier class ClassName extends Xxx {

  // private String name;
  accessSpecifier static final dataType variableName [= initialValue];

  accessSpecifier ClassName([argumentList]) {
    constructorStatement(s)
    System.out.println("Telling you all about it:");
  }
  
  /*
    public String getName() { return name; }
    public void setName(String value) { name = value; }
  */
  accessSpecifier returnType methodName ([argumentList]) {
    methodStatement(s)
  }
  
  // type
  public void typeMethod(){
    // boxing
    int value = 238;
    Integer boxedValue = Integer.valueOf(value);
    // unbox
    Integer boxedValue = Integer.valueOf(238);
    int intValue = boxedValue.intValue();
    // auto
    int intValue = 238;
    Integer boxedValue = intValue;
    intValue = boxedValue;
  }
  
  // scope
  private String someClassVariable;
  public void someMethod(String someParameter) {
    String someLocalVariable = "Hello";
    if (true) {
      String someOtherLocalVariable = "Howdy";
    }
    someClassVariable = someParameter;          // legal
    someLocalVariable = someClassVariable;      // also legal
    someOtherLocalVariable = someLocalVariable; // Variable out of scope!
  }
  
  // collections
  // array
  public void someOtherMethod() {
    someLocalVariable = "Hello there";// That variable is out of scope!
    int[] integers = new int[5];
    int[] integers2 = new int[] { 1, 2, 3, 4, 5 };
    int[] integers3 = { 1, 2, 3, 4, 5 };
    int[] integers4 = new int[5];
    for (int aa = 0; aa < integers.length; aa++) {
      integers4[aa] = aa+1;
    }
    for (int i : integers) {
      // i
    }
  }
  // list
  public void listMethod(){
    List<Integer> listOfIntegers = new ArrayList<>();
    listOfIntegers.add(Integer.valueOf(238));
    listOfIntegers.size()
    listOfIntegers.get(0)
  }
  // sets
  public void setsMethod(){
    Set<Integer> setOfIntegers = new HashSet<Integer>();
    setOfIntegers.add(Integer.valueOf(10));
  }
  // Maps
  @Override
  public void mapsMethod(){
    Map<String, Integer> mapOfIntegers = new HashMap<>();
    mapOfIntegers.put("1", Integer.valueOf(1));
    mapOfIntegers.get("1")
  }
  
  // try-with-resource
  public void exceptionTestTryWithResources() {
    Logger l = Logger.getLogger(Employee.class.getName());
    File file = new File("file.txt");
    try (BufferedReader bufferedReader = new BufferedReader(new FileReader(file))) {
      String line = bufferedReader.readLine();
      while (line != null) {
        // Read the file
      }
    } catch (Exception e) {
      l.severe(e.getMessage());
    }
  }
}
```

## abstract

```
public abstract class Employee
{
   private String name;
   private String address;
   private int number;
   
   public abstract double computePay();
}
```

## interface

```
public interface InterfaceName {
  returnType methodName(argumentList);
}
public class Manager extends Employee implements BonusEligible, StockOptionRecipient {
  // And so on
}
```

## nested class

```
public class Manager extends Employee {
  public Manager() {
  }
  . . .
  public class DirectReports {
  . . .
  }
}

// Meanwhile, in another method somewhere...
public static void main(String[] args) {
  Manager manager = new Manager();
  Manager.DirectReports dr = manager.new DirectReports();
}

ref: https://www.jianshu.com/p/b7f9c806b3aa
```

## Overload

```
public void printAudit(StringBuilder buffer) {
   buffer.append("Name=");
}
 
public void printAudit(Logger l) {
   StringBuilder sb = new StringBuilder();
   printAudit(sb);
   l.info(sb.toString());
}
```

## enum

```
public enum Gender {
  MALE("male"),
  FEMALE("female"),
  OTHER("other");
 
  private String displayName;
  private Gender(String displayName) {
    this.displayName = displayName;
  }
 
  public String getDisplayName() {
    return this.displayName;
  }
}
```

## JAR

```
src/...
lib/xxx.jar (Add to Build Path)
```

## Generics

```
ArrayList is Generics:
  ArrayList<String> strList = new ArrayList<String>();  
  ArrayList<Integer> intList = new ArrayList<Integer>();  
  ArrayList<Double> doubleList = new ArrayList<Double>();  
  
-------------------------

class Point<T>{   
    private T x ;        
    private T y ;        
    public void setX(T x){
        this.x = x ;  
    }  
    public void setY(T y){  
        this.y = y ;  
    }  
    public T getX(){
        return this.x ;  
    }  
    public T getY(){  
        return this.y ;  
    }  
};  
Point<Integer> p = new Point<Integer>() ;   
p.setX(new Integer(100)) ;   
System.out.println(p.getX());    

Point<Float> p = new Point<Float>() ;   
p.setX(new Float(100.12f)) ;   
System.out.println(p.getX());  

-------------------------

class MorePoint<T,U> {  
    private T x;  
    private T y;         
    private U name;  
    public void setX(T x) {  
        this.x = x;  
    }  
    public T getX() {  
        return this.x;  
    }  
    public void setName(U name){  
        this.name = name;  
    }  
    public U getName() {  
        return this.name;  
    }  
}
MorePoint<Integer,String> morePoint = new MorePoint<Integer, String>();  
morePoint.setName("harvic");  
Log.d(TAG, "morPont.getName:" + morePoint.getName());  

-------------------------

interface Info<T>{    
    public T getVar();  
    public void setVar(T x);  
}    

http://blog.csdn.net/qq_27093465/article/details/73229016
```