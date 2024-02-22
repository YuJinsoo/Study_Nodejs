# Typescript의 타입

## 숫자(number, Number)

## 문자열(string, String)

- `string`, `String`

### 메서드

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


