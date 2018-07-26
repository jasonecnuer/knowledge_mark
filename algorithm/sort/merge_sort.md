# 归并排序


```java
public class MergeSort {

    private int[] nums;

    MergeSort(int[] nums) {
        this.nums = nums;
    }

    public void sort() {
        sort(nums, 0, nums.length - 1);
    }

    public void sort(int nums[], int start, int end) {
        if (start >= end) {
            return;
        }

        int middle = (start + end) / 2;
        sort(nums, start, middle);
        sort(nums, middle + 1, end);

        int[] copy = new int[nums.length];
        int i = start;
        int left = start;
        int right = middle + 1;
        while (left <= middle && right <= end) {
            if (nums[left] <= nums[right]) {
                copy[i++] = nums[left++];
            } else {
                copy[i++] = nums[right++];
            }
        }
        while (left <= middle) {
            copy[i++] = nums[left++];
        }
        while (right <= end) {
            copy[i++] = nums[right++];
        }
        System.arraycopy(copy, start, nums, start, end - start + 1);
        System.out.println("Start:" + start + ";End:" + end);
        printNums();
    }

    public void printNums() {
        for (int i = 0; i < nums.length; i++) {
            System.out.print(nums[i] + " ");
        }
        System.out.println("");
    }

    public static void main(String[] args) {
        int nums[] = new int[]{46, 30, 82, 90, 56, 17, 95, 15, 39};
        MergeSort sort = new MergeSort(nums);
        sort.printNums();
        sort.sort();
    }
}
```

执行结果如下：
```java
排序前: 46 30 82 90 56 17 95 15 39 

Start:0;End:1
30 46 82 90 56 17 95 15 39 
Start:0;End:2
30 46 82 90 56 17 95 15 39 
Start:3;End:4
30 46 82 56 90 17 95 15 39 
Start:0;End:4
30 46 56 82 90 17 95 15 39 
Start:5;End:6
30 46 56 82 90 17 95 15 39 
Start:7;End:8
30 46 56 82 90 17 95 15 39 
Start:5;End:8
30 46 56 82 90 15 17 39 95 
Start:0;End:8
15 17 30 39 46 56 82 90 95 
```
