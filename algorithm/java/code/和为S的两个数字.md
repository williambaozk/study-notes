## 总结

> 设置前后两个指针，如果相加大于则后面个指针减，小于那么前面个指针加，相等则返回

## 代码

```java
    public ArrayList<Integer> FindNumbersWithSum(int [] array,int sum) {
        int i=0,j=array.length-1;
        while (i < j) {
            int count=array[i]+array[j];
            if (count == sum) {
                ArrayList<Integer> arrayList=new ArrayList<>();
                arrayList.add(array[i]);
                arrayList.add(array[j]);
            return arrayList;
            } else if (count > sum) {
                j--;
            } else {
                i++;
            }
        }
        return new ArrayList<>();
    }
