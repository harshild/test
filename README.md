import java.util.Arrays;

/**
 * Created by harshild on 5/2/2016.
 */
public class CC {
    public static boolean flag;
    public static int count;
    public static int findWater(int input1, int input2,int[] input3)
    {
        int waterFilled = 0;




        return waterFilled;
    }


    public static int checkGrid(int r, int c, int[][] grid) {
        flag = true;
        count = 0;
        int tempCount = 0;

        while (flag) {
            for (int i = 0; i < r; i++) {
                for (int j = 0; j < c; j++) {
                    if ((i == 0 || j==0)||(i == r - 1 || j == c - 1)){

                    }//Ignore if sides
                    else {
                        int startAndEnd = min(grid[i][0], grid[i][c - 1]);
                        int[] afterElem = new int[c-j];
                        for (int k = j,z=0 ;k < c; k++,z++) {
                            afterElem[z] = grid[i][k];
                        }
                        int toEnd = max(afterElem);
                        int[] tempList =new int[]{grid[i - 1][j],grid[i][j - 1],
                                grid[i + 1][j], grid[i][j + 1]};

                        int minVal = min(tempList);
                        if(minVal > grid[i][j]) {
                            grid[i][j] += 1;
                            System.out.println(i+"   "+j);
                            count += 1;
                            i=0;
                            j=0;
                        }
                        else if(startAndEnd>grid[i][j]) {
                            if(r<c) {
                                if(startAndEnd == grid[i][j] + 1) {
                                    grid[i][j] += 1;
                                    System.out.println(i+"   "+j);
                                    count += 1;
                                    i=0;
                                    j=0;
                                }
                            }

                            else {
                                if(grid[i-1][j] > grid[i][j]) {
                                    grid[i][j] += 1;
                                    System.out.println(i+"   "+j);
                                    count += 1;
                                    i=0;
                                    j=0;
                                }
                            }
                        }
                        else if(toEnd>grid[i][j]){
                            int elemX = -1;
                            for(int n=j;n<c;n++){
                                if(grid[i][n] == toEnd)
                                    elemX = n;
                            }
                            for(int n=elemX;n>=j;n--){
                                if(grid[i][n] == toEnd)
                                    elemX = n;
                            }

                        }
                    }
                    if (tempCount == count && i==r - 1 && j==c - 1)
                        flag = false;
                }
            }
            tempCount = count;
        }

        return count;
    }

    public static int GetWaterLevel(int input1,int input2,int[] input3) {

        int[][] grid= new int[input1][input2];

        for (int i = 0,k=0; i < input1; i++) {
            for (int j = 0; j < input2; j++) {
                grid[i][j] = input3[k];
                k++;
            }
        }

        return checkGrid(input1, input2, grid);
    }

    public static int min(int... a){
        Arrays.sort(a);
        return a[0];
    }
    public static int max(int... a){
        Arrays.sort(a);
        return a[a.length-1];
    }
}
class aa{
    public static void main(String[] args) {
        // System.out.println(CC.GetWaterLevel(3,6,new int[]{3,3,4,4,4,2,3,1,3,2,1,4,7,3,1,6,4,1}));
        System.out.println(CC.GetWaterLevel(4,8,new int[]{
                1,7,1,6,7,6,1,7,
                7,6,6,1,6,6,1,6,
                6,1,4,6,5,4,6,1,
                1,6,6,6,6,6,6,6})
        );
        /*System.out.println(CC.GetWaterLevel(7,6,new int[]{
                3,3,4,4,4,2,
                3,1,3,2,1,4,
                8,8,8,8,8,8,
                7,3,1,6,4,1,
                8,8,8,8,8,8,
                9,9,9,9,9,9,
                10,10,10,10,10,10}));*/
        /*System.out.println(CC.GetWaterLevel(7,6,new int[]{
                10,10,10,10,10,10,
                10,1,1,1,1,10,
                10,2,2,2,2,10,
                10,1,1,1,1,10,
                10,2,2,2,2,10,
                10,1,1,1,1,10,
                10,10,10,10,10,10}));*/
      /*  System.out.println(CC.GetWaterLevel(3,6,new int[]{
                3,3,4,4,4,2,
                3,1,3,2,1,4,
                7,3,1,6,4,1
        }));*/
    }
}

