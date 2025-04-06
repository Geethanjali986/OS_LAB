# Problem Statement: Simulate the Indexed file allocation strategies
# source code:
#include <stdio.h>
#include <stdlib.h>

int f[50], i, k, j, inde[50], n, c, p;

int main() {
    // Initialize all blocks as free (0)
    for (i = 0; i < 50; i++)
        f[i] = 0;

    x:
    printf("\nEnter index block (0-49): ");
    scanf("%d", &p);

    if (p < 0 || p >= 50) {
        printf("Invalid block number. Please enter between 0 and 49.\n");
        goto x;
    }

    if (f[p] == 0) {
        f[p] = 1;
        printf("Enter number of file blocks: ");
        scanf("%d", &n);

        if (n > 49) {
            printf("Too many blocks requested. Try again.\n");
            f[p] = 0;  // Free the index block again
            goto x;
        }

        printf("Enter the block numbers:\n");
        for (i = 0; i < n; i++) {
            scanf("%d", &inde[i]);
            if (inde[i] < 0 || inde[i] >= 50) {
                printf("Invalid block number %d. Try again.\n", inde[i]);
                f[p] = 0; // Reset index block
                goto x;
            }
        }

        for (i = 0; i < n; i++) {
            if (f[inde[i]] == 1) {
                printf("\nBlock %d already allocated. Try again.\n", inde[i]);
                f[p] = 0;  // Free the index block
                goto x;
            }
        }

        for (j = 0; j < n; j++)
            f[inde[j]] = 1;

        printf("\nBlocks allocated successfully.\n");
        printf("File indexed:\n");
        for (k = 0; k < n; k++)
            printf("%d -> %d : Allocated\n", p, inde[k]);
    } else {
        printf("Index block already allocated.\n");
        goto x;
    }

    printf("\nEnter 1 to enter more files, 0 to exit: ");
    scanf("%d", &c);
    if (c == 1)
        goto x;
    else
        exit(0);
}

# Output:
![oslab 10b](https://github.com/user-attachments/assets/0fda2b15-2660-4b80-a2ce-2e831ffbb413)

