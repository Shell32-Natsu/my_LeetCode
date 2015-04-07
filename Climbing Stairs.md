#Climbing Stairs

[Climbing Stairs](https://leetcode.com/problems/climbing-stairs/ "Climbing Stairs")

斐波那契数列.

C++:
    
    class Solution {
    public:
        int climbStairs(int n) {
            if(n == 1)return 1;
            if(n == 2)return 2;
            int a = 1, b = 2, t;
            for(int i = 2; i < n; i++){
                t = b;
                b = a + b;
                a = t;
            }
            return b;
        }
    };