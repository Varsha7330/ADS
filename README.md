# ADS
#finding BFT and DFT using linkedlist
import java.util.*;
public class Main{
    public static void merge(int a[],int low,int high, int mid) {
        int n1=mid-low+1;
        int n2=high-mid;
        int L[]=new int[n1];
        int R[]=new int[n2];
        for(int i=0;i<n1;++i) {
            L[i]=a[low+i];
        }
        for(int j=0;j<n2;++j){
            R[j]=a[mid+1+j];
        }
        int i=0;int j=0;
        int k=low;
        while(i<n1){
            a[k]=L[i];
            i++;
            k++;
        }
        while(j<n2){
            a[k]=R[j];
            j++;
            k++;
        }
    }
    public static void sort(int a[],int low,int high) {
        if(low<high){
            int mid=(low+high)/2;
            sort(a,low,mid);
            sort(a,mid+1,high);
            merge(a,low,mid,high);
        }
    }
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        System.out.println("enter the no.of elements: ");
        int n=sc.nextInt();
        int a[]=new int[n];
        System.out.println("enter elements: ");
        for(int i=0;i<n;i++){
            a[i]=sc.nextInt();

        }
        System.out.println("given array:\n"+Arrays.toString(a));
        long start=System.nanoTime();
        sort(a,0,n-1);
        long end=System.nanoTime();
        System.out.println("Sorted array: \n"+Arrays.toString(a));
        System.out.println("time taken: "+(end-start)+ "ns");
    }
}
