# 在维基百科学数组排序
### 1.冒泡排序

对比相邻的两个数值顺序错了就会互换一遍一遍的走访知道不需要交换为止

冒泡排序算法的运作如下：

1. 比较相邻的元素。如果第一个比第二个大，就交换他们两个。
2. 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数。
3. 针对所有的元素重复以上的步骤，除了最后一个。
4. 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

改进后的冒泡又叫鸡尾酒排序实例如下

![](https://upload.wikimedia.org/wikipedia/commons/e/ef/Sorting_shaker_sort_anim.gif)

```javascript
Array.prototype.cocktail_sort = function() {
	var i, left = 0, right = this.length - 1;
	var temp;
	while (left < right) {
		for (i = left; i < right; i++)
			if (this[i] > this[i + 1]) {
				temp = this[i];
				this[i] = this[i + 1];
				this[i + 1] = temp;
			}
		right--;
		for (i = right; i > left; i--)
			if (this[i - 1] > this[i]) {
				temp = this[i];
				this[i] = this[i - 1];
				this[i - 1] = temp;
			}
		left++;
	}
};
```

## 2.插入排序

由后往前扫描找到相应位置并插入，为了给插入值位置已排序值会不断的向后挪动

![](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0f/Insertion-sort-example-300px.gif/220px-Insertion-sort-example-300px.gif)

**举例：**

Input: {5 2 4 6 1 3}。

首先拿起第一张牌, 手上有 {5}。

拿起第二张牌 2, 把 2 insert 到手上的牌 {5}, 得到 {2 5}。

拿起第三张牌 4, 把 4 insert 到手上的牌 {2 5}, 得到 {2 4 5}。

以此类推。

## 3.选择排序

工作原理就是找到最小的存放在数组开头再找一个最大的放在数组末尾知道排序结束

选择排序的优点就是如果那个数在正确的位置就不会移动

![](https://upload.wikimedia.org/wikipedia/commons/9/94/Selection-Sort-Animation.gif)

## 4.递归排序也叫归并排序

简单来说就是把一个数组拆分为两份然后在把值分成对对比交换位置依次类推直到数组结束

官方说法：归并操作（merge），也叫归并算法，指的是将两个已经排序的序列合并成一个序列的操作。归并排序算法依赖归并操作。

采用分治法:

- 分割：递归地把当前序列平均分割成两半。
- 整合：在保持元素顺序的同时将上一步得到的子序列整合到一起（归并）。

![](https://upload.wikimedia.org/wikipedia/commons/thumb/c/cc/Merge-sort-example-300px.gif/220px-Merge-sort-example-300px.gif)

## 5.计数排序

通俗地理解，例如有10个年龄不同的人，统计出有8个人的年龄比A小，那A的年龄就排在第9位，用这个方法可以得到其他每个人的位置，也就排好了序。当然，年龄有重复时需要特殊处理（保证稳定性），这就是为什么最后要反向填充目标数组，以及将每个数字的统计减去1

计数排序不是[比较排序](https://zh.wikipedia.org/wiki/比较排序)，排序的速度快于任何比较排序算法。

由于用来计数的数组{\displaystyle C}![ C ](https://wikimedia.org/api/rest_v1/media/math/render/svg/4fc55753007cd3c18576f7933f6f089196732029)的长度取决于待排序数组中数据的范围（等于待排序数组的最大值与最小值的差加上1），这使得计数排序对于数据范围很大的数组，需要大量时间和内存。例如：计数排序是用来排序0到100之间的数字的最好的算法，但是它不适合按字母顺序排序人名。但是，计数排序可以用在[基数排序](https://zh.wikipedia.org/wiki/基数排序)算法中，能够更有效的排序数据范围很大的数组。

