# Object 관련

```java
public class ObjectTest {
    public static void main(String[] args) {
        Object obj1 = new Object();
        Object obj2 = new Object();

        System.out.println(obj1.hashCode());
        System.out.println(Integer.toHexString(obj1.hashCode())); // hashCode(): 객채의 주소값을 변환하여 생성한 객체의 고유한 정수값

        System.out.println(obj1 == obj2); // 주소 비교
        System.out.println(obj1.equals(obj2)); // 내용 비교


        System.out.println(obj1);
//        String str = obj1.getClass().getName() + '@' + Integer.toHexString(obj1.hashCode());
//        System.out.println(str);

        Object objstr = new String("Good");
        System.out.println(objstr);
        System.out.println(objstr.getClass().getName()); // 클래스 출력

        // instanceof: 객체 타입 확인
        System.out.println(objstr instanceof Object);
        System.out.println(objstr instanceof String);

        String hello = "hello";
        System.out.println(hello.getClass()); // 클래스 출력
    }
}

```