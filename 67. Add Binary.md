#Add Binary

[Add Binary](https://leetcode.com/problems/add-binary/ "Add Binary")

模拟计算。遇到了编译器对于数组初始化的不同实现的问题，LeetCode似乎并没有把空字符串数组初始化为0，导致我的代码中字符串结尾的位置出现问题。相同的代码在不同的环境中编译运行得到不同的结果，这种bug很隐蔽，要多多注意C中字符串的问题。

C:

    void swap_string(char *a){
        int len = strlen(a);
        for(int i = 0; i <= len / 2 - 1; i++){
            a[i] += a[len - i - 1];
            a[len - i - 1] = a[i] - a[len - i - 1];
            a[i] -= a[len - i - 1];
        }
        return ;
    }
    
    char *addBinary(char *a, char *b) {
        swap_string(a);
        swap_string(b);
        int len_a = strlen(a), len_b = strlen(b);
        int min_len = len_a < len_b ? len_a : len_b, max_len = len_a > len_b ? len_a : len_b;
    
        static char ret[10000] = {0};
    
        unsigned int jinwei = 0;
        for(int i = 0; i < min_len; i++){
            ret[i] = (((a[i] - '0') ^ (b[i] - '0')) ^ jinwei) + '0';
            if((a[i] - '0') ^ (b[i] - '0') && jinwei == 1)
                jinwei = 1;
            else
                jinwei = (a[i] - '0') & (b[i] - '0');
    
        }
        for(int i = min_len; i < max_len; i++){
            if(min_len == len_a){
                ret[i] = ((0 ^ (b[i] - '0')) ^ jinwei) + '0';
                jinwei = jinwei & (b[i] - '0');
            }else if(min_len == len_b){
                ret[i] = (((a[i] - '0') ^ 0) ^ jinwei) + '0';
                jinwei = (a[i] - '0') & jinwei;
            }
        }
    
        if(jinwei == 1){
            ret[max_len] = '1';
            ret[max_len + 1] = 0;
        }else{
            ret[max_len] = 0;
        }
    
        swap_string(ret);
        return ret;
    }

把颠倒字符串函数中交换字符位置修改为通过中间变量的形式:

    void swap_string(char *a){
        int len = strlen(a);
        char t;
        for(int i = 0; i <= len / 2 - 1; i++){
            t = a[len - i - 1];
            a[len - i - 1] = a[i];
            a[i] = t;
        }
        return ;
    }

速度加快了1ms，看来赋值比计算效率要高。把char t的声明放到循环体里面去:

    void swap_string(char *a){
        int len = strlen(a);
        for(int i = 0; i <= len / 2 - 1; i++){
            char t = a[len - i - 1];
            a[len - i - 1] = a[i];
            a[i] = t;
        }
        return ;
    }

又更快了1ms。。。看来不能想当然，编译器的优化要厉害很多。