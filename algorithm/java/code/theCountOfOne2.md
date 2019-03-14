## 代码

```java
  //for循环
  public static int theCountOfOne2(int number) {
		String binary=Integer.toBinaryString(number);
		int count=0;
		for(int i=0;i<binary.length();i++) {
			if(binary.charAt(i)=='1') {
				count++;
			}
		}
		return count;
	}
  //位运算
	public static int theCountOfOne2(int number) {
		int count=0;
		while(number!=0) {
			if((number&1)==1) {
				count++;
			}
			number>>>=1;//>>>和>>的区别
		}
		return count;
	}
```

```java
   public int numberOf1(int n){
   	return Integer.bitCount(n);
}
```
