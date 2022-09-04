## bcb-week8 二分查找法  
### 基本概念  
二分查找法（Binary Search）算法，也叫折半查找算法。二分查找要求数组数据必须采用顺序存储结构有序排列。查找思想有点类似于分治思想。每次都通过跟区间的中间元素对比，将带查找的区间缩小为之前的一半，直到找到要查找的元素，或者区间被缩小为0。二分查找是一种非常非常高效的查询算法，时间复杂度为O(logn)。
### 二分查找法查找某一特定数  
关于二分查找最重要的是细节，到底是left < right 还是 left <= right , left = mid 还是left = mid + 1,只要弄明白它的区间是开还是闭，细节自然会一清二楚。  
代码1因为它此刻的右端索引为right = len - 1; right为数组最后一个索引，为左闭右闭区间，[left,right]，缩小区间是故应为[left, mid - 1] 和[mid + 1,right]，而mid已经被搜索过，则应被删除。  
### 搜索左边界（两种方法）  
若有数组[2,3,5,5,6,7,9],我要获得第一个5的下标，此时index应为2，即为获取左边界！  
此时找到符合的数不要立即返回，应继续缩小区间，right = mid。此刻区间为[left,right),缩小区间而mid没有被搜索过，故需要right = mid。  
while(left < right) 终止的条件是 left == right，此时搜索区间 [left, left) 为空，所以可以正确终止。  
代码2此时为左闭右闭区间，[left,right]，判断区间范围，可根据right是否为最后一个元素索引还是最后一个元素的下一个下标。right = v1.size() -->左闭右开区间， right = v1.size() - 1 -->左闭右闭区间。    
### 搜索右边界（两种方法）  
类似于左边界，不过需要注意return right - 1;因为此刻退出循环时，left = right,v1[left] 一定不等于target了,而v1[left - 1]可能等于target,故需要right - 1。  
若有数组[2,3,5,5,6,7,9],我要获得最后一个5的下标，此时index应为3，即为获取右边界！  
代码3  
return right;//因为代码中有right - 1,故不需要减1了  
代码4  
### 局限性  
1.二分查找法依赖的是顺序表结构，简单点来说就是数组。主要原因是二分查找方法需要按照下标随机访问元素。如果使用其他数据结构，时间复杂度就会提高。  
2.二分查找针对的是有序数据。所以二分查找只能在插入、删除操作不频繁，一次排序多次查找的场景中；  
3.数据量太小不适合二分查找，如果要处理的数据量很小，顺序遍历就够了。不过，如果元素直接的比较操作非常耗时，例如字符串之间的比较，不管数据量大小，都推荐使用二分查找算法。  
4.数据量太大也不适合用二分查找，因为二分查找依赖于顺序存储结构，要求内存空间连续，如果数据量很大的情况下，可能存在空间不够分配的困难。

