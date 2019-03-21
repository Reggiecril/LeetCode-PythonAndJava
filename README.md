# LeetCode-Practice

##### This is just a practice for LeetCode by Python. Author By [Reggiecril](https://github.com/Reggiecril).
***
##### 1. Two Sum
```python
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        dict={}
        length=len(nums)
        count=0
        while(count<length):
            if target-nums[count] in dict:
                return [dict[target-nums[count]],count]
            dict[nums[count]]=count
            count+=1
```
***
##### 2. Add Two Numbers
```python
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        dummyHead = ListNode(0)
        l3 = dummyHead
        count = 0
        while (l1 or l2):
            if l1 == None:
                sum = l2.val + count
                l3.next = ListNode(sum % 10)
                count = 1 if sum >= 10 else 0
                l3 = l3.next
                l2 = l2.next
            elif l2 == None:
                sum = l1.val + count
                l3.next = ListNode(sum % 10)
                count = 1 if sum >= 10 else 0
                l3 = l3.next
                l1 = l1.next
            else:
                sum = l1.val + l2.val + count
                l3.next = ListNode(sum % 10)
                count = 1 if sum >= 10 else 0
                l3 = l3.next
                l1 = l1.next
                l2 = l2.next
        if count==1:
            l3.next=ListNode(count)
        return dummyHead.next

```
***
##### 3. Longest Substring Without Repeating Characters
```python
    def lengthOfLongestSubstring(s):
        """
        :type s: str
        :rtype: int
        """
        collect = []
        length = 0
        for i in s:
            if i in collect:
                collect = collect[collect.index(i)+1:]
                collect.append(i)
            else:
                collect.append(i)
            length=max(len(collect),length)

```
***
##### 9. Palindrome Number
```python
    def isPalindrome(x):
        """
        :type x: int
        :rtype: bool
        """
        if x < 10 and x > 0:
            return True
        x = str(x)
        length = len(x)
        count = 0
        while count < length / 2 + 1:
            first = x[count]
            last = x[length - 1 - count]
            if not first.__eq__(last):
                return False
            count += 1
        return True
    ###Best Solution
        # if str(x) == str(x)[::-1]:
        #     return True
        # else:
        #     return False

```
***
##### 11. Container With Most Water
```python
    def maxArea(self, height):
        """
        :type height: List[int]
        :rtype: int
        """
        startPtr=0
        lastPtr=len(height)-1
        sum=0
        while lastPtr>startPtr:
            sum=max(sum,min(height[lastPtr],height[startPtr])*(lastPtr-startPtr))
            if height[lastPtr]>height[startPtr]:
                startPtr+=1
            elif height[startPtr]>height[lastPtr]:
                lastPtr-=1
            else:
                startPtr+=1
                lastPtr-=1
        return sum

```
***
##### 35. Search Insert Position

```python
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        if len(nums) == 1:
            return 0 if target <= nums[0] else 1
        if target > nums[len(nums) - 1]:
            return len(nums)
        elif target <= nums[0]:
            return 0
        for i in range(len(nums)):
            if target <= nums[i]:
                return i

```
***
##### 19. Remove Nth Node From End of List

```python

    def removeNthFromEnd(head, n):
        """
        :type head: ListNode
        :type n: int
        :rtype: ListNode
        """
        dummyHead=ListNode(0)
        dummyHead.next=head
        first_ptr=dummyHead
        second_ptr=head
    
        for i in range(1,n):
            second_ptr=second_ptr.next
        while second_ptr.next:
            second_ptr=second_ptr.next
            first_ptr=first_ptr.next
        l1=first_ptr.next
        l1=l1.next
        first_ptr.next=l1
        return dummyHead.next

```
