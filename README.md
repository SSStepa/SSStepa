- 👋 Hi, I’m @SSStepa
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
SSStepa/SSStepa is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
class Solution:
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
