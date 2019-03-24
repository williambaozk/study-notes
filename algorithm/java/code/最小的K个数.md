## 总结

> 根据快速排序的选择算法，partition处对应的值都大于前面的值，如果等于k那么直接返回，如果大于k，那么r等于j-1，小于k,那么l等于j+1

## 代码

```java
    public ArrayList<Integer> GetLeastNumbers_Solution(int[] input, int k) {
        ArrayList<Integer> result = new ArrayList<>();
        if (k > input.length || input.length == 0) {
            return result;
        }
        findKthSmallest(input, k - 1);
        for (int i = 0; i < k; i++) {
            result.add(input[i]);
        }
        return result;
    }

    private void findKthSmallest(int[] input, int k) {
        int l = 0, r = input.length - 1;
        while (l < r) {
            int j = partition(input, l, r);
            if (j == k) {
                break;
            } else if (j > k) {
                r = j - 1;
            } else {
                l = j + 1;
            }
        }
    }

    private int partition(int[] input, int l, int r) {
        int x = input[r];
        int i = l - 1;
        for (int j = l; j < r; j++) {
            if (input[j] < x) {
                i++;
                swap(input, i, j);
            }
        }
        swap(input, i + 1, r);
        return i + 1;
    }

    private void swap(int[] input, int i, int j) {
        int temp = input[i];
        input[i] = input[j];
        input[j] = temp;
    }
