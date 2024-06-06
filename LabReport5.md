

**Piazza Post**  

Hello everyone,


I've been tasked with implementing a factorial calculation method in Java for my class project. However, I'm encountering some unexpected results when testing different inputs. For instance, when I input 0, the output is 2 instead of the expected 1. Here's a screenshot of my terminal output:




Code Snippet:
```
public class FactorialCalculator {
    public static int factorial(int n) {
        if (n == 0) {
            return 2;  // This is intentionally incorrect.
        }
        int result = 1;
        for (int i = 2; i < n; i++) {
            result *= i;
        }
        return result;
    }

    public static void main(String[] args) {
        int input = Integer.parseInt(args[0]); // Takes an integer argument from the command line.
        System.out.println("Input: " + input);
        System.out.println("Output: " + factorial(input));
    }
}
```

I also noticed that the output for factorial(5) is much lower than expected. I think there might be something wrong with my loop or initial conditions. Does anyone have any ideas on what might be going wrong here?


Screenshot:
![my Screenshot](https://github.com/Xnyi8830/CSE15L/blob/main/output.png)

**TA Response**

Body:
Hi there,

You should write some Junit tests and try debugging it yourself!


**Student's response to TA**

Thank you for your suggestion. this is what I tried: 
```

  import static org.junit.Assert.*;
import org.junit.*;


public class FactorialCalculatorTest {

  @Test
  public void testFactorialZero() {
      assertEquals(1, FactorialCalculator.factorial(0));
  }

  @Test
  public void testFactorialPositive() {
      assertEquals(120, FactorialCalculator.factorial(5));
  }

  @Test
  public void testFactorialNegative() {
      // This should ideally throw an IllegalArgumentException for negative input
      assertThrows(IllegalArgumentException.class, () -> FactorialCalculator.factorial(-1));
  }

  @Test
  public void testFactorialLargeNumber() {
      // Testing for overflow - behavior might not be what is desired, should fail
      assertNotEquals(0, FactorialCalculator.factorial(30));  // Expecting an incorrect result due to overflow
  }
}

```


the command lines to trigger the bugs are:   
local $ javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java   

local $ java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore FactorialCalculatorTest

And this is my output:   

![screenshot 2](https://github.com/Xnyi8830/CSE15L/blob/main/testOutput.png)


After running it, i've realized my implementation has incorrect loop initialization and condition.



The loop in the factorial method starts at i = 2 and ends at i < n. This causes two issues:
It never multiplies by n, underestimating the result for all n > 1.
It entirely skips the multiplication of 1, although this does not change the result but is logically inconsistent with typical factorial calculations.
JUnit Test Finding: For any n > 1, particularly a small n like 2, the output would be incorrect. For instance, factorial(2) would return 1 instead of 2, which is clearly incorrect. Tests like assertEquals(2, FactorialCalculator.factorial(2)); would fail.
 
Here's a revised version of my code: 
```
public class FactorialCalculator {
    public static int factorial(int n) {
        if (n < 0) {
            throw new IllegalArgumentException("Factorial is not defined for negative numbers.");
        }
        if (n == 0) {
            return 1;  // Corrected return value for 0!
        }
        int result = 1;
        for (int i = 1; i <= n; i++) {  // Corrected loop initialization and condition
            result *= i;
        }
        return result;
    }
}
```

**Information about the setup**
/Users/xinyizhang/Desktop/LabReport5
- Users
  - xinyizhang
    - Desktop
      - LabReport5
      -   lib
          - FactorialCalculatorTest.java
          - FactorialCalculator.java
        





