Develop a C program to demonstrate Address Resolution Protocol (ARP).



#include <stdio.h> 
#include <string.h> 
int main() 
{ 
    char ip[4][20] = {"192.168.1.1", "192.168.1.2", 
                      "192.168.1.3", "192.168.1.4"}; 
 
    char mac[4][20] = {"AA:BB:CC:DD:EE:01", 
                       "AA:BB:CC:DD:EE:02", 
                       "AA:BB:CC:DD:EE:03", 
                       "AA:BB:CC:DD:EE:04"}; 
 
    char searchIP[20]; 
    int i, found = 0; 
 
    printf("Enter IP Address: "); 
    scanf("%s", searchIP); 
 
    for(i = 0; i < 4; i++) 
    { 
        if(strcmp(searchIP, ip[i]) == 0) 
        { 
            printf("\nARP Reply\n"); 
            printf("IP Address  : %s\n", ip[i]); 
            printf("MAC Address : %s\n", mac[i]); 
            found = 1; 
            break; 
        } 
    } 
    if(found == 0) 
        printf("\nARP: IP Address not found in ARP Table.\n");
            return 0; 
}



















O U T P U T 



Enter IP Address: 192.168.1.2 
IP Address  : 192.168.1.2 
MAC Address : AA:BB:CC:DD:EE:02 
Enter IP Address: 192.168.1.10 
ARP: IP Address not found in ARP Table.
