## bcb-week8 二分查找法  
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
