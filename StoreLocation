/**
 * StoreLocation.java
 *
 * $Id: StoreLocation.java,v 1.3 2013/10/16 01:30:20 brandon Exp brandon $
 *
 * $Log: StoreLocation.java,v $
 * Revision 1.3  2013/10/16 01:30:20  brandon
 * Code fully tested and Results file logged
 *
 * Revision 1.2  2013/10/16 00:39:28  brandon
 * Code finished, must be tested fully
 *
 * Revision 1.1  2013/10/15 02:16:29  brandon
 * Initial revision
 *
 *
 */

/**
 * Locates the best store location based on the distances
 * of surrounding businesses
 *
 * @author: Brandon James
 * Sorting algorithm help from: 
 *   http://www.algolist.net/Algorithms/Sorting/Selection_sort
 * & http://cs.millersville.edu/~liffick/cs161/Source_Code/ch13/MergeSort.java
 */

import java.util.*;
import java.io.*;

public class StoreLocation{

    /**
     * Calculates the midpoint of a set of store locations
     * using a selection sort.
     *
     * @returns the midpoint the data
     */
    public static int midPoint(int[] arr){
        selectionSort(arr);
        return (arr[0]+arr[arr.length-1])/2;
    }

    /**
     * Calculates the median of a set of store locations
     * using a merge sort.
     *
     * @returns the median of the data
     */
    public static int median(int[] arr){
        int median=0;
        mergeSort(arr);

        if(arr.length%2==0){
            //when array length is even, median is between the two middle values
            median = arr[arr.length/2]-arr[(arr.length/2)-1];
            median = (median/2) + arr[(arr.length/2)-1];
            return median;
        }
        else{
            median = arr[arr.length/2];
            return median;
        }
    }

    /**
     * Calculates the average of a set of store locations
     *
     * @returns the average of the data
     */
    public static int average(int[] arr){
        int total=0;

        for(int i=0; i<arr.length; i++){
            total += arr[i];
        }

        return total/arr.length;
    }
 
    /**
     * Calculates the sum of the distances of each location
     * from the optimal point (midpoint, median, or average)
     *
     * @returns total distance from point
     */
    public static int sumOfDist(int optimumPt, int[] arr){
        int totalDist = 0;
        for(int i=0; i<arr.length; i++){
            if(optimumPt >= arr[i]){
                totalDist += (optimumPt - arr[i]);
            }
            else{
                totalDist += (arr[i] - optimumPt);
            }
        }

        return totalDist;
    }

    /**
     * Sorts the data for the midpoint method from
     * smallest to largest
     */
    private static void selectionSort(int[] arr){
        int temp, smallest;
        for(int i=0; i<arr.length; i++){
            smallest = i;
            for(int j=i+1; j<arr.length; j++){
                if(arr[j] < arr[smallest]){
                    smallest = j;
                }  
            }
            if(smallest != i){
                //swap smallest value to current index
                temp = arr[i];
                arr[i] = arr[smallest];
                arr[smallest] = temp;
            }
        }
    }

    /**
     * Sorts the data for the median method by splitting
     * the array into smaller arrays, then sorting
     */
    private static void mergeSort(int[] arr){
        if (arr.length > 1) {
            //split array into two halves and sorts them recursively
            int[] left = leftSide(arr);
            int[] right = rightSide(arr);
            mergeSort(left);
            mergeSort(right);
            
            //merge the sorted halves together
            merge(arr, left, right);
        }
    }

    /**
     * Becomes the first have the the current array
     */
    private static int[] leftSide(int[] arr){
        int size = arr.length / 2;
        int[] left = new int[size];
        for (int i = 0; i < left.length; i++) {
            left[i] = arr[i];
        }
        return left;
    }
 
    /**
     * Becomes the second half of the current array
     */
    private static int[] rightSide(int[] arr){
        int size1 = arr.length / 2;
        int size2 = arr.length - size1; //size of right half of current array
        int[] right = new int[size2];
        for (int i = 0; i < size2; i++) {
            //fills right array from second half of current array
            right[i] = arr[i + size1]; 
        }
        return right;
    }

    /**
     * Merges the left and right arrays into a whole array
     */
    public static void merge(int[] result, 
                             int[] left, int[] right) {
        int i1 = 0;   // index into left array
        int i2 = 0;   // index into right array
        
        for (int i = 0; i < result.length; i++) {
            if (i2 >= right.length || (i1 < left.length && 
                    left[i1] <= right[i2])) {
                result[i] = left[i1];    // take from left
                i1++;
            } else {
                result[i] = right[i2];   // take from right
                i2++;
            }
        }
    }

    /**
     * Main method to test the StoreLocation program 
     */
    public static void main(String args[]){
        int size=0, midpoint, median, average;
        int[] distArray;
        String inputStr=null;
        BufferedReader input = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer tokenizer;

        System.out.print("Enter distances: ");
         
        try{
            inputStr = input.readLine();  //read and store data from console
        }
        catch(IOException ioe){
            System.err.println(ioe.getMessage());
            System.exit(1);
        }
        
        //counts the number of entries and creates an array of that size
        tokenizer = new StringTokenizer(inputStr, " ");
        size = tokenizer.countTokens();
        distArray = new int[size];

        for(int i=0; i<distArray.length; i++){
            //stores entries in the distance array
            distArray[i] = Integer.parseInt(tokenizer.nextToken());   
        }

        //output for the midpoint strategy
        midpoint = midPoint(distArray);
        System.out.println("The midpoint is: " + midpoint);
        System.out.println("The sum of distances for the midpoint is: " + 
                            sumOfDist(midpoint, distArray));

        //output for the median strategy
        median = median(distArray);
        System.out.println("The median is: " + median);
        System.out.println("The sum of distances for the median is: " + 
                            sumOfDist(median, distArray));

        //output for the average strategy
        average = average(distArray);
        System.out.println("The average is: " + average);
        System.out.println("The sum of distances for the average is: " + 
                            sumOfDist(average, distArray));
    }
}
