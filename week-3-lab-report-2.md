## Week 3 Lab Report 2

### Part 1

This is my code for my Simplest Search Engine.
```
import java.io.IOException;
import java.util.*;
import java.net.URI;

class Handler implements URLHandler {
    ArrayList<String> words = new ArrayList<String>();

    public String handleRequest(URI url) {
        if (url.getPath().contains("/add")) {
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                words.add(parameters[1]);
                return String.format("Word added to the list! The word added was %s", parameters[1]);
            }
            
        } else if (url.getPath().equals("/search")) {
            ArrayList<String> temp = new ArrayList<String>();
            String[] parameters = url.getQuery().split("=");
            if (parameters[0].equals("s")) {
                for (int i = 0; i < words.size(); i++) {
                    if (words.get(i).contains(parameters[1])){
                        temp.add(words.get(i));
                    }
                }
                
                return String.format("Words: %s", temp);
            } else {
                return "Add a query.";
            }
        } else {
            return "404 Not Found! Use a different path.";
        }
        return null;
    }
}

class SearchEngine {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

#### Screenshot 1 of adding a value:
![Add Example 1](/week-3-images/add_example_1.png)

The method that is called in this screenshot is the `handleRequest` function. The `handleRequest` function takes the URL value of the URL for the site which includes "/add?s=cookie". An if statement then checks to see if the path contains "/add". If so, the query is then split into an array and adds the value at index 1 in the array in this case "cookie" to my Arraylist of words.

#### Screenshot 2 of adding a value:
![Add Example 2](/week-3-images/add_example_2.png)

The method that is called in this screenshot is the `handleRequest` function. The `handleRequest` function takes the URL value of the URL for the site which includes "/add?s=cook". An if statement then checks to see if the path contains "/add". If so, the query is then split into an array and adds the value at index 1 in the array in this case "cook" to my Arraylist of words.

#### Screenshot of searching through the Arraylist:
![Add Example 2](/week-3-images/search_example.png)

The method that is called in this screenshot is the `handleRequest` function. The `handleRequest` function takes the URL value of the URL for the site which includes "/search?s=ok". An if statement then checks to see if the path contains "/search". If so, the query is then split into an array and looks for the value at index 1, in this case the substring "ok", in my Arraylist of words.

---

### Part 2

#### Bug from `averageWithoutLowest` in the file `ArrayExamples.java`

* Here is an example of a failure-inducing input for this bug: 
    ```
    @Test
    public void test() {
        double[] input1 = {1, 2, 1};
        double solution = 1.5;
        assertEquals(solution, ArrayExamples.averageWithoutLowest(input1), 0);
    }
    ```

* Here is the symptom for this bug: 

    The symptom is that the program would return the incorrect value.
    ```
    There was 1 failure:
    1) test(ArrayTests)
    java.lang.AssertionError: expected:<1.5> but was:<1.0>
            at org.junit.Assert.fail(Assert.java:89)
            at org.junit.Assert.failNotEquals(Assert.java:835)
            at org.junit.Assert.assertEquals(Assert.java:555)
            at org.junit.Assert.assertEquals(Assert.java:685)
            at ArrayTests.test(ArrayTests.java:83)

    FAILURES!!!
    Tests run: 1,  Failures: 1
    ```

* Here is the bug in the code: 

    `if(num != lowest) { sum += num; }`

    The bug was that the program was getting rid of all values that are equivalent to the lowest value instead of just a single iteration of the lowest value. The line of code shown above is the statement that had to be replaced.


* Here is the fixed version of this bug: 
    
    ```
    static double averageWithoutLowest(double[] arr) {
        if(arr.length < 2) { return 0.0; }
        double lowest = arr[0];
        for(double num: arr) {
            if(num < lowest) { lowest = num; }
        }
        double sum = 0;
        for(double num: arr) {
            //if(num != lowest) { sum += num; }
            sum += num;
        }
        sum -= lowest;
        return sum / (arr.length - 1);
    }
    ```

* Here is an explaination of the connection between the symptom and the bug:

    Because the bug would take out every single iteration of the lowest value but still divide by one less than the total number of values, this would cause the symptom, which is returning an unexpected value.

    As for the input {1,2,1}, we expect the output to be 1.5 as the average minus a single interation of the lowest value, but we ended up getting the value 1.0 instead. Since the bug gets rid of all iterations of the lowest value, the program runs 2 divided by 2 and results in the value 1.0, which is the symptom of being the wrong value.

#### Bug from `filter` in the file `ListExamples.java`

* Here is an example of a failure-inducing input for this bug: 
    ```
    @Test
    public void test() {
        List<String> list1 = new ArrayList<>();
        list1.add("cook");
        list1.add("ate");
        list1.add("cookie");
        List<String> solution = new ArrayList<>();
        solution.add("cook");
        solution.add("cookie");
        assertEquals(solution, ListExamples.filter(list1, new StringCheckerClass()));
  }
    ```

* Here is the symptom for this bug: 

    The symptom is that the program would return the values in the Arraylist in the reverse order.

    ```
    There was 1 failure:
    1) test(ListTests)
    java.lang.AssertionError: expected:<[cook, cookie]> but was:<[cookie, cook]>
            at org.junit.Assert.fail(Assert.java:89)
            at org.junit.Assert.failNotEquals(Assert.java:835)
            at org.junit.Assert.assertEquals(Assert.java:120)
            at org.junit.Assert.assertEquals(Assert.java:146)
            at ListTests.test(ListTests.java:16)

    FAILURES!!!
    Tests run: 1,  Failures: 1
    ```

* Here is the bug in the code: 

    `result.add(0, s);`

    The bug was that the program was adding the checked string to the beginning of new Arraylist which outputs an array with the reverse order rather than the same order they appeared in.


* Here is the fixed version of this bug: 
    
    ```
    static List<String> filter(List<String> list, StringChecker sc) {
        List<String> result = new ArrayList<>();
        for(String s: list) {
            if(sc.checkString(s)) {
                result.add(s);
            }
        }
        return result;
    }
    ```

* Here is an explaination of the connection between the symptom and the bug:

    Because the bug would add each verified string at the beginning of the new list, while it was iterating through the original list in the correct order, it ends up having a reversed order for the returned list. This ends up causing the symptom of printing a reversed order list.

    As for the input {cook, ate, cookie}, we expect the output to be {cook,cookie} with checkString removing strings under the length of 4. We end up with the output {cookie, cook} instead of {cook, cookie}. As the method iterates through the list to check each string, the bug adds the valid strings to the beginning of the returned list causing the list to be in the reversed order.