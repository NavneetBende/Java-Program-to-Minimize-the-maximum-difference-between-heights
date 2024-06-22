Minimize the maximum difference between heights in Java
Here, in this page we will discuss the program to minimize the maximum difference between heights in Java . We are Given with heights of n towers and a value k. We need to either increase or decrease the height of every tower by k (only once) where k > 0. Our task is to minimize the difference between the heights of the longest and the shortest tower after modifications and output this difference.

Example : Input : arr[] = {1, 5, 15, 10} k = 3

                  Output : Maximum difference is 8

Explanation : After modification array become , arr[] = {4, 8, 12, 7} and maximum   height – minimum height (12-4) = 8.

Minimize the maximum difference between heights
Algorithm :
Take the size of the array from the user and store it in a variable called n, and the value of K in another variable called k.
Declare an array of size n and take n array elements from the user.
Create a  function to carry out the required operation.
First, we attempt to sort the array and maximize the height of each tower.
We accomplish this by decreasing the height of all towers to the right by k and increasing the height of all towers to the left by k. (by k).
It’s also possible that the tower you’re attempting to raise doesn’t have the maximum height.

Therefore we only need to check whether it has the maximum height or not by comparing it with the last element towards the right side which is a[n]-k.

Since the array is sorted if the tower’s height is greater than the a[n]-k then it’s the tallest tower available.

Similar reasoning can also be applied for finding the shortest tower

Code in Java
Run

import java.io.*;
import java.util.*;

public class Main {

	public static void main(String[] args)
	{
		int[] arr = { 7, 4, 8, 8, 8, 9 };
		int k = 6;
		int ans = getMinDiff(arr, arr.length, k);
		System.out.println(ans);
	}
	// } Driver Code Ends

	// User function Template for Java

	public static int getMinDiff(int[] arr, int n, int k)
	{

		Arrays.sort(arr);
		int ans = (arr[n - 1] + k)- (arr[0] + k); // Maximum possible height difference

		int tempmax = arr[n - 1] - k; // Maximum element when we subtract k from whole array
		int tempmin = arr[0] + k; // Minimum element when we add k to whole array
		int max, min;

		for (int i = 0; i < n - 1; i++) {
			if (tempmax > (arr[i] + k)) {
				max = tempmax;
			}
			else {
				max = arr[i] + k;
			}

			if (tempmin < (arr[i + 1] - k)) {
				min = tempmin;
			}
			else {
				min = arr[i + 1] - k;
			}

			if (ans > (max - min)) {
				ans = max - min;
			}
		}
		return ans;
	}
}
5
