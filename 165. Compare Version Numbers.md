#Compare Version Numbers

[Compare Version Numbers](https://leetcode.com/problems/compare-version-numbers/ "Compare Version Numbers")

stoi函数在win平台上实现有问题(GCC 4.7.1)，所以使用atoi函数。使用最笨的办法，递归处理字符串，每次递归只处理两个版本号的第一个小数点前面的部分。

C++:

    class Solution {
    public:
        int compareVersion(string version1, string version2) {
            if(version1.size() == 0 && version2.size() == 0) return 0;
            size_t v1_pot_pos = version1.find("."), v2_pot_pos = version2.find(".");
            int v1_front, v2_front;
            string v1_behind, v2_behind;
            if(v1_pot_pos != string::npos){
                v1_front = atoi(version1.substr(0,v1_pot_pos).c_str());
                v1_behind = version1.substr(v1_pot_pos + 1);
            }else{
                if(version1.size() != 0)v1_front = atoi(version1.c_str());
                else v1_front = 0;
                v1_behind = "";
            }
    
            if(v2_pot_pos != string::npos){
                v2_front = atoi(version2.substr(0,v2_pot_pos).c_str());
                v2_behind = version2.substr(v2_pot_pos + 1);
            }else{
                if(version2.size() != 0)v2_front = atoi(version2.c_str());
                else v2_front = 0;
                v2_behind = "";
            }
    
            if(v1_front > v2_front)
                return 1;
            else if(v1_front < v2_front)
                return -1;
            else{
                return this->compareVersion(v1_behind, v2_behind);
            }
        }
    };