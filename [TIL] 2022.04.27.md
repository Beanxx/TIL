[TIL] Day2 <br/>
[SEB FE] Day3

## 1️⃣ 조건문
>어떠한 조건을 판별하는 기준을 만드는 것으로 `비교연산자`가 필요!

```jsx
if (조건A) {
	return ~
} else if (조건B) {
	return ~
} else {
	return ~
}
```

<br/>

### 📎 비교연산자

| 연산자 | 의미 |
| :---: | :---: |
| > | 초과 |
| < | 미만 |
| >= | 이상 |
| <= | 이하 |
| === | 같다 |
| !== | 다르다 |

✋ ==, != 사용 지양 (why? 엄격히 타입 비교 X)

<br/>

### 📎 논리 연산자
> 두가지 조건을 한번에 적용하는 경우 사용

1. `AND`

  | 연산 | 결과 |
  | :---: | :---: |
  | true && true | true |
  | true && false | false |
  | false && false | false |

  ✋ AND 연산자는 falsy한 값을 만나면, 그 값 출력
  
  | 연산 | 결과 |
  | :---: | :---: |
  | undefined && 10 | undefined |
  | 5 && false | false |

  ✋ 둘다 truthy할 경우, 뒤에 있는 값 출력

  | 연산 | 결과 |
  | :---: | :---: |
  | 5 && 10 | 10 |

<br/>

2. `OR`

  | 연산 | 결과 |
  | :---: | :---: |
  | true \|\| true | true |
  | true \|\| false | true |
  | false \|\| false | false |

  ✋ OR 연산자는 truthy한 값을 만나면, 그 값 출력 (그 이후는 평가 x)

  | 연산 | 결과 | 이유 |
  | :---: | :---: | :---: |
  | undefined \|\| 10 | 10 | undefined이 false 취급이므로 10 출력 |
  | 5 \|\| 10 | 5 | 앞에서 부터 평가하기 때문에 5 출력 |

  ✋ 둘 다 falsy할 경우, 뒤에 있는 값 출력

  | 연산 | 결과 |
  | :---: | :---: |
  | undefined \|\| false | false |

<br/>  

3. `NOT`

  | 연산 | 결과 |
  | :---: | :---: |
  | !false | true |
  | !(3>2) | false |
  | !undefined | true |
  | !’Hello’ | false |
  
<br/>

✋ undefined: false 취급(falsy)

✋ ‘abc’ 비어 있지 않은 문자열: true 취급(truthy))

<br/>

### 📎 falsy 값
>(if문에서 false로 변환되므로, if 구문 실행 X)

1. `if(false)`
2. `if(null)`
3. `if(undefined)`
4. `if(0)`
5. `if(NaN)`
6. `if(’ ‘)`

<br/>
<hr/>

## 2️⃣ 문자열

- `str[index]` : index에 해당하는 문자 출력 (read-only)
    
    ```jsx
    str1 = 'Code';
    str2 = 5;
    str3 = 'Happy';
    
    console.log(str1 + str2 + str3) // Code5Happy
    // = str1.concat(str2, str3 ...)
    ```
    
    👉🏻 `toString`: string 타입과 다른 타입 사이에 + 연산자를 쓰면, string 형식으로 변환
    <br/>

- `str.length`: 문자열 str의 전체 길이 return

<br/>

- `str.indexOf(searchValue)`: 찾고자 하는 문자열이 위치하는 index return
    
    ```jsx
    // 처음으로 일치하는 index return
    // 공백도 하나의 index를 가진다고 생각하기!
    'Hard Coding Coding'.indexOf('Hard'); // 6
    
    // 찾고자 하는 문자열이 없으면 -1 return
    'Hard Coding'.indexOf('hard'); // -1
    
    // lastIndexOf: 문자열 뒤부터 찾기
    'apple'.lastIndexOf('p'); // 2
    
    ```
    
    - `str.includes(searchValue)`: 찾고자 하는 문자열이 포함되어 있는지 판별 (`true` / `false`)
    <br/>
- `str.split(seperator)`: seperator 문자를 기준으로 문자열을 쪼갬 (csv 형식 처리시 유용)
    
    ```jsx
    A.
    var str = 'Nice to meet you';
    str.split(' ');
    // str.split('\n') => 줄단위로 문자열을 쪼갬
    
    // ['Nice', 'to', 'meet', 'you']
    
    B.
    let alphabet = 'abcedf';
    alphabet.split('');
    
    // ['a', 'b', 'c', 'e', 'd', 'f']
    
    ```
    <br/>

- `str.substring(start index, end index)`: 시작과 끝 index 사이의 문자열 retrun
    
    cf. = `str.slice(start, end)`
    
    ```jsx
    var str = 'abcdefg';
    str.substring(0,3); // 'abc'
    // index가 0~3이 아니라 0~2인 문자를 return함을 주의!
    // parameter가 (end index, start index)처럼 순서가 바뀌어도 OK
    // parameter가 음수일 경우 0으로 취급
    
    ```
    <br/>
- `str.toLowerCase()`: 소문자로 변환
- `str.toUpperCase()`: 대문자로 변환
    
    👉🏻 str 문자열 자체가 변환되는 것은 아님 (Immutable)
    
<br/>

### 📎 템플릿 리터럴(Template literals)

>문자열을 + 연산자를 사용하지 않고 편리하게 여러 타입의 문자열 혼합 가능
>>👉🏻 ``지금은 ${hour}시 ${minute}분 ${second}초 입니다.``

<br/>
<hr/>

## ➕ etc
> 연습 문제 풀다가 기억해야 할 기타 개념들
>>
- 짝수 구하는 조건: `num % 2 === 0`    (`%`: 나머지 구하는 연산자)
- 제곱근 구하는 방법
    1. `a * a`
    2. `a ** 2`
    3. `Math.pow(a, 2)`
- 내림 연산: `Math.floor()`
- 최소값: `Math.min(num1, num2 ...)`
- 최대값: `Math.max(num1, num2 ...)`
- 절대값 연산: `Math.abs(num1 - num2)`

<br/>
<hr/>

## ➕ Advanced

### 📎 substr() & substring() & slice() 차이

- `str.substr(start index, length)`: start index부터 length 길이만큼 잘라내어 return
    
    
    |  | substring(start, end) | slice(start, end) |
    | :---: | :---: | :---: |
    | start > end일 경우 | start, end 서로 바꿔서 처리 | 빈 문자열 return |
    | index가 음수일 경우 | index를 0으로 취급 | 문자열 맨 끝에서 음수의 절대값만큼 내려온 index로 취급 |
    
    ```jsx
    let str = Carpediem
    str.slice(-3, 9)
    // 맨뒤의 'm'을 -1 기준으로, index -3는 'i'
    // 즉, str.slice(-3, 9) === str.splice(6, 9)
    
    // 'iem'
    ```
