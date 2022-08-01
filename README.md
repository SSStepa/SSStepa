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


###Given an integer n, return a string array answer (1-indexed) where:
###answer[i] == "FizzBuzz" if i is divisible by 3 and 5.
###answer[i] == "Fizz" if i is divisible by 3.
###answer[i] == "Buzz" if i is divisible by 5.
###answer[i] == i (as a string) if none of the above conditions are true.

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
        
        
           
###Given an integer num, return the number of steps to reduce it to zero.
###In one step, if the current number is even, you have to divide it by 2, otherwise, you have to subtract 1 from it.       
   
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
        
        
###Given an array nums. We define a running sum of an array as runningSum[i] = sum(nums[0]…nums[i]).
###Return the running sum of nums.
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
   
   
###Given an integer array nums, find three numbers whose product is maximum and return the maximum product.   

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



###You are given an m x n integer grid accounts where accounts[i][j] is the amount of money the ith customer has in the jth bank. Return the wealth that the richest ###customer has.
###A customer's wealth is the amount of money they have in all their bank accounts. The richest customer is the customer that has the maximum wealth.

class Solution_6:
    def maximumWealth(self, accounts: List[List[int]]) -> int:
        x=0
        for i in accounts:
            if sum(i)>x:
                x=sum(i)
        return x
       
       
###A school is trying to take an annual photo of all the students. The students are asked to stand in a single file line in non-decreasing order by height. Let this ###ordering be represented by the integer array expected where expected[i] is the expected height of the ith student in line.
###You are given an integer array heights representing the current order that the students are standing in. Each heights[i] is the height of the ith student in line ###(0-indexed).
###Return the number of indices where heights[i] != expected[i].

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


###Given a binary array nums, return the maximum number of consecutive 1's in the array.

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
   
   
   
###Given an array nums of integers, return how many of them contain an even number of digits.

class Solution_9:
    def findNumbers(self, nums: List[int]) -> int:
        x=0
        for i in nums:
            i=list(str(i))
            if len(i)%2==0:
                x+=1
        return x
        
        
        
###Given an integer array nums sorted in non-decreasing order, return an array of the squares of each number sorted in non-decreasing order.       
class Solution_10:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        our_list=[]
        for i in nums:
            x=i**2
            our_list.append(x)
        return sorted(our_list)
        
        
###Write an efficient algorithm that searches for a value target in an m x n integer matrix matrix. This matrix has the following properties:
###Integers in each row are sorted in ascending from left to right.
###Integers in each column are sorted in ascending from top to bottom.

class Solution_11:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        for i in matrix:
            for f in i:
                if f==target:
                    return True
        return False


###Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value.
###If target is not found in the array, return [-1, -1].
###You must write an algorithm with O(log n) runtime complexity.

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



###Write a function to find the longest common prefix string amongst an array of strings.
###If there is no common prefix, return an empty string ""

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
        
        
###Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.
###An input string is valid if:
###Open brackets must be closed by the same type of brackets.
###Open brackets must be closed in the correct order.        

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


###Given two strings needle and haystack, return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack.
###Clarification:
###What should we return when needle is an empty string? This is a great question to ask during an interview.
###For the purpose of this problem, we will return 0 when needle is an empty string. This is consistent to C's strstr() and Java's indexOf().

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


###Given a string s consisting of words and spaces, return the length of the last word in the string.
###A word is a maximal substring consisting of non-space characters only.

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


###Given a sorted array of distinct integers and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.
###You must write an algorithm with O(log n) runtime complexity.

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


###You are given a large integer represented as an integer array digits, where each digits[i] is the ith digit of the integer. The digits are ordered from most ###significant to least significant in left-to-right order. The large integer does not contain any leading 0's.
###Increment the large integer by one and return the resulting array of digits.

class Solution_18:
    def plusOne(self, digits: List[int]) -> List[int]:
        for i in range(len(digits)):
            digits[i]=str(digits[i])
        nums=int("".join(digits))+1
        return list(str(nums))
