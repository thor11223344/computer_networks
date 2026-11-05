Q)   Develop a C program to compute: 
• CRC at the transmitter.  
• Syndrome at the receiver.





#include <stdio.h> 
#include <string.h> 
 
void crc(char data[], char key[]) 
{ 
    int i, j, n = strlen(data), k = strlen(key); 
 
    for (i = 0; i <= n - k; i++) 
    { 
        if (data[i] == '1') 
        { 
            for (j = 0; j < k; j++) 
                data[i + j] = (data[i + j] == key[j]) ? '0' : '1'; 
        } 
    } 
} 
 
int main() 
{ 
    char data[50], key[20]; 
    char temp[100], crc_value[20], codeword[100]; 
 
    int n, k, i; 
 
    printf("Enter data: "); 
    scanf("%s", data); 
 
    printf("Enter generator: "); 
    scanf("%s", key);
     n = strlen(data); 
    k = strlen(key); 
 
    /* Transmitter */ 
    strcpy(temp, data); 
 
    for (i = 0; i < k - 1; i++) 
        strcat(temp, "0"); 
 
    crc(temp, key); 
 
    /* Store CRC */ 
    strcpy(crc_value, temp + n); 
 
    printf("\nCRC = %s", crc_value); 
 
    /* Create codeword */ 
    strcpy(codeword, data); 
    strcat(codeword, crc_value); 
 
    printf("\nCodeword = %s", codeword); 
 
    /* Receiver */ 
    crc(codeword, key); 
 
    printf("\nSyndrome = %s", codeword + n); 
 
    return 0; 
}













0 U T P U T 




Input: 


Enter data: 1101011011 
Enter generator: 10011 
 
Output: 



CRC = 1110 
Codeword = 11010110111110 
Syndrome = 0000 
