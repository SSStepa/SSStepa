
# My LeetCode solutions on Python

## 9. Palindrome Number  

### Given an integer x, return true if x is palindrome integer.  
### An integer is a palindrome when it reads the same backward as forward.  
### For example, 121 is a palindrome while 123 is not.  

    class Solution_1:
        def isPalindrome(self, x: int) -> bool:
            our_list=list(str(x))
            y=-1
            for i in our_list:
                if i==our_list[y]:
                    y-=1
                    continue
                else:
                    return False
            return True

## 412. Fizz Buzz  

### Given an integer n, return a string array answer (1-indexed) where:  
### * Answer[i] == "FizzBuzz" if i is divisible by 3 and 5.  
### * Answer[i] == "Fizz" if i is divisible by 3.  
### * Answer[i] == "Buzz" if i is divisible by 5.  
### * Answer[i] == i (as a string) if none of the above conditions are true.  

    class Solution_2:
        def fizzBuzz(self, n: int) -> List[str]:
            our_list=[i for i in range(1,n+1)]
            for i in our_list:
                if i%3==0 and i%5==0:
                    our_list[our_list.index(i)]="FizzBuzz"
                elif i%3==0:
                    our_list[our_list.index(i)]="Fizz"
                elif i%5==0:
                    our_list[our_list.index(i)]="Buzz"
                else:
                    our_list[our_list.index(i)]=str(i)
            return our_list

## 1342. Number of Steps to Reduce a Number to zero  
           
### Given an integer num, return the number of steps to reduce it to zero.  
### In one step, if the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.  
   
    class Solution_3:
        def numberOfSteps(self, num: int) -> int:
            x=0
            while num!=0:
                if num%2==0 :
                    num=num/2
                else:
                    num-=1
                x+=1
            return x
 
 ## 1480. Running Sum of 1d Array
        
### Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]).  
### Return the running sum of nums.

    class Solution_4:
        def runningSum(self, nums: List[int]) -> List[int]:
            our_list=[nums[0]]
            y=1
            element=our_list[-1]
            while y<len(nums):
                x=nums[y]
                our_list.append(x+element)
                y+=1
                element=our_list[-1]
            return our_list

## 628. Maximum Product of Three Numbers  
   
### Given an integer array nums, find three numbers whose product is maximum and return the maximum product.  

    class Solution_5:
        def maximumProduct(self, nums: List[int]) -> int:
            nums=sorted(nums)
            if nums[0]>=0:
                y,z=-2,-3
            elif nums[0]<0 and nums[-1]>=0:
                if nums[0]*nums[1]>nums[-2]*nums[-3]:
                    y,z=0,1
                else:
                    y,z=-2,-3
            else:
                y,z=-2,-3
            x=nums[-1]*nums[y]*nums[z]
            return x

## 1672. Richest Customer Wealth  

### You are given an m x n integer grid accounts where accounts[i][j] is the amount of money the ith customer has in the jth bank. Return the wealth that the richest customer has. 
### A customer's wealth is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.  

    class Solution_6:
        def maximumWealth(self, accounts: List[List[int]]) -> int:
            x=0
            for i in accounts:
                if sum(i)>x:
                    x=sum(i)
            return x

№№ 1051. Height Checker  
       
### A school is trying to take an annual photo of all the students. The students are asked to stand in a single file line in non-decreasing order by height. Let this ordering be represented by the integer array expected where expected[i] is the expected height of the ith student in line.  
### You are given an integer array heights representing the current order that the students are standing in. Each heights[i] is the height of the ith student in line (0-indexed).  
### Return the number of indices where heights[i] != expected[i].  

    class Solution_7:
        def heightChecker(self, heights: List[int]) -> int:
            expected=sorted(heights)
            x=0
            for i in heights:
                f=expected[heights.index(i)]
                if i!=f:
                       x+=1
             heights[heights.index(i)]=0
            return x

 ## 485. Max Consecutive Ones  

### Given a binary array nums, return the maximum number of consecutive 1's in the array.  

    class Solution_8:
        def findMaxConsecutiveOnes(self, nums: List[int]) -> int:
            our_list=[]
            x=[]
            for i in nums:
                if i==1:
                    x.append(i)
                else:
                    our_list.append(x)
                    x=[]
            else:
                our_list.append(x)
            our_list=sorted(our_list)
            return len(our_list[-1])

## 1295. Find Numbers with Even Number of Digits  

### Given an array nums of integers, return how many of them contain an even number of digits.  

    class Solution_9:
        def findNumbers(self, nums: List[int]) -> int:
            x=0
            for i in nums:
                i=list(str(i))
                if len(i)%2==0:
                    x+=1
            return x

## 977. Squares of a Sorted Array  
        
### Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.  

    class Solution_10:
        def sortedSquares(self, nums: List[int]) -> List[int]:
            our_list=[]
            for i in nums:
                x=i**2
                our_list.append(x)
            return sorted(our_list)

## 240. Search a 2D Matrix II  
        
### Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:  
### Integers in each row are sorted in ascending from left to right.  
### Integers in each column are sorted in ascending from top to bottom.  

    class Solution_11:
        def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
            for i in matrix:
                for f in i:
                    if f==target:
                        return True
            return False

## 34. Find First and Last Position of Element in Sorted Array  

### Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.  
### If target is not found in the array, return [-1, -1].  
### You must write an algorithm with O(log n) runtime complexity.  

    class Solution_12:
        def searchRange(self, nums: List[int], target: int) -> List[int]:
            nums_1=sorted(nums,reverse=True)
            for i in nums:
                if i==target:
                    x=nums.index(i)
                    break
            else:
                return -1,-1
            for i in nums_1:
                if i==target:
                    y=len(nums)-(nums_1.index(i)+1)
                    break
            return x,y

