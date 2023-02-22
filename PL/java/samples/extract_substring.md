# 비트 연산자(&)를 이용한 이진수 변환

```java
public class AndOperatorBitShift {

    public static String bitshifts(int num) {
        final int BITMASK = 1;
        String s = "";

        for (int i=0; i<31; i++) {
            s = (num & BITMASK) + s; // num과 BITMASK를 bit 이진수 변환 후 &연산
            num>>=1;
        }
        return s.;

    }
    public static void main(String[] args) {
        int intNum = 123;
        int intNum2 = -123;

        System.out.printf("%d: %s\n",intNum, bitshifts(intNum));
        System.out.printf("%d: %s\n",intNum2, bitshifts(intNum2));

    }
}
```