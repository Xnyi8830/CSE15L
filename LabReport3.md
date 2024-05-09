 ## Part 1: Choose one of the bugs from week 4 lab


A failure-inducing input:   
```
 @Test
  public void testReverseInPlace() {
      int[] arr1 = {1, 2, 3, 4, 5};
      ArrayExamples.reverseInPlace(arr1);
      assertArrayEquals(new int[]{5, 4, 3, 2, 1}, arr1);

      int[] arr2 = {};
      ArrayExamples.reverseInPlace(arr2);
      assertArrayEquals(new int[]{}, arr2);

      int[] arr3 = {1};
      ArrayExamples.reverseInPlace(arr3);
      assertArrayEquals(new int[]{1}, arr3);

      int[] arr4 = {1, 2};
      ArrayExamples.reverseInPlace(arr4);
      assertArrayEquals(new int[]{2, 1}, arr4);
  }

```

screenshot:  
<img width="1148" alt="Screenshot 2024-05-08 at 10 15 58 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/6a0a03ea-e15d-472b-8c72-398abb6c365b">


Bug:
The current implementation of reverseInPlace attempts to reverse the array in place by iterating through the entire array, 
swapping elements from start to end. However, the assignment arr[i] = arr[arr.length - i - 1]; overwrites the original elements before they are swapped to the other side,
resulting in an array that does not get reversed correctly and ends up with duplicated elements in the second half.

Fix:
To correctly reverse the array in place, iterate halfway through
the array and swap the elements at symmetric positions from the start and the end.   


```
static void reverseInPlace(int[] arr) {
    for (int i = 0; i < arr.length / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[arr.length - i - 1];
        arr[arr.length - i - 1] = temp;
    }
}
```

Screenshot of the test passing after the fix:

<img width="1168" alt="Screenshot 2024-05-08 at 10 26 22 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/1c1f1ca8-afd4-43e8-8bb7-2b244c29c8bf">



An input that doesn't include a failure:    

```
@Test
public void testReversedBuggy() {
    int[] inputArray = {1, 2, 3, 4, 5};
    int[] expectedOutput = {0, 0, 0, 0, 0}; // Expecting array filled with zeros due to the bug
    assertArrayEquals("The array should be filled with zeros due to the bug", expectedOutput, ArrayExamples.reversed(inputArray));
}
```

screenshot: 

<img width="1148" alt="Screenshot 2024-05-08 at 10 20 00 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/3b5c3a64-40ef-4eb0-bd56-c0196bb097f2">

## Part 2 Research Commands


I choose to focus on the "grep" command, which is a powerful utility for searching text using patterns.

**1. "-r" (recursive)**

The -r option allows grep to search through directories recursively, looking into every file and directory nested within the specified directory.

Example 1:   
```
grep -r "activity" ./technical
```

output:   
<img width="1681" alt="Screenshot 2024-05-08 at 10 41 30 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/f1285773-cf6d-4077-959e-0a8e80ea77ba">

This command will output lines from files in the ./technical directory and its subdirectories that contain the word "activity". It's useful for quickly finding all occurrences of a specific term across multiple files.


Example 2:  Search for the string "2023" in all files recursively.
```
grep -r "2023" ./technical
```

output:  
<img width="1228" alt="Screenshot 2024-05-08 at 10 43 51 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/f7fc962c-73bb-4f03-bb15-3f399e425664">

This command helps locate all references to the year "2023" within the ./technical directory and subdirectories, which can be useful for reviewing entries or changes made in that year.

**2. -i (ignore case)**

The -i option makes the search case-insensitive, allowing grep to match lines regardless of the case.

Example 1: 
```
grep -ri "research" ./technical
```
output:   
<img width="1792" alt="Screenshot 2024-05-08 at 10 50 13 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/f7ba9953-aa4a-49cc-8b36-4fcb5f718eaa">

This command will search through all files in the 911report, biomed, government, and plos directories (and any subdirectories they may contain), ignoring case sensitivity, and it will list every line in which the string "research" appears. This is particularly useful for finding occurrences of a word where there may be variations in its capitalization, such as "Research", "RESEARCH", or "research".

Example 2:
```
grep -ri "terrorist" ./technical
```

output:   
<img width="1792" alt="Screenshot 2024-05-08 at 10 51 09 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/d6b57424-6250-4160-b4e1-2e6e18fe4715">


**3."--color=auto"**
This option highlights the matching strings, making them stand out in the terminal output

Example 1:
```
grep -ri --color=auto "data" ./technical
```
output: 

<img width="1792" alt="Screenshot 2024-05-08 at 10 53 59 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/3083a205-2f58-4db3-81ab-f5b52837349b">

Example 2:
```
grep -ri --color=auto "national" ./technical
```
output:  
<img width="1792" alt="Screenshot 2024-05-08 at 10 54 24 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/856c0df2-1181-4acc-96fb-9b5cb80034b2">


**4. "v" (invert match)**
The -v option inverts the match, showing lines that do not match the specified pattern.


Example 1: 
```
grep -riv "security" ./technical
```

output:  

<img width="1792" alt="Screenshot 2024-05-08 at 10 56 35 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/4f6bfd8c-23b2-4ec3-aa51-ec905dd701a4">

This command will search through all files recursively within the ./technical directory and its subdirectories, displaying lines that do not include the word "security". The -i option ensures that the search ignores case sensitivity (matching "security", "Security", "SECURITY", etc.), while -v inverts the match. This is useful, for example, if you want to filter out all mentions of "security" to focus on other aspects of data or content in these documents.

Example 2:  
```
grep -riv "national" ./technical
```
output: 
<img width="1792" alt="Screenshot 2024-05-08 at 10 57 44 PM" src="https://github.com/Xnyi8830/CSE15L/assets/146397382/bc9a3d89-bc36-4408-89e5-6855ae931e89">

