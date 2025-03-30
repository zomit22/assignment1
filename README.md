#include <iostream>
using namespace std;

void simpleSort(int arr[], int n, int &swaps) {
    swaps = 0;
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[i]) {
                swap(arr[i], arr[j]);
                swaps++;
            }
        }
    }
}

void bubbleSort(int arr[], int n, int &swaps) {
    swaps = 0;
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
                swaps++;
            }
        }
    }
}

void insertionSort(int arr[], int n, int &swaps) {
    swaps = 0;
    for (int i = 1; i < n; i++) {
        int key = arr[i], j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            swaps++;
            j--;
        }
        arr[j + 1] = key;
    }
}

void selectionSort(int arr[], int n, int &swaps) {
    swaps = 0;
    for (int i = 0; i < n - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIdx]) {
                minIdx = j;
            }
        }
        if (minIdx != i) {
            swap(arr[i], arr[minIdx]);
            swaps++;
        }
    }
}

void printArray(int arr[], int n) {
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
}

int main() {
    int n;
    cout << "Enter number of elements: ";
    cin >> n;

    int arr[100];
    cout << "Enter elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    int swaps;

    simpleSort(arr, n, swaps);
    cout << "Simple Sort: ";
    printArray(arr, n);
    cout << "Swaps: " << swaps << endl;

    bubbleSort(arr, n, swaps);
    cout << "Bubble Sort: ";
    printArray(arr, n);
    cout << "Swaps: " << swaps << endl;

    insertionSort(arr, n, swaps);
    cout << "Insertion Sort: ";
    printArray(arr, n);
    cout << "Swaps: " << swaps << endl;

    selectionSort(arr, n, swaps);
    cout << "Selection Sort: ";
    printArray(arr, n);
    cout << "Swaps: " << swaps << endl;

    return 0;
}
