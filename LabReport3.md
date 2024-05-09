## Part 1 Choose one of the bugs from week 4 lab


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









