# 快速排序


```java
public class QuickSort {

    public int[] nums;

    QuickSort(int[] nums) {
        this.nums = nums;
    }

    public void sort() {
        sort(nums, 0, nums.length - 1);
    }

    public void sort(int[] nums, int start, int end) {
        if (start >= end) {
            return;
        }

        int base = nums[start];
        int left = start;
        int right = end;
        while (right > left) {
            while (nums[right] >= base && right > left) {
                right--;
            }
            while (nums[left] <= base && right > left) {
                left++;
            }
            if (left < right) {
                swap(nums, left, right);
            }
        }

        swap(nums, right, start);
        System.out.println("Start:" + start + ";End:" + end);
        printNums();

        sort(nums, start, right - 1);
        sort(nums, right + 1, end);
    }

    public void swap(int[] nums, int l, int r) {
        int tmp = nums[l];
        nums[l] = nums[r];
        nums[r] = tmp;
    }

    public void printNums() {
        for (int i = 0; i < nums.length; i++) {
            System.out.print(nums[i] + " ");
        }
        System.out.println("");
    }

    public static void main(String[] args) {
        int nums[] = new int[]{46, 30, 82, 90, 56, 17, 95, 15, 37};
        QuickSort sort = new QuickSort(nums);
        sort.printNums();
        sort.sort();
    }
}
```

执行结果如下：
```java
排序前: 46 30 82 90 56 17 95 15 37 

Start:0;End:8
17 30 37 15 46 56 95 90 82 
Start:0;End:3
15 17 37 30 46 56 95 90 82 
Start:2;End:3
15 17 30 37 46 56 95 90 82 
Start:5;End:8
15 17 30 37 46 56 95 90 82 
Start:6;End:8
15 17 30 37 46 56 82 90 95 
Start:6;End:7
15 17 30 37 46 56 82 90 95 
```
