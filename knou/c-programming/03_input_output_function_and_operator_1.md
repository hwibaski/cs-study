# 입/출력 함수와 연산자 (1)

## 함수

- 함수란 특정한 작업을 수행하도록 설계된 독립적인 프로그램

### C 언어에서의 함수

- 표준함수
  - C언어에서 제공하는 함수
- 사용자 정의 함수
  - 사용자가 직접 정의한 함수

### 표준 입출력 함수

#### 종류

| 표준 출력함수 | 기능                |
|---------|-------------------|
| printf() | 화면에 여러 종류의 자료를 출력 |
| putchar() | 화면에 1개의 문자열을 출력   |
| puts()  | 화면에 문자열을 출력       |


| 표준 입력함수 | 기능                |
|----------|-------------------|
| scanf()  | 키보드로부터 여러 종류의 자료를 입력 |
| getchar() | 키보드로부터 1개의 문자열을 입력   |
| gets()   | 키보드로부터 문자열을 입력       |

#### printf()

- 형식: `printf("출력양식", 변수1, 변수2, ...);`
- 기능: 주어진 출력양식으로 자료를 출력한다

```c
#include <stdio.h>

void main()
{
    char ch = 'A';
    int num = 10;
    
    printf("Hello, World!\n");
    printf("ch = %c, c의 ascii 코드값은 %d\n", ch, ch);
    printf("num = %d\n", num);
}
```

| %문자    | 변환 형식                  | 인자의 자료형  |
|--------|------------------------|----------|
| %d     | 지정한 자료를 부호 있는 10진 정수로 변환 | 정수형, 문자형 |
| %u     | 지정한 자료를 부호 없는 10진 정수로 변환 | 정수형, 문자형 |
| %f     | 지정한 자료를 부동소수점형식으로 변환   | 실수형      |
| %e, %E | 지정한 자료를 지수형태로 변환       | 실수형      |
| %c     | 지정한 자료를 하나의 문자로 변환     | 정수형, 문자형 |
| %s     | 지정한 자료를 문자열로 변환        | 문자열 포인터  |
| %o     | 지정한 자료를 부호 없는 8진 정수로 변환 | 정수형, 문자형 |
| %x,%X  | 지정한 자료를 부호 없는 16진 정수로 변환 | 정수형, 문자형 |

```c
#include <stdio.h>
void main()
{
    printf("%c\n", 'A'); // A
    printf("%d\n", -123); //123
    printf("%o\n", 123); // 173
    printf("%x\n", 123); // 7b
    printf("%X\n", 123); // 7B
    printf("%f\n", 123.456789); // 123.456789
    printf("%e\n", 123.456789); // 1.234568e+02
    printf("%s\n", "Hello, World!"); // Hello, World!
}

```

- 출력 양식의 편집

```c
#include <stdio.h>
void main() {
    printf("|%d|\n", 123); // |123|, 숫자 길이만큼 출력 폭이 자동 지정됨
    printf("|%5d|\n", 123); // |  123|, 출력 폭을 5로 지정
    printf("|%-5d|\n", 123); // |123  |, 출력 폭을 5로 지정하고 왼쪽 정렬
    printf("|%05d|\n", 123); // |00123|, 출력 폭을 5로 지정하고 빈자리를 0으로 채움
    printf("|%6.1f|\n", 123.45); // | 123.5|, 전체 6자리 중 소수점 1자리까지 출력
    printf("|%07.2f|\n", 123.45); // |0123.45|, 전체 7자리 중 소수점 2자리까지 출력
}
```

#### scanf()

- 형식: `scanf("입력양식", &변수1, &변수2, ...);`
- 기능: 주어진 입력양식으로 자료를 입력받는다
- scanf("%d", &num); // 정수형 자료를 입력받아 num에 저장

- 입력양식 변환기호

| %문자 | 변환 기능       |
|-----|-------------|
| %d  | 정수형 입력      |
| %ld | long 정수형 입력 |
| %f  | 실수형 입력      |
| %lf | double 실수형 입력 |
| %c  | 문자형 입력      |
| %s  | 문자열 입력      |

```c
#include <stdio.h>
void main()
{
    int num;
    printf("정수를 입력하세요: ");
    scanf("%d", &num);
    printf("입력한 정수는 %d입니다.\n", num);
}
```

#### getchar()

- 형식: `getchar();`
- 기능: 키보드로부터 1개의 문자를 입력받는다
- a=getchar(); // 키보드로부터 1개의 문자를 입력받아 a에 저장

```c
#include <stdio.h>
void main()
{
    char ch;
    printf("문자를 입력하세요: ");
    ch = getchar();
    printf("입력한 문자는 %c입니다.\n", ch);
}
```

#### putchar()

- 형식: `putchar(문자);`
- 기능: 화면에 1개의 문자를 출력한다
- putchar('A'); // A를 화면에 출력

```c
#include <stdio.h>
void main()
{
    char ch = 'A';
    putchar(ch); // A
    purchar(ch+1); // B
    putchar('\n'); // 개행
    putchar('K'); // K
    putchar('K'+2); // M
    putchar('\007'); // 소리 출력
}
```

#### gets()

- 형식: `gets(변수);`
- 기능: 키보드로부터 문자열을 입력받는다
- gets(str); // 키보드로부터 문자열을 입력받아 str에 저장

```c
#include <stdio.h>
void main()
{
    char str[100];
    printf("문자열을 입력하세요: ");
    gets(str);
    printf("입력한 문자열은 %s입니다.\n", str);
}
```

#### puts()

- 형식: `puts("문자열");`
- 기능: 화면에 문자열을 출력한다
- puts("Hello, World!"); // Hello, World!를 화면에 출력

```c
#include <stdio.h>
void main()
{
    char str[] = "Hello, World!"; 
    puts(str); // Hello, World! - 자동 개행
    printf("%s", str); // Hello, World!
}
```