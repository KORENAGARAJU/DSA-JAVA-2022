# DSA-JAVA-2022
package Sort_algorithms;

import Util.Util_To_Print;

import java.util.*;

public class SortigAlgorithms {
    public static void main(String[] args) {
        Scanner scn = new Scanner(System.in);
        int N = scn.nextInt() ;
        int[] arr = new int[N] ;
        //filling array
        for (int i = 0; i < arr.length ; i++) {
            arr[i] = scn.nextInt() ;
        }
        // BubbleSortingIterative(arr) ;
        // BubbleSortRecurisveWay(arr , arr.length);
        // insertionSort(arr);
 //      //  selectionSort(arr) ;
        mergeSort(arr , 0 , arr.length-1);
        Util_To_Print.Util(arr);
    }
    public static void BubbleSortingIterative(int[]  arr){
        for(int i = 0 ; i < arr.length ; i++){
            for(int j = 0 ; j < arr.length-i-1 ; j++){
                if(arr[j] > arr[j+1]){
                    int temp = arr[j] ;
                    arr[j] = arr[j+1] ;
                    arr[j+1] = temp ;
                }
            }
        }
        //time complexity = O(N^2)
        //space complexity = O(1)
    }

    public static void BubbleSortRecurisveWay(int[] arr , int N){
        if(N == 0 || N == 1 ){
            return ;
        }

        for(int j = 0 ; j < N-1 ; j++){
            if(arr[j] > arr[j+1]){
                int temp = arr[j] ;
                arr[j] = arr[j+1] ;
                arr[j+1] = temp ;
            }
        }
        //faith
        BubbleSortRecurisveWay(arr , N-1);
        //time complexitiy = O(N^2)
        //space complexitiy =
    }
    public static void insertionSort(int[] arr){
        for(int i = 0 ; i < arr.length ; i++){
            for(int j = i ; j > 0 ; j--){
                if( arr[j] < arr[j-1] ){
                    int temp = arr[j] ;
                    arr[j] = arr[j-1] ;
                    arr[j-1] = temp ;
                }
            }
            //time compexitiy = O(N^2)
        }
    }
    public static void selectionSort( int[] arr ){
        for(int i = 0 ; i < arr.length ; i++){
            int lowest = i ;
            for(int j = i+1 ; j < arr.length ; j++){
                if(arr[lowest] > arr[j]){
                    lowest = j;

                }
            }
            int temp = arr[i] ;
            arr[i] = arr[lowest] ;
            arr[lowest] = temp ;
        }
    }

    //merge sorting
    public static void mergeSort(int [] arr, int left , int right ){
         //base case
        if(left >= right){
            return ;
        }
        int mid = left+(right-left)/2 ;
        mergeSort(arr, left , mid);
        mergeSort(arr , mid+1 ,right );
        mergingWork(arr,left , mid , right);
    }
    public static void mergingWork(int [] arr , int left , int mid , int right){
        int p1 = left ;
        int p2 = mid+1;
        int iter = 0 ;
        int [] ansArr = new int[(right-left)+1] ;
        while(p1 <= mid && p2 <= right){
            if(p1 < p2){
                ansArr[iter] = p1 ;
                p1++ ;
                iter++ ;
            }
            else{
                ansArr[iter] = p2 ;
                p2++;
                iter++;
            }
        }
        while(p1<=mid){
            ansArr[iter] = p1 ;
            p1++;
            iter++;
        }
        while(p2<=right){
            ansArr[iter] = p2;
            p2++ ;
            iter++;
        }
//      change original arr with ansArr
        for (int i = left; i <= right; i++) {
            arr[i] = ansArr[i-left] ;
        }
    }
}
