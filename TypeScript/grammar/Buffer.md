
## Typescript의 Buffer

- 바이너리 데이터를 다루는 데 사용되는 클래스
- 주로 파일 시스템, 네트워크 통신, 데이터 스트림 처리 등과 같은 I/O 작업에서 사용

- Buffer.from() 은 주어진 데이터를 버퍼로 변환
    - 첫번째 인자: 변환할 변수
    - 두번째 인자: 인코딩 지정(생략시 'utf8')
      - 'utf8', 'hex', 'base64' 등이 있음

- 빈 버퍼 생성

```ts
Buffer.alloc(10); // 10바이트 크기의 빈 버퍼 생성
```

```ts
// 예제 바이너리 데이터
const buffer = Buffer.from([72, 101, 108, 108, 111]);

// Buffer를 'utf-8' 문자열로 변환 (인코딩 타입 생략 가능)
const str = buffer.toString('utf-8'); // 'Hello'
console.log(str); // 출력: Hello


// 바이너리 데이터를 'hex' 문자열로 변환
const hexStr = buffer.toString('hex');
console.log(hexStr); // 예: "48656c6c6f" (Hello의 hex 표현)
```

- 주의할점
  - 버퍼의 크기를 동적으로 조절할 수 없음
    (하지만 추가로 늘리는 `Buffer.concat()`함수가 있음)
  - 직접 메모리에 접근하여 수정할 수 있어서 보안 취약점이 될 수 있습니다
  - 최신 JavaScript에서는 `TypedArray와` `DataView를` 사용하여 이러한 문제를 해결
    - `Uint8Array`같은게 `typedArray`

#### Buffer를 이용한 변환 예제
- 문자열과 같은 데이터를 Buffer로 변환(인코딩 지정) 하여 2진 데이터로 만듦
- 이후
  - 문자열 변환이면
    ```ts
    const buffer = Buffer.from(uint8Array);
    const str_buf = buffer.toString('utf8');
    ```
  
  - uint8Array이면
    ```ts
    const buffer = Buffer.from(uint8Array);
    const uint_buf = new Uint8Array(buffer);
    ```
  
  - json 이면 문자열로 변환 후 JSON으로 변환
    ```ts
    const buffer = Buffer.from(uint8Array);
    const json_str_buf = buffer.toString('utf8');
    cosnt josn_object = JSON.parse(json_str_buf);
    ```


## Uint8Array

- Uint8Array??
- `nodejs`에서 제공하는 `TypedArray`
- `TypedArray`는 버퍼를 다루는 객체로, 고정된 길이의 이진 데이터를 나타냅니다

- array.filter
콜백에 true인 것만 추가

### 타입가드

