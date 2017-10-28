# A-B-Problem-II

A + B Problem II

Problem Description
I have a very simple problem for you. Given two integers A and B, your job is to calculate the Sum of A + B.
 
Input

The first line of the input contains an integer T(1<=T<=20) which means the number of test cases. Then T lines follow, each line consists of two positive integers, A and B. Notice that the integers are very large, that means you should not process them by using 32-bit integer. You may assume the length of each integer will not exceed 1000. 

Output

For each test case, you should output two lines. The first line is "Case #:", # means the number of the test case. The second line is the an equation "A + B = Sum", Sum means the result of A + B. Note there are some spaces int the equation. Output a blank line between two test cases.
 
Sample Input

2
1 2
112233445566778899 998877665544332211
 
 
Sample Output

Case 1:

1 + 2 = 3

Case 2:

112233445566778899 + 998877665544332211 = 1111111111111111110 

代码：

#include <stdio.h>

#include <string.h>

int main(){

    char str1[1001], str2[1001];
    
    int t, i, len_str1, len_str2, len_max, num = 1, k;
    
    scanf("%d", &t);
    
    getchar();
    
    while(t--){
    
        int a[1001] = {0}, b[1001] = {0}, c[1001] = {0};
        
        scanf("%s", str1);
        
        len_str1 = strlen(str1);
        
        for(i = 0; i <= len_str1 - 1; ++i)
        
            a[i] = str1[len_str1 - 1 - i] - '0';
            
        scanf("%s",str2);
        
        len_str2 =  strlen(str2);
        
        for(i = 0; i <= len_str2 - 1; ++i)
        
            b[i] = str2[len_str2 - 1 - i] - '0';
            
        if(len_str1 > len_str2)
        
            len_max = len_str1;
            
        else
        
            len_max = len_str2;
            
        k = 0;
        
        for(i = 0; i <= len_max - 1; ++i){
        
            c[i] = (a[i] + b[i] + k) % 10;
            
            k = (a[i] + b[i] + k) / 10;
            
        }
        
        if(k != 0)
        
        c[len_max] = 1;
        
        printf("Case %d:\n", num);
        
        num++;
        
        
        printf("%s + %s = ", str1, str2);
        
        
        if(c[len_max] == 1)
        
            printf("1");
            
        for(i = len_max - 1; i >= 0; --i){
        
            printf("%d", c[i]);
            
        }
        printf("\n");
        
        if(t >= 1)
        
            printf("\n");
            
    }
    
    return 0;
    

}
