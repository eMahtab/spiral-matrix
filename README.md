# Spiral Matrix
Spiral Traversal of a 2D Matrix

Given a matrix of m x n elements (m rows, n columns), return all elements of the matrix in spiral order.

```
Example :

Input:

{
   {1, 2, 3, 4},
   {5, 6, 7, 8},
   {9, 10, 11, 12},
   {13, 14, 15, 16},
   {17, 18, 19, 20}
}

Output: [1, 2, 3, 4, 8, 12, 16, 20, 19, 18, 17, 13, 9, 5, 6, 7, 11, 15, 14, 10]
```

![Spiral Traversal of a 2D Matrix](spiral-traversal.PNG?raw=true "Spiral Traversal of a 2D Matrix")

![Spiral Traversal of a 2D Matrix](example.PNG?raw=true "Spiral Traversal of a 2D Matrix")

![Spiral Traversal of a 2D Matrix](examples-2.PNG?raw=true "Spiral Traversal of a 2D Matrix")


### Implementation

```java
import java.util.ArrayList;
import java.util.List;

public class App {

	public static void main(String[] args) {
		int[][] mat = {
				{1, 2, 3, 4},
				{5, 6, 7, 8},
				{9, 10, 11, 12},
				{13, 14, 15, 16},
				{17, 18, 19, 20}
		};

		
		System.out.println(spiralOrder(mat));
	}
	
	public static List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> spiral = new ArrayList<>();
        if(matrix == null || matrix.length == 0)
            return spiral;
        int rowStart = 0;
        int rowEnd = matrix.length - 1;
        int columnStart = 0;
        int columnEnd = matrix[0].length - 1;
        
        while(rowStart <= rowEnd && columnStart<= columnEnd){
            for(int i = columnStart; i <= columnEnd; i++){
                spiral.add(matrix[rowStart][i]);
            }
            
            rowStart++;
            
            for(int i = rowStart; i <= rowEnd; i++){
                spiral.add(matrix[i][columnEnd]);
            }
            
            columnEnd--;
            
            if(rowStart <= rowEnd){
              for(int i = columnEnd; i>= columnStart; i--){
                spiral.add(matrix[rowEnd][i]);
              }
            }
            
            rowEnd--;
            
            if(columnStart <= columnEnd){
                for(int i = rowEnd; i >= rowStart; i--){
                    spiral.add(matrix[i][columnStart]);
                }
            }
            
            columnStart++;
            
        }
        
        return spiral;
    }

}

```

The above implementation have runtime complexity of O(m * n) and space complexity of O(1), where m is number of rows in input matrix and n is the number of columns in the input matrix.

```
Runtime Complexity = O(m*n)
Space Complexity   = O(1)
```
