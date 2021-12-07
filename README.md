# mergeSort
//Merge Sort is an Optimized Sorting Process


import java.util.*;

public class Main{
    // public static void selectionSorting(int[] myArray){
    //     int length = myArray.length;
    //     for(int i=0;i<length;i++){
    //         int minimumElementIndex = i;
    //         for(int j=i+1;j<length;j++){
    //             if(myArray[minimumElementIndex]>myArray[j]){
    //                 minimumElementIndex = j;
    //             }
    //         }
    //         int temp = myArray[minimumElementIndex];
    //         myArray[minimumElementIndex] = myArray[i];
    //         myArray[i] = temp;
    //     }
    //     for(int element:myArray){
    //         System.out.print(element+" ");
    //     }
    // }
    // public static void bubbleSorting(int[] myArray){
    //     int length = myArray.length;
    //     for(int i = 0;i<length-1;i++){
    //         for(int j=0;j<length-1-i;j++){
    //             if(myArray[j]>myArray[j+1]){
    //                 int temp = myArray[j+1];
    //                 myArray[j+1] = myArray[j];
    //                 myArray[j] = temp;
    //             }
    //         }
    //     }
    //     for(int element:myArray){
    //         System.out.print(element+" ");
    //     }
    // }
    public static int[] mergeSorting(int[] myArray,int low,int high){
        int mid = (low+high)/2 ;
        
        if(low==high){
            int[] baseCaseResult = new int[1];
            baseCaseResult[0] = myArray[low];
            return baseCaseResult;
        }
        int[] fh = mergeSorting(myArray,low,mid);   //For First Half Part
        int[] sh = mergeSorting(myArray,mid+1,high);//For Second Half Part
        
        int[] result = mergeTwoSortedArray(fh,sh);
        
        return result;
    }
    public static int[] mergeTwoSortedArray(int[] fh,int[] sh){
        int[] arr3 = new int[fh.length + sh.length];
        int i = 0;
        int j = 0;
        int k = 0;
        
        while(i<fh.length && j<sh.length){
            if(fh[i]<sh[j]){
                arr3[k] = fh[i];
                i++;
                k++;
            }
            else{
                arr3[k] = sh[j];
                j++;
                k++;
            }
        }
        while(i<fh.length){
            arr3[k] = fh[i];
            i++;
            k++;
        }
        while(j<sh.length){
            arr3[k] = sh[j];
            j++;
            k++;
        }
        return arr3;
    }
    public static void main (String[] args) {
    int[] myArray = {8,9,4,3,2,10};
//     bubbleSorting(myArray);
//     selectionSorting(myArray);
       int[] answer = mergeSorting(myArray,0,5);
        System.out.println(Arrays.toString(answer));
    }
}
