# Kth Element
215. Kth Largest Element in an Array (Medium)

[Leetcode](https://leetcode.com/problems/kth-largest-element-in-an-array/description/)

Brutal force:

    import java.util.Arrays;

    public class Solution {

        public int findKthLargest(int[] nums, int k) {
            int len = nums.length;
            Arrays.sort(nums);
            return nums[len - k];
        }
    }
    

Heap:

    class Solution {
        public int findKthLargest(int[] nums, int k) {
            int heapSize = nums.length;
            buildMaxHeap(nums, heapSize);
            //建堆完毕后，nums【0】为最大元素。逐个删除堆顶元素，直到删除了k-1个。
            for (int i = nums.length - 1; i >= nums.length - k + 1; --i) {
                //先将堆的最后一个元素与堆顶元素交换，由于此时堆的性质被破坏，需对此时的根节点进行向下调整操作。
                swap(nums, 0, i);
                //相当于删除堆顶元素，此时长度变为nums.length-2。即下次循环的i
                --heapSize;
                maxHeapify(nums, 0, heapSize);
            }
            return nums[0];
        }

        public void buildMaxHeap(int[] a, int heapSize) {
            //从最后一个父节点位置开始调整每一个节点的子树。数组长度为heasize，因此最后一个节点的位置为heapsize-1，所以父节点的位置为heapsize-1-1/2。
            for (int i = (heapSize-2)/ 2; i >= 0; --i) {
                maxHeapify(a, i, heapSize);
            } 
        }

        public void maxHeapify(int[] a, int i, int heapSize) {      //调整当前结点和子节点的顺序。
            //left和right表示当前父节点i的两个左右子节点。
            int left = i * 2 + 1, right = i * 2 + 2, largest = i;
            //如果左子点在数组内，且比当前父节点大，则将最大值的指针指向左子点。
            if (left < heapSize && a[left] > a[largest]) {
                largest = left;
            } 
            //如果右子点在数组内，且比当前父节点大，则将最大值的指针指向右子点。
            if (right < heapSize && a[right] > a[largest]) {
                largest = right;
            }
            //如果最大值的指针不是父节点，则交换父节点和当前最大值指针指向的子节点。
            if (largest != i) {
                swap(a, i, largest);
                //由于交换了父节点和子节点，因此可能对子节点的子树造成影响，所以对子节点的子树进行调整。
                maxHeapify(a, largest, heapSize);
            }
        }

        public void swap(int[] a, int i, int j) {
            int temp = a[i];
            a[i] = a[j];
            a[j] = temp;
        }
    }

Priority queue:

    class Solution {
        public int findKthLargest(int[] nums, int k) {
            // 使用小顶堆
            PriorityQueue<Integer> pq = new PriorityQueue<>(k);
            for (int num : nums) {
                if (pq.size() < k) {
                    pq.offer(num);
                } else if (pq.peek() < num) {
                    pq.poll();
                    pq.offer(num);
                }
            }
            return pq.peek();
        }

    }
    
# Top K Frequent Elements
347. Top K Frequent Elements (Medium)

[leetcode](https://leetcode.com/problems/top-k-frequent-elements/description/)

Buket sort

    public static int[] topKFrequent(int[] nums, int k) {
            /*
             * 分析题意：出现频次前k高的元素，尝试下用桶排序的知识来求解，
             * 我们把数出现的频次作为每个桶的标签，然后把出现相同频次的数
             * 字放入到对应的桶当中，而桶的标签范围是根据数可能出现的最大
             * 次数决定的，接着初始化的时候标签就已经是按从小到大的顺序排
             * 好无需我们再次比较排序，直接倒过来从标签最大的桶反向遍历每
             * 个桶，从倒数第一个不为空的桶开始算，把里面的数取出来，就是
             * 频次出现最高的k个数了。
             */
            // 定义一个hashmap来初始化每个数出现的频次，key是数值，value是频次
            HashMap<Integer, Integer> hashMap = new HashMap<>();
            // 返回的结果集开辟空间
            int[] result = new int[k];

            for(int num : nums) {
                hashMap.put(num, hashMap.getOrDefault(num, 0) + 1);
            }

            List<Integer>[] list = new ArrayList[nums.length + 1];
            // 让数字key出现的频次value作为桶的索引index
            for(int num : hashMap.keySet()) {
                int i = hashMap.get(num);
                // 如果当前桶当中还未建立对应的桶表我们就初始化一个
                if(list[i] == null) {
                    list[i] = new ArrayList<>();
                }
                list[i].add(num);
            }
            int i = 0, t, j;
            // 从频次最高的第一个不为空的桶开始反向取值
            for(t = nums.length; t > 0; --t) {
                if(list[t] != null) {
                    for(j = 0; j < list[t].size() && i < k; ++j) {
                        result[i++] = list[t].get(j);
                    }
                }
            }
            return result;
        }
        
# Sort Characters By Frequency
451. Sort Characters By Frequency (Medium)

[leetcode](https://leetcode.com/problems/sort-characters-by-frequency/description/)
