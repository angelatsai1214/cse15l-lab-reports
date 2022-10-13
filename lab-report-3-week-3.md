# Part 1

## Simplest Search Engine

**Code**:

```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
import java.util.Arrays;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    ArrayList<String> list = new ArrayList<>();

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return Arrays.toString(list.toArray());
        } else if (url.getPath().contains("/search")) {
            String desiredLetters = url.getQuery().split("=")[1];
            ArrayList<String> result = new ArrayList<>();
            for (int i = 0; i < list.size(); i++) {
                String currWord = list.get(i);
                if (currWord.contains(desiredLetters)) {
                    result.add(currWord);
                }
            }
            return Arrays.toString(result.toArray());
        } else {
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                list.add(parameters[1]);
                return "Word added!";
            }
            return "404 Not Found!";
        }
    }
}

public class SearchEngine {
    public static void main(String[] args) throws IOException {
        if (args.length == 0) {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
```

**Results**:

![Image](/Images/root.png)
1. The handleRequest method inside the Handler class was called.
2. There wasn't an argument.
3. n/a

![Image](/Images/addPineapple.png)
1. The handleRequest method inside the Handler class was called.
2. The relevant argument was 'add' and 'pineapple'
3. If 'add' was changed to 'search' then searching will be performed. If 'pineapple" was changed to 'apple' then 'apple' will be added instead.

![Image](/Images/findPineapple.png)
1. The handleRequest method inside the Handler class was called.
2. The relevant argument was 'search' and 'pineapple'
3. If 'search' was changed to 'add' then addition will be performed. If 'pineapple" was changed to 'apple' then 'apple' will be searched for instead.


---


# Part 2

## Bug 1: averageWithoutLowest Method from ArrayExamples Class

![Image](/Images/testAverageError2.png)

- The failure-inducing input was `{ 6.0, 6.0, 3.0, 3.0 }`, but it was essentially any arrays that has duplicating lowest values
- Symptom: `java.lang.AssertionError: expected:[5.0] but was:[4.0]` since I was using `assertEquals` method for JUnit
- The bug was that the loop for getting the sum needs to be modified. There are probably various ways to modify it, but I just removed the if statement inside the summing for loop and later substracted the lowest number from the total sum. You can see from the image below that the test passed after that. 
- The original code was buggy because it was excluding every number that equals the lowest number from the calculation of sum. I my test case, 3.0 was the lowest number in the array. The code would result in a sum that is 6.0 + 6.0 = 12.0 only, and yet this sum is still divided by 3, which means the average will be 4.0. However, the actual average should be (6.0 + 6.0 + 3.0)/3 = 5.0.

![Image](/Images/correctedAverage.png)

## Bug 2: merge Method from ListExamples Class

![Image](/Images/mergeError.png)
- The failure-inducing input was any input that has a non-empty second list (second argument to the method).
- Symptom: `java.lang.OutOfMemoryError: Java heap space`
- The bug was that inside the last while loop for the method, index1 was being updated instead of index2.
- The original code caused an infinite loop because the value being checked for the while loop wasn't being updated at all inside the loop. When I updated `index1 += 1` to `index2 += 1` the code worked. 

![Image](/Images/correctedMerge.png)
