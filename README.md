
#Data Structures - HW#01


###Exercise #1

Assume functions A(n) and B(n) such that:

 ```java

    public static double A(int n) {
        return 100 * (Math.pow(n, 3));
    }

    public static double B(int n){
        return 5 * Math.pow(2, n);
    }
 ```

 As B(n) is an exponential function, if we take large number, we will get that B(n) > A(n)

    B(69) > A(69) / returns true


###Exercise 2 

1. 1250 x 2^45^   
2. 10 + logn  
3. 13n + 2logn  
4. 15n 
5. 3n + 2nlogn 
6. 2n^2^
7. 5n^3^
8. 2n^2^ + 4n^3^
9. 3 x 2^n^

###Exercise 3
```java
Java example:

  public static int example(int[] first, int[] second) {
  int n = first.length, count = 0, total = 0;

  for (int j = 0; j < n; j++)
    for (int k = 0; k <= j; k++)
      total += first[k];

  for (int i = 0; i < n; i++)
    if (second[i] == total) count++;

  return count;
}  

```
Here, the complexity of a function is `O(n`^2^` + n)`

Another function that can do the same work but with complexity of `O(n)` is:

```java
public static int example1(int[] first, int[] second) {
  int count = 0, total = 0;
  for (int j = 0; j < first.length; j++)
    total += first[j];
  for (int k = 0; k < second.length; k++)
    if (total == second[k]) count ++;
  return count;
}
```

###Exercise 4

In order to compare the relative running times of these two methods we should use `System.currentTimeMillis()` function. 

```java
    long startTime = System.currentTimeMillis();
    //`Example` Function Here//
    long endTime = System.currentTimeMillis();
    long totalTime = System.currentTimemillis();
    System.out.println("Total time is " + totalTime)
```

```java
    long startTime = System.currentTimeMillis();
    //`Example1` Function Here//
    long endTime = System.currentTimeMillis();
    long totalTime = System.currentTimemillis();
    System.out.println("Total time is " + totalTime)
```
*Run these functions with arrays of 350000 integers we get output*

`Total time is 37163`  //Example
`Total time is 13`  //Example1

`Here is the whole code`
```java
public class ex4 {
  public static int example(int[] first, int[] second) {
    int n = first.length, count = 0, total = 0;

    for (int j = 0; j < n; j++)
      for (int k = 0; k <= j; k++)
        total += first[k];

    for (int i = 0; i < n; i++)
      if (second[i] == total) count++;

    return count;
  }

  public static int example1(int[] first, int[] second) {
    int count = 0, total = 0;
    for (int j = 0; j < first.length; j++)
      total += first[j];
    for (int k = 0; k < second.length; k++)
      if (total == second[k]) count ++;
    return count;
  }
  
  public static void main(String[] args) {
    int[] first = new int[350000];
    int[] second = new int[350000];

    for (int i = 0; i < 350000; i++) {
      first[i] = i;
      second[i] = i + 1;
    }

    long curTime = System.currentTimeMillis();
    example(first, second);
    long endTime = System.currentTimeMillis();
    System.out.println("Total time is " + totalTime)

    curTime = System.currentTimeMillis();
    example1(first, second);
    endTime = System.currentTimeMillis();

    System.out.println("Total time is " + totalTime)
```

###Exercise 5

If `f(n)` is `O(g(n))` =>  there exist a constant `c > 0`, and a constant `n`~0~ such that for all `n ≥ n`~0~`: f(n) ≤ c*g(n)`

hence: 
   there exist a constant `c > 0`, and a constant `n`~0~ such that for all `n ≥ n`~0~`: g(n) ≥ (1/c)*f(n)` 
     note that since `c > 0`, then the constant `(1/c) > 0`

hence: 
   there exist a constant `k > 0`, namely `k = (1/c)`, and a constant `n`~0~` such that for all n ≥ n`~0~`: g(n) ≥ k*f(n)`

which is the definition of `g(n) = Ω (f(n)).`