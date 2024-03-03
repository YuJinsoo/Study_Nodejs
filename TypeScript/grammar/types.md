# Typescript의 타입

## 숫자(number, Number)

## 문자열(string, String)

- `string`, `String`

### 메서드

#### length
- 프로퍼티(속성)임. 메서드는 아니지만 길이를 반환해줌.
```ts
let str:string = 'test_string';
console.log(str.length); //11
```


#### replace()
- 문자열 대체하기

```ts
let str:string = 'test_string';
let new_str:string = str.replace('_', ':');
console.log(new_str);  // test:string
```

#### split()
- 문자열 분리하기
- 구분자로 분리하여 자르는 메서드

```ts
let str:string = 'test_string';
let parts:string[] = str.split('_');
console.log('parts[0]', parts[0]); // "parts[0]",  "test" 
console.log('parts[1]', parts[1]); // "parts[1]",  "string"
```

#### concat()
- 문자열 합치기
- `+` 연산을 사용하는 것과 같은 기능
```ts
let str:string = 'test_string';
let concat_string:string = str.concat('_concat');
console.log(concat_string) //"test_string_concat" 
```

#### trim()
- `string.trim()` 하면 양쪽 공백 문자열을 제거해줍니다.
    - 모두 공백 문자열일 경우 ''를 리턴합니다.

```ts
let str1: string = '  left2space';
let str2: string = 'right2space  ';
let str3: string = '  both2space ';
let str4: string = 'inner  2space';

console.log('str1.trim(): ',str1.trim());
console.log('str2.trim(): ',str2.trim());
console.log('str3.trim(): ',str3.trim());
console.log('str4.trim(): ',str4.trim());

// str1.trim():  left2space
// str2.trim():  right2space
// str3.trim():  both2space
// str4.trim():  inner  2space
```

#### toLowerCase(), toUppserCase()
- 문자열의 모든 문자를 소문자(`toLowerCase()`) 혹은 대문자(`toUpperCase()`)로 된 새로운 문자열을 반환합니다.

```ts
let str:string = 'Hello, I love Typescript!'
let upper:string = str.toUpperCase();
let lower:string = str.toLowerCase();

console.log('str: ', str);
console.log('upper: ', upper);
console.log('lower: ', lower);
// str:  Hello, I love Typescript!
// upper:  HELLO, I LOVE TYPESCRIPT!
// lower:  hello, i love typescript!
```

#### IndexOf(), lastIndexOf()

- `IndexOf()` 는 문자열에서 지정된 값이 처음 나타나는 인덱스를 반환합니다.
- `lastIndexOf()` 는 문자열에서 지정된 값이 마지막으로 나타나는 인덱스를 반환합니다.(뒤에서 처음)
- 두 함수 모두 문자열에 없는 값을 지정하면 -1(number) 를 반환합니다.

```ts
let str:string = 'Hello world!';

console.log(str);                   // Hello world!
console.log(str.indexOf('o'));      // 4
console.log(str.lastIndexOf('o'));  // 7
console.log(str.indexOf('t'));      // -1
console.log(str.lastIndexOf('t'));  // -1    
```

#### substring(), slice()
- 하위 문자열 및 슬라이스 하는 메서드입니다.
- 문자열의 지정된 부분을 포함하는 새 문자열을 반환합니다.
- `slice()` 메서드는 문자열의 지정된 부분을 포함하는 새 문자열을 반환하지만 음수 값이 문자열 끝에서 위치를 나타낼 수 있습니다.
    - `substring()`은 음수 인덱스 전달시 아무 문자열이 안나옴.
- 인자는 (시작 index, 끝 index) 입니다.
    - 시작 인덱스만 준 경우는 문자열의 끝까지 범위를 반환합니다.

```ts
let message: string = 'Hello world!!';

let sub1: string = message.substring(0,5);
let sub2: string = message.substring(2);
let sub3: string = message.substring(-8, -6);
let slice: string = message.slice(-6,-1);
let slice2: string = message.slice(-6);

console.log('message: ', message);  // message:  Hello world!!
console.log('sub1: ', sub1);        // sub1:  Hello
console.log('sub2: ', sub2);        // sub2:  llo world!!
console.log('sub2: ', sub2);        // sub2:  llo world!!
console.log('sub3: ', sub3);        // sub3:
console.log('slice: ', slice);      // slice:  orld!
console.log('slice2: ', slice2);    // slice2:  orld!!
```

string.substring()
string.repeat()
string.indexOf()
string.lastIndexOf()
string.charAt( index) > 인덱스 위치의 문자 1개 반환

공부해보기.
- 


## Array

### 메서드

### 언패킹



## Object

### 메서드

### 비교연산

- 오브젝트 비교
- 내용물이 완벽히 같아도 객체가 다르면 다른 오브젝트로 판단함.
```ts
let a = {
    "num": 1 
    }

let b = {
    "num": 1 
    }

if (a === b) { console.log('bnb')} // undefined
if (a !== b) { console.log('bnb')} // 'bnb'
```


### 언패킹 하는 법

- 오브젝트의 key에 해당하는 value를 모두 한번에 꺼내고 싶을 때 언패킹을 사용
- 오브젝트의 key와 동일한 이름으로 할당을 해주어야 합니다.

``` ts
type T_packet = {
    tn_type: number;
    tn_seq: number;
    bt_data: Uint8Array;
}

let temp_a: T_packet = {
    tn_type: 0,
    tn_seq: 0,
    bt_data: new Uint8Array(10)
}

temp_a.bt_data[0] = 1
temp_a.bt_data[1] = 2
temp_a.bt_data[2] = 3
temp_a.bt_data[3] = 4
temp_a.bt_data[4] = 5
temp_a.bt_data[5] = 5
temp_a.bt_data[6] = 5
temp_a.bt_data[7] = 5
temp_a.bt_data[8] = 5
temp_a.bt_data[9] = 5

function unpack_packet_data(_packet: T_packet): { tn_type: number, tn_seq: number, bt_data: Uint8Array } {
    // 바로 언패킹 가능
    let {tn_type, tn_seq, bt_data} = _packet 
    console.log(`tn_type: ${tn_type}, tn_seq: ${tn_seq}, bt_data: ${bt_data}`) 
  
  // 함수 리턴으로 하는 경우
    return {
        tn_type: _packet.tn_type,
        tn_seq: _packet.tn_seq,
        bt_data: _packet.bt_data
    };
}

// 함수 리턴으로 하는 경우
const {tn_type, tn_seq, bt_data} = unpack_packet_data(temp_a); 
console.log(`tn_type: ${tn_type}, tn_seq: ${tn_seq}, bt_data: ${bt_data}`)
```


