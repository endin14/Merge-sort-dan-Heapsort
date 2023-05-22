public class App {
	public static void main(String args[]) {
		int arr[] = {45,27, 21, 5, 3};

		System.out.print("Sebelum Diurutkan : ");
		printArray(arr);

		System.out.print("Sesudah Diurutkan : ");
        sort(arr);
		printArray(arr);
	}

	static void sort(int arr[]) {
		int n = arr.length;
        
		// Membangun heap (menyusun ulang array)
		for (int i = n / 2 - 1; i >= 0; i--) {
			heapShort(arr, n, i);
        }

		// Satu per satu ekstrak elemen dari heap
		for (int i = n - 1; i >= 0; i--) {
			// Pindahkan root saat ini ke akhir
			int temp = arr[0];
			arr[0] = arr[i];
			arr[i] = temp;

			// panggil max heapShort pada heap yang dikurangi
			heapShort(arr, i, 0);
		}
	}

	static void heapShort(int arr[], int n, int i) {
		int largest = i; // Inisialisasi terbesar sebagai root
		int l = i; // kiri = i
		int r = i + 1; // kanan = i + 1

		// Jika leftc child lebih besar dari root
		if (l < n && arr[l] > arr[largest]) {
			largest = l;
        }

		// Jika right child lebih besar dari root
		if (r < n && arr[r] > arr[largest]) {
			largest = r;
        }

		// Jika terbesar bukan root
		if (largest != i) {
			int swap = arr[i];
			arr[i] = arr[largest];
			arr[largest] = swap;

			heapShort(arr, n, largest);
		}

	}

	// Fungsi untuk mencetak array
	static void printArray(int arr[]) {
		int n = arr.length;
		for (int i = 0; i < n; ++i) {
			System.out.print(arr[i] + " ");
        }
		System.out.println();
	}
}

Merge Sort

public class App {
        public static void main(String[] args) {
            int[] arr = {32, 12, 17, 97, 79};
            mergeSort(arr, 0, arr.length - 1);
            
            System.out.println("Hasil pengurutan menggunakan merge sort:");
            for (int num : arr) {
                System.out.print(num + " ");
            }
        }
    
        public static void mergeSort(int[] arr, int left, int right) {
            if (left < right) {
                int mid = (left + right) / 2;
                mergeSort(arr, left, mid);
                mergeSort(arr, mid + 1, right);
                merge(arr, left, mid, right);
            }
        }

        public static void merge(int[] arr, int left, int mid, int right) {
            int n1 = mid - left + 1;
            int n2 = right - mid;
            
            int[] leftArr = new int[n1];
            int[] rightArr = new int[n2];
            
            for (int i = 0; i < n1; i++) {
                leftArr[i] = arr[left + i];
            }
            for (int j = 0; j < n2; j++) {
                rightArr[j] = arr[mid + 1 + j];
            }

            int i = 0, j = 0, k = left;
            
            while (i < n1 && j < n2) {
                if (leftArr[i] <= rightArr[j]) {
                    arr[k] = leftArr[i];
                    i++;
                } else {
                    arr[k] = rightArr[j];
                    j++;
                }
                k++;
            }
            
            while (i < n1) {
                arr[k] = leftArr[i];
                i++;
                k++;
            }
            
            while (j < n2) {
                arr[k] = rightArr[j];
                j++;
                k++;
            }
        }
    }
