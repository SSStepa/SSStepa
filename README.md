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

class Solution_7:
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
