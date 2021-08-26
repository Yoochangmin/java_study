## 인스턴스 :클래스에의해 생성된 각각의 객체

------

########

모든 인스턴스가 공유하는 어떤 값이 필요할 때 그 변수는 static으로 설정 (정적 변수)

heap은 동적 메모리 입니다

static 변수는 heap 메모리에 저장되지 않고 따로 저장됨

인스턴스 변수는 new 사용할때 메모리를 할당 받지만

이것은 전체 프로그램이 메모리에 load될 때 할당 like  상수, 리터럴 

#######

-----



# Static 변수

------

- 인스턴스의 생성과 관계없이 클래스 이름으로 직접 참조함   -->클래스 변수라고도 함

  ex) Student.serialNum =100; // serailNum이 static 변수

- 멤버변수 --> 인스턴스 변수라고도 함

```static 변수 예제
#생성자 호출시마다 static변수를 이용하여 시리얼 넘버를 증가시키는 예제
public class Student {

    static  int serialNum = 10000;
    int studentID;
    String studentName;

    public Student(){
        serialNum++;
        studentID = serialNum;
    }
}

package staticex;

public class StudentTest1 {

    public static void main(String[] args){
        Student studentJ = new Student();
        System.out.println(studentJ.studentID);

        Student studentT = new Student();
        System.out.println(studentT.studentID);
		
  		System.out.println(Student.serialNum);    // 클래스 이름으로 참조
        //System.out.println(studentT.serialNum);  // 참조변수로 참조 안함 static변수는
        //System.out.println(studentT.serialNum);
    }
}
결과 값 10001
        10002
        10002
        10002
```

## %주의 사황%

```
 public static int getSerialNum(){
        int i = 10;  // 지역변수

        i++;
        System.out.println(i);
		
		### studentName = "홍길동"  //멤버변수, 인스턴스 변수
		
        return serialNum;  //static 변수, 클래스 변수
    }
```

인스턴스 변수의 경우 꼭 인스턴스(new를 통한 클래스를 이용하여 )가 먼저 생성되어야 하므로 static 변수는 인스턴스 생성과 관계없이 클래스 이름으로 직접 호출이 가능하기에

인스턴스 변수를 사용 못함



# 메모리

----

1. 스택 : 지역변수  
   - 생성과 소멸 : 함수가 호출될 떄 생성되고 함수가 끝나면 소멸함
2. 힙 : 멤버변수
   - 생성과 소멸 :인스턴스가 생성될 때 힙에 생성되고, 가바지 컬렉터가 메모리를 수거할 떄 소멸됨
3. 데이터 영역 : static
   - 프로그램이 처음 시작할 때 상수와 함께 데이터 영역에 생성, 프로그램이 끝나고 메모리를 해제할 때 소멸됨