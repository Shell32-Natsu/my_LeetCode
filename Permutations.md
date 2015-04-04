#Permutations 

[Permutations](https://leetcode.com/problems/permutations/ "Permutations")

使用递归算法生成全排列，由于每一次递归都要创建和销毁vector，所以效率受到了影响.

C++:

    class Solution {
    public:
        vector<vector<int> > permute(vector<int> &num) {
            if(num.size() == 1){
                vector<vector<int> > ret;
                ret.push_back(num);
                return ret;
            }
    
            vector<vector<int> > ret;
            for(int i = 0; i < num.size(); i++){
                vector<int> t(num);
                t.erase(t.begin() + i);
                vector<vector<int> > ret_t;
                ret_t = this->permute(t);
                for(int j = 0; j < ret_t.size(); j++){
                    ret_t[j].insert(ret_t[j].begin(), num[i]);
                }
                ret.insert(ret.end(), ret_t.begin(), ret_t.end());
            }
            return ret;
        }
    };

把vector的创建放到for循环外面。。。时间从33ms变为29ms，还是很慢。。

C++:

    class Solution {
    public:
        vector<vector<int> > permute(vector<int> &num) {
            if(num.size() == 1){
                vector<vector<int> > ret;
                ret.push_back(num);
                return ret;
            }
    
            vector<vector<int> > ret;
            vector<int> t(num);
            vector<vector<int> > ret_t;
            for(int i = 0; i < num.size(); i++){
                t = num;
                t.erase(t.begin() + i);
                ret_t = this->permute(t);
                for(int j = 0; j < ret_t.size(); j++){
                    ret_t[j].insert(ret_t[j].begin(), num[i]);
                }
                ret.insert(ret.end(), ret_t.begin(), ret_t.end());
            }
            return ret;
        }
    };