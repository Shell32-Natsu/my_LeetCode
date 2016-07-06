#Rotate Image

[Rotate Image](https://leetcode.com/problems/rotate-image/ "Rotate Image")

将矩阵顺时针旋转90度，一开始准备用递归，但是被多维数组指针狠狠地坑了。。。

C:

    void rotate(int **matrix, int n) {
        int swap_t;
        int i, j;
        for(j = 0; j < n / 2; j++){
            for(i = j; i < n - 1 - j; i++){
                swap_t = matrix[j][i];
                matrix[j][i] = matrix[n - 1 - i][j];
                matrix[n - 1 - i][j] = matrix[n - 1 - j][n - 1 - i];
                matrix[n - 1 - j][n - 1 - i] = matrix[i][n - 1 - j];
                matrix[i][n - 1 - j] = swap_t;
            }
        }
    }