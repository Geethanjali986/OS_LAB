# Program Statement: Simulate the Sequential file allocation strategies.
# SOURCE CODE
#include<stdio.h>
#include<stdlib.h>

int main()
{
    int f[50], i, st, j, len, c;

    for(i = 0; i < 50; i++)
        f[i] = 0;

    X:
    printf("\nEnter the starting block & length of file: ");
    scanf("%d%d", &st, &len);

    if (st < 0 || st + len > 50) {
        printf("Invalid block range. Please enter a valid range (0 to 49).\n");
        goto X;
    }

    for(j = st; j < (st + len); j++) {
        if(f[j] == 0) {
            f[j] = 1;
            printf("\n%d -> Allocated", j);
        }
        else {
            printf("\nBlock %d already allocated!", j);
            break;
        }
    }

    if(j == (st + len))
        printf("\nThe file is allocated to disk successfully.");

    printf("\nDo you want to enter more files? (Yes - 1 / No - 0): ");
    scanf("%d", &c);

    if(c == 1)
        goto X;
    else
        exit(0);
}
# output:
![oslab 10a](https://github.com/user-attachments/assets/df2f41b9-01d5-4c55-aaad-068b51492511)
