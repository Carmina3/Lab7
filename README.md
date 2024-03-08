/***************
Carmina Sanchez
Lab 7 for CS1
3/7/2024
Thurs 2:30-3:30
****************/

#include <stdio.h>
#include <stdlib.h>

#define SIZE 9

// Function to print the number of swaps for each value
void Swap(int arr[], int swapCounts[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d: # of times %d is swapped\n", arr[i], swapCounts[i]);
    }
}

// Bubble Sort with swap count tracking
void bubbleSort(int arr[], int size, int *totalSwaps, int swapCounts[]) {
    *totalSwaps = 0;
    int i, j, temp;
    for (i = 0; i < size - 1; i++) {
        for (j = 0; j < size - i - 1; j++) {
            if (arr[j] > arr[j+1]) {
                temp = arr[j];
                arr[j] = arr[j+1];
                arr[j + 1] = temp;
                (*totalSwaps)++;
                swapCounts[j]++;
                swapCounts[j + 1]++;
            }
        }
    }
}

// Selection Sort with swap count
void selectionSort(int arr[], int size, int *totalSwaps, int swapCounts[]) {
    *totalSwaps = 0;
    int i, j, min_idx, temp;
    for (i = 0; i < size - 1; i++) {
        min_idx = i;
        for (j = i + 1; j < size; j++)
            if (arr[j] < arr[min_idx])
                min_idx = j;
        if (min_idx != i) {
            temp = arr[min_idx];
            arr[min_idx] = arr[i];
            arr[i] = temp;
            (*totalSwaps)++;
            swapCounts[i]++;
            swapCounts[min_idx]++;
        }
    }
}

int main() {
    int array1[SIZE] = {97, 16, 45, 63, 13, 22, 7, 58, 72};
    int array2[SIZE] = {90, 80, 70, 60, 50, 40, 30, 20, 10};

    int swapCounts1[SIZE] = {0};
    int swapCounts2[SIZE] = {0};

    int totalSwaps1, totalSwaps2, totalSwaps3, totalSwaps4;

    printf("Bubble Sort on array1:\n");
    bubbleSort(array1, SIZE, &totalSwaps1, swapCounts1);
    Swap(array1, swapCounts1, SIZE);
    printf("Total swaps: %d\n\n", totalSwaps1);

    printf("Bubble Sort on array2:\n");
    bubbleSort(array2, SIZE, &totalSwaps2, swapCounts2);
    Swap(array2, swapCounts2, SIZE);
    printf("Total swaps: %d\n", totalSwaps2);

    //Selection sorts array
    printf("\nSelection sorts on array1:\n");
    selectionSort(array1, SIZE, &totalSwaps3, swapCounts1);
    Swap(array1, swapCounts1, SIZE);
    printf("Total swaps: %d\n\n", totalSwaps3);

    printf("\nSelection Sort on array2:\n");
    selectionSort(array2, SIZE, &totalSwaps4, swapCounts2);
    Swap(array2, swapCounts2, SIZE);
    printf("Total swaps: %d\n", totalSwaps4);

    return 0;
}
