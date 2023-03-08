# quick-sort
quick sort
### 퀵 정렬(Quick sort)
은 가장 널리 사용되는 정렬 알고리즘 중 하나입니다. 이 알고리즘은 분할 정복(Divide and Conquer) 전략을 사용하며, 일반적으로 재귀적으로 구현됩니다.

퀵 정렬은 배열을 정렬하는 데 사용됩니다. 이 알고리즘의 핵심 아이디어는 하나의 요소를 피벗(Pivot)으로 선택하고 피벗보다 작은 요소는 피벗의 왼쪽에, 큰 요소는 피벗의 오른쪽에 배치하는 것입니다. 그런 다음, 피벗의 왼쪽 부분 배열과 오른쪽 부분 배열을 각각 재귀적으로 정렬합니다.

퀵 정렬은 다른 정렬 알고리즘보다 일반적으로 빠르게 작동하며, 최악의 경우에도 O(n log n)의 시간 복잡도를 가지지만, 피벗의 선택 및 배열의 분할 방법에 따라 성능이 크게 좌우될 수 있습니다. 또한, 퀵 정렬은 정렬하는 배열의 크기가 작을 때는 다른 알고리즘보다 느리게 작동할 수 있습니다.

### Java 코드

package project;

import java.util.Arrays;

public class quick {
    public static void quickSort(int[] arr, int left, int right) {
        if (left < right) {
            int pivotIndex = partition(arr, left, right);
            quickSort(arr, left, pivotIndex - 1);
            quickSort(arr, pivotIndex + 1, right);
        }
    }
    
    private static int partition(int[] arr, int left, int right) {
        int pivotValue = arr[right];
        int i = left - 1;
        
        for (int j = left; j < right; j++) {
            if (arr[j] <= pivotValue) {
                i++;
                swap(arr, i, j);
            }
        }
        
        swap(arr, i + 1, right);
        return i + 1;
    }
    
    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }
    
    public static void main(String[] args) {
        int[] arr = {5, 2, 9, 3, 6, 7};
        System.out.println("Original array: " + Arrays.toString(arr));
        quickSort(arr, 0, arr.length - 1);
        System.out.println("Sorted array: " + Arrays.toString(arr));
    }

