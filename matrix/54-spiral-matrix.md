

Pattern Name:Boundary Traversal

My Approach

Tried to manually simulate spiral direction.
Traversed top row, right column, bottom row, left column.
Forgot to properly manage boundary updates.
Mixed up row/column indices.
Missed safety checks → caused duplicates / off-by-one errors.

Studied Approach

Maintain 4 boundaries: top, bottom, left, right.
Use while (top <= bottom && left <= right).
Traverse in 4 steps:
Top row → top++
Right column → right--
Bottom row (if valid) → bottom--
Left column (if valid) → left++
Add safety checks before bottom row and left column to avoid duplicates.

TC: O(m x n) we visit each cell once
SC: O(1) since we just made arraylist to add elements in it and return it so it doesn’t count and hence the sc is O(1)


class Solution {
    public List<Integer> spiralOrder(int[][] matrix) {
        int m = matrix.length;
        int n = matrix[0].length;
        int top = 0;
        int bottom = m-1;
        int left = 0;
        int right = n-1;
        ArrayList<Integer> result = new ArrayList<>();

        while(top <= bottom && left <= right){
            for(int col = left; col <= right;col++){
                result.add(matrix[top][col]);
            }
            top++;
            for(int i = top; i <= bottom;i++){
                result.add(matrix[i][right]);
            }
            right--;
            
            if (top <= bottom){
                for(int i = right; i >= left;i--){
                result.add(matrix[bottom][i]);
                }
                bottom--;
            }
            
            if (left <= right){
                for(int row = bottom; row >= top; row--){
                result.add(matrix[row][left]);
                }
                left++;
            }
            
        }
        return result;
    }
}