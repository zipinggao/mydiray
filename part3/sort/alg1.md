##题目描述

归并排序将待排序的元素序列分成两个长度相等的子序列，为每一个子序列排序，然后再将他们合并成一个子序列。合并两个子序列的过程也就是两路归并。

##示例： 
![](/assets/merge2.jpg)

![](/assets/mergesort.gif)

 
##题解： 


    public class Main {
        public void merge(int []a,int left,int mid,int right){
            int []tmp=new int[a.length];//辅助数组
            int p1=left,p2=mid+1,k=left;//p1、p2是检测指针，k是存放指针
    
            while(p1<=mid && p2<=right){
                if(a[p1]<=a[p2])
                    tmp[k++]=a[p1++];
                else
                    tmp[k++]=a[p2++];
            }
    
            while(p1<=mid) tmp[k++]=a[p1++];//如果第一个序列未检测完，直接将后面所有元素加到合并的序列中
            while(p2<=right) tmp[k++]=a[p2++];//同上
    
            //复制回原素组
            for (int i = left; i <=right; i++)
                a[i]=tmp[i];
        }
    
        public void mergeSort(int[] a,int start,int end){
            if (start < end){ //当只有一个元素时结束递归
                int mid = (start+end)/2;//划分子序列
                mergeSort(a, start,mid);//对左侧子序列进行递归排序
                mergeSort(a, mid + 1, end);//对右侧子序列进行递归排序
                merge(a,start,mid,end);//合并
    
            }
        }
    
        public static void main(String[] args) {
    	    // write your code here
            int [] a = {49,38,65,97,76,13,27,50};
            Main test = new Main();
            test.mergeSort(a,0,a.length-1);
            System.out.println("排序好的数组：");
            for(int e : a)
                System.out.print(e + " ");
            }
    }
 
##复杂度分析：
**时间复杂度：** 数组 a[]中相邻的长度为h的有序序列进行两两归并.并将结果放到temp[]，需要将待排序列中的所有记录扫描一遍，因此耗费$$O(n)$$，完全二叉树的归并排序需要进行$$log{2^n}$$次.因此总的时间复杂度$$O(nlogn)$$。

**空间复杂度:** 归并排序在归并过程中需要与原始序列同样数量的存储空间存放归并结果以及递归时深度为$$log{2_n}$$的栈空间，因此空间复杂度为$$O(n+logn)$$。   

归并排序是一种比较占内存，但却效率高且稳定的算法。