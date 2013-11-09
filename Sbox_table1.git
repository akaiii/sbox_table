package javaapplication1;

import java.util.*;
//import java.lang.*;
//import java.lang.Character;

public class Sbox_table {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        String input = sc.nextLine();
        /*char [] x = {'0','1','2','3','4','5','6','7','8'
         ,'9','a','b','c','d','e','f'};
         char [] y = {'0','1','2','3','4','5','6','7','8'
         ,'9','a','b','c','d','e','f'};*/   //等待使用中

        int[][] xy = new int[16][16];       //?
        int n = 100011011;                  //作mod的固定值
        int inv;
        String answer;
        int input_int;
        input_int = convert(input);                     //十六進制轉二進制        
        inv = FindInverse(n,input_int);          //找出乘法反元素
       // answer = finalConvert(inv);                   //最後轉換
        
       // System.out.println(answer);
    }
//***************************************************//找出乘法反元素
    public static int FindInverse(int m, int b) {    
        int[] T = {0, 0, 0};
        int[] A = {1, 0, m};
        int[] B = {0, 1, b};

        while (B[2] != 1) {
            
            int[] info = Division(A[2], B[2]);  //求Q (商)          
            int Q = info[0];
            
            for (int i = 0; i < 2; i++) {   //做XOR 和 交換
                T[i] = A[i]^(B[i] * Q);
                A[i] = B[i];
                B[i] = T[i];
            }
            T[2] = info[1];            //給餘數 再交換
            A[2] = B[2];
            B[2] = T[2];
        }    

        return B[1];
    }
//***************************************************/// 改寫多項式除法
    public static int[] Division(int x1, int y1) {    
        String x = Integer.toString(x1);                //整數轉字元陣列
        String y = Integer.toString(y1);
        System.out.println(y);
      
        int[] n1 = new int[x.length()];
        int[] n2 = new int[y.length()];
        
        for (int i = 0; i < x.length(); i++) {
            n1[i] =  Character.getNumericValue(x.charAt(i));
            
        }
        
        for (int i = 0; i < y.length(); i++) {
            n2[i] =  Character.getNumericValue(y.charAt(i));
        }
        //---------------------------------------------
        int[] t1 = new int[y.length()];
        int[] Q = new int[y.length()];
        int count = 0;
        boolean zero = true;
        int[] info = new int[2];
        int k = 0;
        
        for(int i=0;i<y.length();i++)
            Q[i] = 0;
        for (int j = 0; j < 20; j++) {
            for (int i = 0; i < y.length() - k; i++) {    // 求餘數
                t1[i] = n1[i] ^ n2[i];
                n1[i] = t1[i];
                if ((i >= 2) && (n1[i] == 0) && (zero == true)) {
                    Q[count] = 1;
                    count += 1;
                } else if ((i >= 2) && (n1[i] == 1)) {
                    zero = false;
                }
            }
            if (x.length() - 7 >= 0) {
                k = 7;

            } else {
                info[1] = Integer.valueOf(String.valueOf(n1));
                break;
            }
            
        }
        //info : [0] 為 商, [1] 為 餘數

        info[0] = Integer.valueOf(String.valueOf(Q));
        return info;
    }
//*****************************************************///十六進制轉二進制    
    public static int convert(String x){                   
        int[] b = {0, 1, 10, 11, 100, 101, 110, 111, 1000, 1001,
                   1010, 1011, 1100,1101, 1110, 1111};  //轉二進制表
        //String str = Integer.toString(x);
        int i1 = Character.getNumericValue(x.charAt(0));
        int i2 = Character.getNumericValue(x.charAt(1));
        System.out.println(b[i1]);                     //測試用
        return (b[i1]*10000+b[i2]);              
    }
//******************************************************//最後結果轉換    
 /*   public static String finalConvert(int inv){
        int[] x = {10001111,
                   11000111,
                   11100011,
                   11110001,
                   11111000,
                   01111100,
                   00111110,
                   00011111};                      //與乘法反元素相乘  固定值表 
         String str;                               //str系列 都做暫存
         int[] y = {0,1,1,0,0,0,1,1};              //最後XOR的固定值
         int[] a = new int[8];                     //放結果陣列
         int count = 8;                            //反相計數
         char[] n = new char[8];                   //跟自己做XOR
         
         for(int i=0;i<8;i++){
             str = Integer.toString(x[i]^inv);      //inv先補0再過來做(未做)
             for(int k=0;k<8;k++){
                n[k] = str.charAt(k);
             }
             for(int j=1;j<8;j++){
                n[0] ^= n[j];
             }             
             a[count] = Character.getNumericValue(n[0])^y[count];
             count--;
         }
//---------------------------------------------------------//結果轉換為16進制
         int[] pushfour = new int[4];
         int[] pushfour1 = new int[4];
         int z,z1;
         int h;                                           //?
         System.arraycopy(a, 0 , pushfour , 0 , 4 );        //陣列複製
         z = Integer.valueOf(String.valueOf(pushfour));     //將整數陣列做合併轉字串
         String str1 = Integer.toHexString(z);              //轉換 (待測)
         System.arraycopy(a , 4 , pushfour1 , 0 , 4);      //做後面4位元
         z1 = Integer.valueOf(String.valueOf(pushfour1));
         String str2 = Integer.toHexString(z1);
         String str3 = str1 + str2 ;
         
        return str3;
    }*/
}
