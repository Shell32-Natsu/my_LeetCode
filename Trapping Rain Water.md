#Trapping Rain Water

[Trapping Rain Water](https://leetcode.com/problems/trapping-rain-water/ "Trapping Rain Water")

蓄水的问题，我的想法是一个凹槽能蓄水，意味着它的两边比最低处高。考虑两边的话，最高的水面高度与较矮的一边相同。所以从左到右遍历每一个高度，对每一个高度向右寻找比它高的第一个高度，得到的就是蓄水的宽度。但是也有左边高右边低的情况，所以我先找到最高的高度，该高度左边的高度的右边都必然存在一个比它高的高度（最高的）。最高高度右边的高度则从右向左遍历。

C++；

    class Solution {
    public:
        int trap(int A[], int n) {
            int max_pos = 0, ret = 0;
            for(int i = 1; i < n; i++){
                if(A[i] > A[max_pos]) max_pos = i;
            }
    
            for(int i = 0; i < max_pos; i++){
                for(int j = i + 1; j <= max_pos; j++){
                    if(A[j] >= A[i]){
                        for(int k = i + 1; k < j; k++){
                            ret = ret + (A[i] - A[k]);
                        }
                        i = j;
                        i--;
                        break;
                    }
                }
            }
    
            for(int i = n - 1; i > max_pos; i--){
                for(int j = i - 1; j >= max_pos; j--){
                    if(A[j] >= A[i]){
                        for(int k = i - 1; k > j; k--){
                            ret = ret + (A[i] - A[k]);
                        }
                        i = j;
                        i++;
                        break;
                    }
                }
            }
            return ret;
        }
    };