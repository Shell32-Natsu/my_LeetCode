#Maximum Gap

[Maximum Gap](https://leetcode.com/problems/maximum-gap/ "Maximum Gap")

使用桶排序，代码写的很渣，把元素放到桶中之后就不需要考虑桶内的元素之间的差（因为肯定小于桶的宽度），只要考虑两个相邻的有元素的桶的最大和最小值之间的关系。

C++:

    class Solution {
    public:
        int maximumGap(vector<int> &num) {
            int length = num.size();
            if (length < 2) return 0;
            int max_item = num[0], min_item = num[0];
    
    
            for(int i = 1; i < length; i++){
                if(num[i] > max_item) max_item = num[i];
                else if(num[i] < min_item) min_item = num[i];
            }
    
            int bucket_gap = ( max_item - min_item ) / length >= 1 ? ( max_item - min_item ) / length : 1;
            int bucket_size = ( max_item - min_item ) / bucket_gap + 1;
    
            vector<vector<int> > bucket(bucket_size);
    
            for(int i = 0; i < length; i++){
                bucket[(num[i] - min_item) / bucket_gap].push_back(num[i]);
            }
    
            int max_gap = 0;
    
            for(int i = 0; i < bucket_size; i++){
                sort(bucket[i].begin(), bucket[i].end());
            }
    
            for(int i = 0; i < bucket.size(); i++){
                for(int j = 0; j < bucket[i].size(); j++){
                    if(j == 0 && i != 0 && bucket[i - 1].size() > 0){
                        if(bucket[i][j] - bucket[i - 1][bucket[i - 1].size() - 1] > max_gap) max_gap = bucket[i][j] - bucket[i - 1][bucket[i - 1].size() - 1];
                    }
                    if(j == 0 && i != 0 && bucket[i - 1].size() == 0){
                        int t = i - 1;
                        for(; t >= 0 && bucket[t].size() == 0; t--);
                        if(bucket[i][j] - bucket[t][bucket[t].size() - 1] > max_gap) max_gap = bucket[i][j] - bucket[t][bucket[t].size() - 1];
                    }
                    if(j > 0){
                        if(bucket[i][j] - bucket[i][j - 1] > max_gap)max_gap = bucket[i][j] - bucket[i][j - 1];
                    }
                }
            }
    
            return max_gap;
        }
    };