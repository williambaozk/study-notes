## 总结

> 设置序列的前后两个指针，使用到了等差数列的和，如何大于那么前面个指针加1，如果小于那么后面个指针加1，等于时前面个指针也要加1

## 代码

```java
    public ArrayList<ArrayList<Integer> > FindContinuousSequence(int sum) {
        ArrayList<ArrayList<Integer>> result=new ArrayList<>();
        int start=1,end=2;
        while (end>start) {
            int count=(end+start)*(end-start+1)/2;
            if (count == sum) {
                ArrayList<Integer> list=new ArrayList<>();
                for (int i = start; i <= end; i++) {
                    list.add(i);
                }
                result.add(list);
                start++;
            } else if (count > sum) {
                start++;
            } else {
                end++;
            }
        }
        return result;
    }
