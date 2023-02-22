# Shift를 이용한 이진수 표현

```java
public class BitShiftDicimal {

    public static String decimalToBinary(int input) {
        String str = "";

        // 십진수 이진수 변환
        for (int i=0; i<31; i++) {
            int bit = input%2;

            str = (bit>=0) ? bit+str: (-bit)+str;
            input>>=1; // input/2 대입(input/=2)
        }

        return str;
    }

    public static void main(String[] args) {
        int NUM1 = 123;
        int NUM2 = -123;

        System.out.printf("%d: %s\n",NUM1, decimalToBinary(NUM1));
        System.out.printf("%d: %s\n",NUM2, decimalToBinary(NUM2));
    }
}
```

