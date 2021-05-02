

public class main {

    public static void main(String[] args) {
        int[] arr = {2, 5, 42, -34, 5, 0, 15, -156, 2424, -2424, 4562, -654};
        int n = arr.length;
        mergeSort(arr, 0, n - 1);
        for (int h = 0; h < n; h++) {
            System.out.print(arr[h] + " ");
        }
    }


    public static void mergeSort ( int[] elements, int low, int high){
        if (low < high) {
            int mid = (low + high) / 2;
            mergeSort(elements, low, mid);
            mergeSort(elements, mid + 1, high);
            merge(elements, low, mid, high);
        }
    }
    private static void merge ( int[] subset, int low, int mid, int high){
        int n = high - low + 1;
        int[] Temp = new int[n];
        int i = low, j = mid + 1;
        int k = 0;
        while (i <= mid || j <= high) {
            if (i > mid) {
                Temp[k++] = subset[j++];
            }
            else if (j > high) {
                Temp[k++] = subset[i++];
            }
            else if (subset[i] < subset[j]) {
                Temp[k++] = subset[i++];
            }
            else {
                Temp[k++] = subset[j++];
            }
        }
        for (j = 0; j < n; j++) {
            subset[low + j] = Temp[j];
        }
    }
}