## 14. Longest Common Prefix  

### Write a function to find the longest common prefix string amongst an array of strings.  
### If there is no common prefix, return an empty string ""  

    class Solution_13:
        def longestCommonPrefix(self, strs: List[str]) -> str:
            x=0
            index=0
            answer=""
            while x<len(strs[0]):
                answer_1=strs[0][index]
                for i in range(1,len(strs)):
                    try:
                        if answer_1!=strs[i][index]:
                            return answer
                    except:
                        return answer
                else:
                    answer+=answer_1
                x+=1
                index+=1
            return answer

## 20. Valid Parentheses  
  
### Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.  
### An input string is valid if:  
### * Open brackets must be closed by the same type of brackets.  
### * Open brackets must be closed in the correct order.  

    class Solution_14:
        def isValid(self, s: str) -> bool:
            our_list=list(s)
            while len(our_list)>0:
                x=0
                for i in our_list:
                    x+=1
                    if (i=="(" or i=="[" or i=="{") and len(our_list)>x:
                        if  our_list[x]=="(" or our_list[x]=="[" or our_list[x]=="{":
                            continue
                        else:
                            if i=="(" and our_list[x]==")":
                                our_list.pop(x)
                                our_list.pop(x-1)
                                break
                            elif i=="[" and our_list[x]=="]":
                                our_list.pop(x)
                                our_list.pop(x-1)
                                break
                            elif i=="{" and our_list[x]=="}":
                                our_list.pop(x)
                                our_list.pop(x-1)
                                break
                            else:
                                return False
                    else:
                        return False
            return True

## 28. Implement strStr()  

### Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.  
### Clarification:  
### What should we return when needle is an empty string? This is a great question to ask during an interview.  
### For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().  

    class Solution_15:
        def strStr(self, haystack: str, needle: str) -> int:
            if needle=="":
                return 0
            x=0
            for i in haystack:
                if i==needle[0]:
                    y=haystack[x:x+len(needle)]
                    if y==needle:
                        return x
            x+=1
            return -1

## 58. Length of Last Word  

### Given a string s consisting of words and spaces, return the length of the last word in the string.  
### A word is a maximal substring consisting of non-space characters only.  

    class Solution_16:
        def lengthOfLastWord(self, s: str) -> int:
            x=0
            while x==0:
                if s[-1]==" ":
                    s=s[:len(s)-1]
                    print(s)
                else:
                    break
            print(s,1)
            s=reversed(s)
            for i in s:
                if i!=" ":
                    x+=1
                else:
                    return x
            return x

## 35. Search Insert Position  

### Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.  
### You must write an algorithm with O(log n) runtime complexity.  

    class Solution_17:
        def searchInsert(self, nums: List[int], target: int) -> int:
            for i in nums:
                if i==target:
                    return nums.index(i)
            for i in nums:
                if target>i and (nums[-1]==i or nums[nums.index(i)+1]>target):
                    return nums.index(i)+1
            else:
                return 0

## 66. Plus One  

### You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most significant to least significant in left-to-right order. The large integer does not contain any leading 0's.  
### Increment the large integer by one and return the resulting array of digits.  

    class Solution_18:
        def plusOne(self, digits: List[int]) -> List[int]:
            for i in range(len(digits)):
                digits[i]=str(digits[i])
            nums=int("".join(digits))+1
            return list(str(nums))

## 378. Kth Smallest Element in a Sorted Matrix  

### Given an n x n matrix where each of the rows and columns is sorted in ascending order, return the kth smallest element in the matrix.  
### Note that it is the kth smallest element in the sorted order, not the kth distinct element.  
### You must find a solution with a memory complexity better than O(n2).  

    class Solution_19:
        def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
            x=[]
            for i in matrix:
                for f in i:
                    x.append(f)
            x=sorted(x)
            return x[k-1]

## 1089. Duplicate Zeros  

### Given a fixed-length integer array arr, duplicate each occurrence of zero, shifting the remaining elements to the right.  
### Note that elements beyond the length of the original array are not written. Do the above modifications to the input array in place and do not return anything.  

    class Solution_20:
        def duplicateZeros(self, arr: List[int]) -> None:
            """
            Do not return anything, modify arr in-place instead.
            """
            x=0
            while len(arr)>x:
                if arr[x]==0:
                    arr.insert(x+1,0)
                    x+=2
                    arr.pop(-1)
                    continue
                x+=1
            return(arr)

## 88. Merge Sorted Array  

### You are given two integer arrays nums1 and nums2, sorted in non-decreasing order, and two integers m and n, representing the number of elements in nums1 and nums2 respectively.  
### Merge nums1 and nums2 into a single array sorted in non-decreasing order.  
### The final sorted array should not be returned by the function, but instead be stored inside the array nums1. To accommodate this, nums1 has a length of m + n, where the first m elements denote the elements that should be merged, and the last n elements are set to 0 and should be ignored. nums2 has a length of n.  
    
    class Solution_21:
        def merge(self, nums1: List[int], m: int, nums2: List[int], n: int) -> None:
            """
            Do not return anything, modify nums1 in-place instead.
            """
            while m<len(nums1):
                nums1.pop(-1)
            nums1.extend(nums2)
            x=len(nums1)-1
            element_1=0
            element_2=1
            num=0
            y=0
            while x>0:
                while element_2<len(nums1)-y:
                    if int(nums1[element_1])>int(nums1[element_2]):
                        num=nums1[element_1]
                        nums1[element_1]=nums1[element_2]
                        nums1[element_2]=num
                        element_1+=1
                        element_2+=1  
                    else:
                        element_1+=1
                        element_2+=1
                    continue
                element_1=0
                element_2=1
                x-=1
                y+=1
            return nums1

## 4. Median of Two Sorted Arrays  

### Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.  
### The overall run time complexity should be O(log (m+n)). 

    class Solution_22:
        def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
            nums1.extend(nums2)
            nums=sorted(nums1)
            x=len(nums)
            if x%2==0:
                answer=(nums[x//2] + nums[x//2-1])/2
            else:
                answer=nums[x//2]
            return answer

## 27. Remove Element  

### Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The relative order of the elements may be changed.  
### Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.  
### Return k after placing the final result in the first k slots of nums.  
### Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory  

    class Solution_23:
        def removeElement(self, nums: List[int], val: int) -> int:
            x=0
            while x<len(nums):
                if nums[x]==val:
                    nums.pop(x)
                else:
                    x+=1
## 26. Remove Duplicates from Sorted Array  

### Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once. The relative order of the elements should be kept the same.  
### Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the first part of the array nums. More formally, if there are k elements after removing the duplicates, then the first k elements of nums should hold the final result. It does not matter what you leave beyond the first k elements.  
### Return k after placing the final result in the first k slots of nums.  
### Do not allocate extra space for another array. You must do this by modifying the input array in-place with O(1) extra memory.  

    class Solution_24:
        def removeDuplicates(self, nums: List[int]) -> int:
            array=set(nums)
            array=sorted(list(array))
            for i in range(len(nums)):
                nums.pop(0)
            for i in array:
                nums.append(i)
            nums=sorted(nums)

## 2351. First Letter to Appear Twice  

### Given a string s consisting of lowercase English letters, return the first letter to appear twice.  
### Note:  
### * A letter a appears twice before another letter b if the second occurrence of a is before the second occurrence of b.  
### * s will contain at least one letter that appears twice.  

    class Solution_25:
        def repeatedCharacter(self, s: str) -> str:
            our_set=set()
            for i in s:
                if our_set&{i} !=set():
                    return i
                else:
                    our_set.add(i)

## 387. First Unique Character in a String  

### Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.  

    class Solution_26:
        def firstUniqChar(self, s: str) -> int:
            for i in range(len(s)):
                num=0
                for f in s:
                    if s[i]==f:
                        num+=1
                        if num>1:
                            break
                else:
                    return i
            return -1

## 804. Unique Morse Code Words  

### International Morse Code defines a standard encoding where each letter is mapped to a series of dots and dashes, as follows:  
### 'a' maps to ".-",  
### 'b' maps to "-...",  
### 'c' maps to "-.-.", and so on.  
### For convenience, the full table for the 26 letters of the English alphabet is given below:  
### [".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--.."]  
### Given an array of strings words where each word can be written as a concatenation of the Morse code of each letter.  
### For example, "cab" can be written as "-.-..--...", which is the concatenation of "-.-.", ".-", and "-...". We will call such a concatenation the transformation of a word.  
### Return the number of different transformations among all words we have.  

    class Solution_27:
        def uniqueMorseRepresentations(self, words: List[str]) -> int:
            our_tuple=(".-","-...","-.-.","-..",".","..-.","--.","....","..",".---","-.-",".-..","--","-.","---",".--.","--.-",".-.","...","-","..-","...-",".--","-..-","-.--","--..")
            our_set=set()
            for i in words:
                txt=""
                for s in i:
                    txt+=our_tuple[ord(s)-97]
                our_set.add(txt)
            return len(our_set)

## 1346. Check If N and Its Double Exist  

### Given an array arr of integers, check if there exists two integers N and M such that N is the double of M ( i.e. N = 2 * M).  
### More formally check if there exists two indices i and j such that :  
### * i != j  
### * 0 <= i, j < arr.length  
### * arr[i] == 2 * arr[j]  

    class Solution_28:
        def checkIfExist(self, arr: List[int]) -> bool:
            our_list=[]
            for i in arr:
                our_list.append(i*2)
            for i in range(len(arr)):
                for d in range(len(arr)):
                    if i!=d and our_list[i]==arr[d]:
                        return True
            return False
            
## 941. Valid Mountain Array  

### Given an array of integers arr, return true if and only if it is a valid mountain array.  
### Recall that arr is a mountain array if and only if:  
### * arr.length >= 3  
### * There exists some i with 0 < i < arr.length - 1 such that:  
### * arr[0] < arr[1] < ... < arr[i - 1] < arr[i]  
### * arr[i] > arr[i + 1] > ... > arr[arr.length - 1]  

    class Solution_29:
        def validMountainArray(self, arr: List[int]) -> bool:
            if len(arr)<3:
                return False
            x=True
            for i in range(1,len(arr)):
                if x==True:
                    if arr[i]>arr[i-1]:
                        None
                    elif arr[i]<arr[i-1] :
                        x=False
                    else:
                        return False
                else:
                    if i==2:
                        return False
                    if arr[i]<arr[i-1]:
                        None
                    else:
                        return False
            if x==True:
                return False
            return True

## 1299. Replace Elements with Greatest Element on Right Side  

### Given an array arr, replace every element in that array with the greatest element among the elements to its right, and replace the last element with -1.  
### After doing so, return the array.  

    class Solution_30:
        def replaceElements(self, arr: List[int]) -> List[int]:
            if len(arr)==1:
                return [-1]
            x=0
            for i in range(len(arr)):
                if x==0 or arr[i]==x:
                    x=0
                    for d in arr[i+1:]:
                        if x<d:
                            x=d
                arr[i]=x
            arr[-1]=-1
            return arr
            
## 283. Move Zeroes  

### Given an integer array nums, move all 0's to the end of it while maintaining the relative order of the non-zero elements.  
### Note that you must do this in-place without making a copy of the array. 

    class Solution_31:
        def moveZeroes(self, nums: List[int]) -> None:
            """
            Do not return anything, modify nums in-place instead.
            """
            l=[]
            for i in range(len(nums)):
                if nums[i]==0:
                    l.append(i)
            for i in reversed(l):
                nums.pop(i)
                nums.append(0)
            return nums
            
## 905. Sort Array By Parity  

### Given an integer array nums, move all the even integers at the beginning of the array followed by all the odd integers.  
### Return any array that satisfies this condition.  

    class Solution_32:
        def sortArrayByParity(self, nums: List[int]) -> List[int]:
        arr=[]
            for i in nums:
                if i%2==0:
                    arr.append(i)
            for i in nums:
                if i%2!=0:
                    arr.append(i)
            return arr

## 414. Third Maximum Number  

### Given an integer array nums, return the third distinct maximum number in this array. If the third maximum does not exist, return the maximum number.  

    class Solution_33:
        def thirdMax(self, nums: List[int]) -> int:
            nums=set(nums)
            nums=sorted(list(nums))
            if len(nums)>=3:
                return nums[-3]
            else:
                return nums[-1]

## 448. Find All Numbers Disappeared in an Array  

### Given an array nums of n integers where nums[i] is in the range [1, n], return an array of all the integers in the range [1, n] that do not appear in nums.  

    class Solution_34:
        def findDisappearedNumbers(self, nums: List[int]) -> List[int]:
            l=[k for k in range(1,len(nums)+1)]
            nums=set(nums)
            l=set(l)
            l=l.difference(nums)
            return list(l)

## 326. Power of Three  

### Given an integer n, return true if it is a power of three. Otherwise, return false.  
### An integer n is a power of three, if there exists an integer x such that n == 3x.  

    class Solution_35:
        def isPowerOfThree(self, n: int) -> bool:
            if n<=0:
                return False
            if n==1:
                return True
            while 1==1:
                if n==3:
                    return True
                if n%3==0:
                    n=n/3
                else:
                    return False

## 383. Ransom Note  

### Given two strings ransomNote and magazine, return true if ransomNote can be constructed by using the letters from magazine and false otherwise.  
### Each letter in magazine can only be used once in ransomNote. 

    class Solution_36:
        def canConstruct(self, ransomNote: str, magazine: str) -> bool:
            ransomNote=list(ransomNote)
            magazine=list(magazine)
            while ransomNote!=[] :
                for t in range(len(magazine)):
                    if ransomNote[0]==magazine[t]:
                        ransomNote.pop(0)
                        magazine.pop(t)
                        break
                else:
                    return False
            return True

## 69. Sqrt(x)  

### Given a non-negative integer x, compute and return the square root of x.  
### Since the return type is an integer, the decimal digits are truncated, and only the integer part of the result is returned  
### Note: You are not allowed to use any built-in exponent function or operator, such as pow(x, 0.5) or x ** 0.5.  

    class Solution:
        import math
        def mySqrt(self, x: int) -> int:
            sqrt=math.sqrt(x)
            return int(sqrt)

## 7. Reverse Integer

### Given a signed 32-bit integer x, return x with its digits reversed. If reversing x causes the value to go outside the signed 32-bit integer range [-231, 231 - 1], then return 0.

    class Solution:
        def reverse(self, x: int) -> int:
            x = list(str(x))
            if x[0] == "-":
                x.pop(0)
                x.append("-")
            s = ""
            for i in reversed(x):
                s+=i
            s = int(s)
            if s < (-2**31) or s > 2**31:
                return 0
            return s


## 67. Add Binary

### Given two binary strings a and b, return their sum as a binary string.

    class Solution:
        def addBinary(self, a: str, b: str) -> str:
            a = int(a,2)
            b = int(b,2)
            ans = bin(a + b)
            return ans[2:]


## 1137. N-th Tribonacci Number

### The Tribonacci sequence Tn is defined as follows: T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.
### Given n, return the value of Tn.

    class Solution:
        def tribonacci(self, n: int) -> int:
            if n == 0:
                return 0
            elif n == 1 or n == 2:
                return 1
            x1 = 0 
            x2 = 1
            x3 = 1
            x4 = 0
            i = 0
            while i < n-2 :
                x4 = x1 + x2 + x3
                x1 = x2
                x2 = x3
                x3 = x4
                i+=1
            return x4

## 1470. Shuffle the Array

### Given the array nums consisting of 2n elements in the form [x1,x2,...,xn,y1,y2,...,yn].
### Return the array in the form [x1,y1,x2,y2,...,xn,yn].

    class Solution:
        def shuffle(self, nums: List[int], n: int) -> List[int]:
            ans = []
            for i in range(n):
                ans.append(nums[i])
                ans.append(nums[i+n])
            return ans


## 1523. Count Odd Numbers in an Interval Range

### Given two non-negative integers low and high. Return the count of odd numbers between low and high (inclusive).

    class Solution:
        def countOdds(self, low: int, high: int) -> int:
            if low%2 == 1 and high%2 == 1:
                return int((high-low+2)/2)
            elif low%2 == 0 and high%2 == 0:
                return int((high-low)/2)
            else:
                return int((high-low+1)/2)


## 989. Add to Array-Form of Integer

### The array-form of an integer num is an array representing its digits in left to right order.
### For example, for num = 1321, the array form is [1,3,2,1].
### Given num, the array-form of an integer, and an integer k, return the array-form of the integer num + k.

    class Solution:
        def addToArrayForm(self, num: List[int], k: int) -> List[int]:
            s=""
            for i in num:
                s+=str(i)
            s=int(s)
            s=str(s+k)
            ans=[]
            for i in s:
                ans.append(int(i))
            return ans


## 540. Single Element in a Sorted Array

### You are given a sorted array consisting of only integers where every element appears exactly twice, except for one element which appears exactly once.
### Return the single element that appears only once.
### Your solution must run in O(log n) time and O(1) space.

    class Solution:
        def singleNonDuplicate(self, nums: List[int]) -> int:
            for i in range(len(nums)):
                if (nums[i]==nums[-1] or nums[i]!=nums[i+1]) and (i==0 or nums[i-1]!=nums[i]):

                    return nums[i]


## 258. Add Digits
### Given an integer num, repeatedly add all its digits until the result has only one digit, and return it.

    class Solution:
        def addDigits(self, num: int) -> int:
            while int(num)>=10:
                num1 = 0
                for i in str(num):
                    num1+=int(i)
                num = num1
            return num


## 136. Single Number
### Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.
### You must implement a solution with a linear runtime complexity and use only constant extra space.

    class Solution:
        def singleNumber(self, nums: List[int]) -> int:
            arr = set(nums)
            for i in nums:
                if i in arr:
                    arr.remove(i)
                else:
                    arr.add(i)
            nums = list(set(nums)-arr)
            return nums[0]


## 1491. Average Salary Excluding the Minimum and Maximum Salary
### You are given an array of unique integers salary where salary[i] is the salary of the ith employee.
### Return the average salary of employees excluding the minimum and maximum salary. Answers within 10-5 of the actual answer will be accepted.

    class Solution:
        def average(self, salary: List[int]) -> float:
            salary = sorted(salary)
            salary.pop(0)
            salary.pop(-1)
            x = 0
            x = sum(salary)/len(salary)
            return x

## 1822. Sign of the Product of an Array
### There is a function signFunc(x) that returns:
### 1 if x is positive.
### -1 if x is negative.
### 0 if x is equal to 0.
### You are given an integer array nums. Let product be the product of all values in the array nums.
### Return signFunc(product).

    class Solution:
        def arraySign(self, nums: List[int]) -> int:
            x = 1
            for i in nums:
                x = x*i
            if x>0:
                return 1
            elif x<0:
                return -1
            else:
                return 0

## 2215. Find the Difference of Two Arrays
### Given two 0-indexed integer arrays nums1 and nums2, return a list answer of size 2 where:
### answer[0] is a list of all distinct integers in nums1 which are not present in nums2.
### answer[1] is a list of all distinct integers in nums2 which are not present in nums1.
### Note that the integers in the lists may be returned in any order.

    class Solution:
        def findDifference(self, nums1: List[int], nums2: List[int]) -> List[List[int]]:
            nums1, nums2 = set(nums1), set(nums2)
            ans = []
            ans.append(list(nums1-nums2 ))
            ans.append(list(nums2-nums1 ))
            return ans

## 649. Dota2 Senate
### In the world of Dota2, there are two parties: the Radiant and the Dire.
### The Dota2 senate consists of senators coming from two parties. Now the Senate wants to decide on a change in the Dota2 game. The voting for this 
### change is a round-based procedure. In each round, each senator can exercise one of the two rights:
### Ban one senator's right: A senator can make another senator lose all his rights in this and all the following rounds.
### Announce the victory: If this senator found the senators who still have rights to vote are all from the same party, he can announce the victory and 
### decide on the change in the game.
### Given a string senate representing each senator's party belonging. The character 'R' and 'D' represent the Radiant party and the Dire party. Then if 
### there are n senators, the size of the given string will be n.
### The round-based procedure starts from the first senator to the last senator in the given order. This procedure will last until the end of voting. All 
### the senators who have lost their rights will be skipped during the procedure.
### Suppose every senator is smart enough and will play the best strategy for his own party. Predict which party will finally announce the victory and 
### change the Dota2 game. The output should be "Radiant" or "Dire".

    class Solution:
        def predictPartyVictory(self, senate: str) -> str:
            senate = list(senate)
            while "R" in senate and "D" in senate:
                if senate[0] == "R":
                    senate.remove("D")
                    senate.pop(0)
                    senate.append("R")
                else:
                    senate.remove("R")
                    senate.pop(0)
                    senate.append("D")
            else:
                if senate[0] == 'R':
                    return "Radiant"
                else:
                    return "Dire"

## 1456. Maximum Number of Vowels in a Substring of Given Length
### Given a string s and an integer k, return the maximum number of vowel letters in any substring of s with length k.
### Vowel letters in English are 'a', 'e', 'i', 'o', and 'u'.

    class Solution:
        def maxVowels(self, s: str, k: int) -> int:
            s = list(s)
            vowel = { 'a', 'e', 'i', 'o', 'u'}
            x = 0 
            for i in range(k):
                if s[i] in vowel:
                    x+=1
            y = x
            for i in range(k,len(s)):
                if s[i] in vowel:
                    y+=1
                if s[i-k] in vowel:
                    y-=1
                x=max(x, y)
            return x

## 1498. Number of Subsequences That Satisfy the Given Sum Condition
### You are given an array of integers nums and an integer target.
### Return the number of non-empty subsequences of nums such that the sum of the minimum and maximum element on it is less or equal to target. Since the 
### answer may be too large, return it modulo 109 + 7.

    class Solution:
        def numSubseq(self, nums: List[int], target: int) -> int:
            nums.sort()
            left, right = 0, len(nums) - 1
            res = 0
            mod = 10**9 + 7
            while left <= right:
                if nums[left] + nums[right] > target:
                    right -= 1
                else:
                    res += pow(2, right - left, mod)
                    left += 1
            return res % mod

## 1964. Find the Longest Valid Obstacle Course at Each Position
### You want to build some obstacle courses. You are given a 0-indexed integer array obstacles of length n, where obstacles[i] describes the height of the ith obstacle.
### For every index i between 0 and n - 1 (inclusive), find the length of the longest obstacle course in obstacles such that:
### You choose any number of obstacles between 0 and i inclusive.
### You must include the ith obstacle in the course.
### You must put the chosen obstacles in the same order as they appear in obstacles.
### Every obstacle (except the first) is taller than or the same height as the obstacle immediately before it.
### Return an array ans of length n, where ans[i] is the length of the longest obstacle course for index i as described above.

    class Solution:
        def longestObstacleCourseAtEachPosition(self, obstacles: List[int]) -> List[int]:
            lst,ans=[],[]
            for i in obstacles:
                b=bisect_right(lst,i)
                if b==len(lst):
                    lst.append(i)
                else:
                    lst[b]=i
                ans.append(b+1)
            return ans

## 1572. Matrix Diagonal Sum
### Given a square matrix mat, return the sum of the matrix diagonals.
### Only include the sum of all the elements on the primary diagonal and all the elements on the secondary diagonal that are not part of the primary diagonal.

    class Solution:
        def diagonalSum(self, mat: List[List[int]]) -> int:
            num = 0
            ans = 0
            for i in mat:
                ans+= i[num]
                num+=1
            num=len(mat)-1
            for i in mat:
                ans+= i[num]
                num-=1
            if len(mat)%2!=0:
                x = len(mat)//2
                ans-=mat[x][x]
            return ans

## 175. Combine Two Tables
### Write an SQL query to report the first name, last name, city, and state of each person in the Person table. If the address of a personId is not present in the Address table, report null instead.
### Return the result table in any order.
### The query result format is in the following example.

    /* Write your T-SQL query statement below */
    SELECT Person.firstName, Person.lastName, Address.city, Address.state
    FROM Person 
    LEFT JOIN Address ON Person.personId=Address.personId;

## 182. Duplicate Emails
### Write an SQL query to report all the duplicate emails. Note that it's guaranteed that the email field is not NULL.
### Return the result table in any order.
### The query result format is in the following example.



    # Write your MySQL query statement below
    SELECT DISTINCT P1.email FROM Person P1, Person P2
    WHERE P1.id<>P2.id AND P1.email=P2.email;

## 183. Customers Who Never Order
### Find all customers who never order anything.
### Return the result table in any order.
### The result format is in the following example.


    Write your MySQL query statement below
    SELECT name AS Customers FROM Customers
    WHERE Customers.id NOT IN (SELECT CustomerId FROM Orders);

## 181. Employees Earning More Than Their Managers
### Write an SQL query to find the employees who earn more than their managers.
### Return the result table in any order.
### The query result format is in the following example.

    # Write your MySQL query statement below
    SELECT name As Employee FROM Employee AS Em1
    WHERE salary>(SELECT salary FROM Employee AS Em2 WHERE Em2.id = Em1.ManagerId);

## 2798. Number of Employees Who Met the Target
### There are n employees in a company, numbered from 0 to n - 1. Each employee i has worked for hours[i] hours in the company.
### The company requires each employee to work for at least target hours.
### You are given a 0-indexed array of non-negative integers hours of length n and a non-negative integer target.
### Return the integer denoting the number of employees who worked at least target hours.

    class Solution:
        def numberOfEmployeesWhoMetTarget(self, hours: List[int], target: int) -> int:
            good_workers = 0
            hours.sort(reverse=True)
            while len(hours)>=good_workers+1 and hours[good_workers]>=target:
                good_workers+=1
            return good_workers
            
## 74. Search a 2D Matrix
### You are given an m x n integer matrix matrix with the following two properties:
### Each row is sorted in non-decreasing order.
### The first integer of each row is greater than the last integer of the previous row.
### Given an integer target, return true if target is in matrix or false otherwise.
### You must write a solution in O(log(m * n)) time complexity.

    class Solution:
        def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
            for row in matrix:
                if row[-1]>=target:
                    for i in row:
                        if i==target:
                            return True

## 595. Big Countries
### A country is big if:
### it has an area of at least three million (i.e., 3000000 km2), or
### it has a population of at least twenty-five million (i.e., 25000000).
### Write a solution to find the name, population, and area of the big countries.
### Return the result table in any order.
### The result format is in the following example.

    # Write your MySQL query statement below
    SELECT name, population, World.area FROM World 
    WHERE World.area>=3000000 or population>=25000000;

## 511. Game Play Analysis I
### Write a solution to find the first login date for each player.
### Return the result table in any order.
### The result format is in the following example.

    # Write your MySQL query statement below
    SELECT player_id, MIN(event_date) AS first_login FROM Activity
    GROUP BY player_id;

## 196. Delete Duplicate Emails
### Write a solution to delete all duplicate emails, keeping only one unique email with the smallest id.
### For SQL users, please note that you are supposed to write a DELETE statement and not a SELECT one.
### For Pandas users, please note that you are supposed to modify Person in place.
### After running your script, the answer shown is the Person table. The driver will first compile and run your piece of code and then show the Person table. The final order of the Person table does not matter.
### The result format is in the following example.

    # Write your MySQL query statement below
    DELETE P1 FROM Person P1,Person P2
    WHERE P1.email=P2.email AND P1.id>P2.id;

## 577. Employee Bonus
### Write an SQL query to report the name and bonus amount of each employee with a bonus less than 1000.
### Return the result table in any order.
### The query result format is in the following example.

    # Write your MySQL query statement below
    SELECT Employee.name, Bonus.bonus 
    FROM Bonus
    RIGHT JOIN Employee ON Bonus.EmpId=Employee.EmpId
    WHERE Bonus.bonus<1000 OR Bonus.bonus IS NULL;

## 2810. Faulty Keyboard
### Your laptop keyboard is faulty, and whenever you type a character 'i' on it, it reverses the string that you have written. Typing other characters works as expected.
### You are given a 0-indexed string s, and you type each character of s using your faulty keyboard.
### Return the final string that will be present on your laptop screen.
    
    class Solution:
        def finalString(self, s: str) -> str:
            ans = ''
            for letter in s:
                if letter=="i":
                    ans = ans[::-1]
                else:
                    ans+=letter
            return str(ans)

## 1512. Number of Good Pairs
### Given an array of integers nums, return the number of good pairs.
### A pair (i, j) is called good if nums[i] == nums[j] and i < j.

    class Solution:
        def numIdenticalPairs(self, nums: List[int]) -> int:
            good_pairs = 0
            for i in range(len(nums)):
                for j in range(i+1, len(nums)):
                    if nums[i] == nums[j]:
                        good_pairs+=1
            return good_pairs

## 2356. Number of Unique Subjects Taught by Each Teacher
### Write a solution to calculate the number of unique subjects each teacher teaches in the university.
### Return the result table in any order.
### The result format is shown in the following example.

    # Write your MySQL query statement below
    SELECT teacher_id, COUNT(DISTINCT subject_id ) AS cnt  FROM Teacher
    GROUP BY teacher_id;

## 17. Letter Combinations of a Phone Number
### Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.
### A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

    class Solution:
        def letterCombinations(self, digits: str) -> List[str]:
            info = {
                2:("a", "b", "c"), 
                3:("d", "e", "f"), 
                4:("g", "h", "i"),
                5:("j", "k", "l"),
                6:("m", "n", "o"),
                7:("p", "q", "r", "s"),
                8:("t", "u", "v"),
                9:("w", "x", "y", "z")
                }
            ans = []
            for i in reversed(digits):
                if ans:
                    small_ans = []
                    for k in info[int(i)]:
                        for later in range(len(ans)):
                            x = k + ans[later]
                            small_ans.append(x)
                    ans = small_ans
                else:
                    for k in info[int(i)]:
                        ans.append(k)
            return ans

## 242. Valid Anagram
### Given two strings s and t, return true if t is an anagram of s, and false otherwise.
### An Anagram is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

    class Solution:
        def isAnagram(self, s: str, t: str) -> bool:
            s = sorted(s)
            t = sorted(t)
            return s == t

## 1431. Kids With the Greatest Number of Candies
### There are n kids with candies. You are given an integer array candies, where each candies[i] represents the number of candies the ith kid has, and an integer extraCandies, denoting the number of extra candies that you have.
### Return a boolean array result of length n, where result[i] is true if, after giving the ith kid all the extraCandies, they will have the greatest number of candies among all the kids, or false otherwise.
### Note that multiple kids can have the greatest number of candies.

    class Solution:
        def kidsWithCandies(self, candies: List[int], extraCandies: int) -> List[bool]:
            ans = []
            for i in candies:
                if i+extraCandies >= max(candies):
                    ans.append(True)
                else:
                    ans.append(False)
            return ans

## 70. Climbing Stairs
### You are climbing a staircase. It takes n steps to reach the top.
### Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

    class Solution:
        def climbStairs(self, n: int) -> int:
            fib1 = 1
            fib2 = 1
            i = 0
            while i < n - 1:
                fib_sum = fib1 + fib2
                fib1 = fib2
                fib2 = fib_sum
                i = i + 1
            return fib2

## 169. Majority Element
### Given an array nums of size n, return the majority element.
### The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.

    class Solution:
        def majorityElement(self, nums: List[int]) -> int:
            half = (len(nums)/2)
            my_set = set(nums)
            for i in my_set:
                print(i)
                if nums.count(i)>half:
                    return i

## 2108. Find First Palindromic String in the Array
### Given an array of strings words, return the first palindromic string in the array. If there is no such string, return an empty string "".
### A string is palindromic if it reads the same forward and backward.

    class Solution:
        def firstPalindrome(self, words: List[str]) -> str:
            for i in words:
                if i == i[::-1]:
                    return i
            return ""

## 1207. Unique Number of Occurrences
### Given an array of integers arr, return true if the number of occurrences of each value in the array is unique or false otherwise.
    
    class Solution:
        def uniqueOccurrences(self, arr: List[int]) -> bool:
            my_set = set(arr)
            ans_set = set()
            for x in my_set:
                ans_set.add(arr.count(x))
            if len(ans_set) == len(my_set):
                return True
            else:
                return False
## 287. Find the Duplicate Number
### Given an array of integers nums containing n + 1 integers where each integer is in the range [1, n] inclusive.
### There is only one repeated number in nums, return this repeated number.
### You must solve the problem without modifying the array nums and uses only constant extra space.

    class Solution:
        def findDuplicate(self, nums: List[int]) -> int:
            nums_set = set(nums)
            n_sum = sum(nums) - sum(nums_set)
            ans = int(n_sum/(len(nums)- len(nums_set)))
            return ans
            
## 1436. Destination City
### You are given the array paths, where paths[i] = [cityAi, cityBi] means there exists a direct path going from cityAi to cityBi. Return the destination city, that is, the city without any path outgoing to another city.
### It is guaranteed that the graph of paths forms a line without any loop, therefore, there will be exactly one destination city.

    class Solution:
        def destCity(self, paths: List[List[str]]) -> str:
            start = set()
            end = set()
            for path in paths:
                start.add(path[0])
                end.add(path[1])
            ans = list(end-start)[0]
            return ans
## 2149. Rearrange Array Elements by Sign
### You are given a 0-indexed integer array nums of even length consisting of an equal number of positive and negative integers.
### You should rearrange the elements of nums such that the modified array follows the given conditions:
### Every consecutive pair of integers have opposite signs.
### For all integers with the same sign, the order in which they were present in nums is preserved.
### The rearranged array begins with a positive integer.
### Return the modified array after rearranging the elements to satisfy the aforementioned conditions.

    class Solution:
        def rearrangeArray(self, nums: List[int]) -> List[int]:
            pos = []
            neg = []
            for i in nums:
                if i > 0:
                    pos.append(i)
                else:
                    neg.append(i)
            nums = []
            for x in range(len(pos)):
                nums.append(pos[x])
                nums.append(neg[x])
            return nums

## 2966. Divide Array Into Arrays With Max Difference
### You are given an integer array nums of size n and a positive integer k.
### Divide the array into one or more arrays of size 3 satisfying the following conditions:
### Each element of nums should be in exactly one array.
### The difference between any two elements in one array is less than or equal to k.
### Return a 2D array containing all the arrays. If it is impossible to satisfy the conditions, return an empty array. And if there are multiple answers, return any of them.

    class Solution:
        def divideArray(self, nums: List[int], k: int) -> List[List[int]]:
            nums = sorted(nums)
            ans = []
            sub_ans = []
            for i in nums:
                if sub_ans == []:
                    sub_ans.append(i)
                else:
                    if i-min(sub_ans) <= k:
                        sub_ans.append(i)
                    else:
                        return []
                if len(sub_ans) == 3:
                    ans.append(sub_ans)
                    sub_ans = []
            return ans

## 2971. Find Polygon With the Largest Perimeter
### You are given an array of positive integers nums of length n.
### A polygon is a closed plane figure that has at least 3 sides. The longest side of a polygon is smaller than the sum of its other sides.
### Conversely, if you have k (k >= 3) positive real numbers a1, a2, a3, ..., ak where a1 <= a2 <= a3 <= ... <= ak and a1 + a2 + a3 + ... + ak-1 > ak, then there always exists a polygon with k sides whose lengths are a1, a2, a3, ..., ak.
### The perimeter of a polygon is the sum of lengths of its sides.
### Return the largest possible perimeter of a polygon whose sides can be formed from nums, or -1 if it is not possible to create a polygon.

    class Solution:
        def largestPerimeter(self, nums: List[int]) -> int:
            nums = sorted(nums)[::-1]
            for i in range(len(nums)):
                if nums[i] < sum(nums[i+1:]):
                    break
            if len(nums[i:]) >= 3:
                return sum(nums[i:])
            else:
                return -1

## 1481. Least Number of Unique Integers after K Removals
### Given an array of integers arr and an integer k. Find the least number of unique integers after removing exactly k elements.

    class Solution:
        def findLeastNumOfUniqueInts(self, arr: List[int], k: int) -> int:
            ans = len(set(arr))
            my_list = list(collections.Counter(arr).values())
            my_list.sort()
            while my_list and k >= my_list[0]:
                k -= my_list[0]
                ans -= 1
                my_list.pop(0)
            return ans

## 231. Power of Two
### Given an integer n, return true if it is a power of two. Otherwise, return false.
### An integer n is a power of two, if there exists an integer x such that n == 2x.

    class Solution:
        def isPowerOfTwo(self, n: int) -> bool:
            if n <= 0:
                return False
            return int(log(n,2)) == round(log(n,2), 10)

## 268. Missing Number
### Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.

    class Solution:
        def missingNumber(self, nums: List[int]) -> int:
            return sum([i for i in range(len(nums)+1)]) - sum(nums)

## 201. Bitwise AND of Numbers Range
### Given two integers left and right that represent the range [left, right], return the bitwise AND of all numbers in this range, inclusive.

    class Solution:
        def rangeBitwiseAnd(self, left: int, right: int) -> int:
            ziro = 0
            while left!=right:
                left >>= 1
                right >>= 1
                ziro += 1
            return left << ziro

## 997. Find the Town Judge
### In a town, there are n people labeled from 1 to n. There is a rumor that one of these people is secretly the town judge.
### If the town judge exists, then:
### The town judge trusts nobody.
### Everybody (except for the town judge) trusts the town judge.
### There is exactly one person that satisfies properties 1 and 2.
### You are given an array trust where trust[i] = [ai, bi] representing that the person labeled ai trusts the person labeled bi. If a trust relationship does not exist in trust array, then such a trust relationship does not exist.
### Return the label of the town judge if the town judge exists and can be identified, or return -1 otherwise.

    class Solution:
        def findJudge(self, n: int, trust: List[List[int]]) -> int:
            people = dict.fromkeys([i for i in range(1, n+1)], 0)
            for tr in trust:
                if tr[0] in people:
                    people.pop(tr[0])
                if tr[1] in people:
                    people[tr[1]] += 1
            if list(people.keys()) and people[list(people.keys())[0]] == n-1:
                return list(people.keys())[0]
            else:
                return -1

## 977. Squares of a Sorted Array
### Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.

    class Solution:
        def sortedSquares(self, nums: List[int]) -> List[int]:
            ans = []
            for i in nums:
                ans.append(i**2)
            ans.sort()
            return ans

## 948. Bag of Tokens
### You start with an initial power of power, an initial score of 0, and a bag of tokens given as an integer array tokens, where each tokens[i] donates the value of tokeni.
### Your goal is to maximize the total score by strategically playing these tokens. In one move, you can play an unplayed token in one of the two ways (but not both for the same token):
### Face-up: If your current power is at least tokens[i], you may play tokeni, losing tokens[i] power and gaining 1 score.
### Face-down: If your current score is at least 1, you may play tokeni, gaining tokens[i] power and losing 1 score.
### Return the maximum possible score you can achieve after playing any number of tokens.

    class Solution:
        def bagOfTokensScore(self, tokens: List[int], power: int) -> int:
            ans = []
            tokens.sort()
            while tokens:
                print(tokens[0], power)
                if tokens[0] <= power:
                    power -= tokens[0]
                    ans.append(1)
                    tokens.pop(0)
                elif ans:
                    power += tokens[-1]
                    ans.append(-1)
                    tokens.pop(-1)
                else:
                    break
            ans.reverse()
            while ans:
                if ans[0] == -1:
                    ans.pop(0)
                else:
                    break
            return sum(ans)
