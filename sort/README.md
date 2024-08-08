排序主要是将一组无序的记录调整为有序的记录序列。   
算法根据是否需要访问外部内存分为内部和外部排序，其中内部排序整个排序过程不需要访问外存即可完成。   
主要介绍插入排序、交换排序、选择排序、快速排序、希尔排序和归并排序
# 1. 插入排序
## 1.1 直接插入排序
插入排序基本策略是：将待排序记录分为有序区、无序区两部分，每次从无序区中第一个记录插入到有序区的适当位置，使有序区保持有序，重复该过程直到排序完成。

```python
def insert_sort(nums):
    for i in range(len(nums)-1):
        currNum, preIndex = nums[i+1],i
        while preIndex >=  0 and currNum < nums[preIndex]:
            nums[preIndex+1] = nums[preIndex]
            preIndex -= 1
        nums[preIndex] = currNum
    return nums
```
复杂度分析:   
外部的循环执行N-1次，内部需要执行N-1-i次，所以算法复杂度为O(N^2).当序列本身有序时，只需要执行外部循环，内部只需要执行一次比较和赋值。所以当序列本身有序或着比较记录比较少时，优势明显.   
## 1.2 希尔排序
上述分析，当待排序的序列有序时，插入排序只需要O(N)的时间。