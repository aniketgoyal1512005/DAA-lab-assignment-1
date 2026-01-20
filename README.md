#include <iostream>
using namespace std;

int binarySearchArray(int arr[], int size, int target) {
    int left = 0, right = size - 1;
    
    while (left <= right) {
        int mid =left+(right-left)/2;
        
        if (arr[mid]==target) {
            return mid;
        }
        else if (arr[mid]<target) {
            left = mid + 1;
        }
        else {
            right = mid - 1;
        }
    }
    
    return -1;
}

int main() {
    int arr[] = {2,5,8,12,16,23,38,56,72,91};
    int size = sizeof(arr) / sizeof(arr[0]);
    int target = 23;
    
    int result = binarySearchArray(arr, size, target);
    
    if (result != -1) {
        cout << "Element found at index: " << result << endl;
    } else {
        cout << "Element not found" << endl;
    }
    
    return 0;
}


#include <iostream>
using namespace std;

void merge(int arr[], int left, int mid, int right) {
    int i = left, j = mid + 1, k = 0;
    int temp[right - left + 1];
    
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp[k++] = arr[i++];
        } else {
            temp[k++] = arr[j++];
        }
    }
    
    while (i <= mid) {
        temp[k++] = arr[i++];
    }
    
    while (j <= right) {
        temp[k++] = arr[j++];
    }
    
    for (int i = left, k = 0; i <= right; i++, k++) {
        arr[i] = temp[k];
    }
}

void mergeSort(int arr[], int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

int main() {
    int arr[] = {12, 11, 13, 5, 6, 7};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    mergeSort(arr, 0, n - 1);
    int arr2[] = {38, 27, 43,3, 9, 82, 10};
    int n2 = sizeof(arr2) / sizeof(arr2[0]);
    mergeSort(arr2, 0, n2 - 1);
    
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++) {
        cout << arr[i] << " ";
    }
    cout<<endl;
    cout << "Sorted array 2: ";
    for(int i=0;i<n2;i++){
        cout<<arr2[i]<<" ";
    }
    cout << endl;
    
    return 0;
}


#include <iostream>
using namespace std;

int partition(int arr[], int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            swap(arr[i], arr[j]);
        }
    }
    swap(arr[i + 1], arr[high]);
    return i + 1;
}

void quickSort(int arr[], int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    int arr[] = {4, 2, 6, 9, 2};
    int n = sizeof(arr) / sizeof(arr[0]);
    
    quickSort(arr, 0, n - 1);
    
    cout << "Sorted array: ";
    for (int i = 0; i < n; i++)
        cout << arr[i] << " ";
    cout << endl;
    
    return 0;
}


#include<iostream>
using namespace std;

int main(){
    int arr[] = {-2,-5,6,-2,-3,1,5,-6};
    int n = sizeof(arr)/sizeof(arr[0]);
    int sum = 0;
    int max = 0;
    int start = 0;
    int end = 0;
    for(int i = 0;i<n;i++){
        if(arr[i]>0){
            int start  = i;
            break;
        }
    }
    for(int j = n-1;j>=0;j--){
        if(arr[j]>0){
            end = j;
            break;
        }
    }
    for(int k = start;k<=end;k++){
        sum += arr[k];
        if(sum<0){
            sum = 0;
        }
        if(max<sum){
            max = sum;
        }
    }
    cout<<max<<endl;
    return 0;
}
