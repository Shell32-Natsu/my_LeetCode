#Integer to Roman

[Integer to Roman](https://leetcode.com/problems/integer-to-roman/ "Integer to Roman")

整数转化为罗马数字，简单模拟。

C++:

    class Solution {
    public:
        string intToRoman(int num) {
            string ret;
            
            if(num / 1000 > 0){
                if(num / 1000 < 4)
                    for(int i = 0; i < num / 1000; i++)ret.push_back('M');
            }
            int hundred = num / 100 - num / 1000 * 10;
            if(hundred > 0){
                if(hundred < 4)
                    for(int i = 0; i < hundred; i++)ret.push_back('C');
                else if(hundred == 4){
                    ret.push_back('C');
                    ret.push_back('D');
                }else if(hundred < 9){
                    ret.push_back('D');
                    for(int i = 0; i < hundred - 5; i++)ret.push_back('C');
                }else{
                    ret.push_back('C');
                    ret.push_back('M');
                }
            }
            int ten = num / 10 - num / 100 * 10;
            if(ten > 0){
                if(ten < 4)
                    for(int i = 0; i < ten; i++)ret.push_back('X');
                else if(ten == 4){
                    ret.push_back('X');
                    ret.push_back('L');
                }else if(ten < 9){
                    ret.push_back('L');
                    for(int i = 0; i < ten - 5; i++)ret.push_back('X');
                }else{
                    ret.push_back('X');
                    ret.push_back('C');
                }
            }
            int g = num % 10;
            if(g > 0){
                if(g < 4)
                    for(int i = 0; i < g; i++)ret.push_back('I');
                else if(g == 4){
                    ret.push_back('I');
                    ret.push_back('V');
                }else if(g < 9){
                    ret.push_back('V');
                    for(int i = 0; i < g - 5; i++)ret.push_back('I');
                }else{
                    ret.push_back('I');
                    ret.push_back('X');
                }
            }
            return ret;
        }
    };