
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

## Uint8Array

- Uint8Array??
- `nodejs`에서 제공하는 `TypedArray`
- `TypedArray`는 버퍼를 다루는 객체로, 고정된 길이의 이진 데이터를 나타냅니다


- 오브젝트 비교
> let a = {
... "num": 1 }
undefined
> let b = {
... "num": 1 }
undefined
> if (a === b) { console.log('bnb')}
undefined
> if (a !== b) { console.log('bnb')}
bnb



- array.filter
콜백에 true인 것만 추가

### 타입가드



## 웹소켓

- 무엇인가?
 
전송 프로토콜의 일종으로 쉽게 말하면 웹 버전의 TCP 또는 Socket
서버와 클라이언트 간에 소켓 연결을 유지해서 언제든지 양방향 통신 또는 데이터 전송이 가능하게 하도록 하는 기술이다. 

SNS, 멀티플레이어 게임, 구글Docs, 증권거래, 화상채팅

한줄요약
>> 웹 기반으로 양방향 통신이 가능한 전송 프로토콜입니다. 주로 

- 왜 사용하는가?

HTTP는 request/response 기반의 stateless한 프로토콜
즉, 서버와 클라이언트가 지속적으로 연결되지 않고, 클라이언트에서 필요할때 request - 서버는그에 response 구조
즉, 서버측 데이터가 업데이트 되어도 클라이언트가 요청하지 않으면 서버의 변경 상태를 모름
log polling이나 ajax를 사용해도 어느정도 해결가능
데이터의 빠른 업데이트가 아주 중요한 요소인 어플리케이션에서는 web socket이 필수.

웹소켓은 stateful protocol이기 때문에 클라이언트와 서버가 한번 연결이 되면
계속 같은 라인을 사용해서 통신하기 때문에 HTTP 사용시 필요없이 발생되는 HTTP와 TCP연결 트래픽을 피할 수 있다.


- 원리

웹소켓 연결은 HTTP프로토콜을 통해 이루어진다.
연결이 정상적으로 이루어진다면 서버와 클라이언트 간에 웹소켓 연결이 이루어지고
일정 시간이 지나면 HTTP 연결이 자동으로 끊어진다.

웹소켓 프로토콜은 접속을 하는데 HTTP를 사용하지만, 이후의 통신은 웹소켓의 독자적인 프로토콜로 이루어진다.
또한 header가 작아서 overhead가 적은 특징이 있다.



## 웹소켓 플젝

C_Ws_client
메서드

init_peer(_ws: WebSocket, _cb_recv: (_c_client: C_Ws_client, _t_packet: T_Packet) => void): void;
init_client(_s_connect_url: string, _cb_recv: (_c_client: C_Ws_client, _t_packet: T_Packet) => void): void;
  - 최초 웹소켓 연결 시
  
init_auto_reconnect(_n_msec_interval_reconnect: number): void;
  - 자동재접속 횟수 초기화?
  
sock_onmessage(_ev: MessageEvent<any>): Promise<void>;
  - 접속한 소켓에 메시지왔을떄?

send_n_recv(_bt_data: Uint8Array, _cb: (_c_client: C_Ws_client, _t_packet: T_Packet) => void): void;
send_call(_bt_data: Uint8Array): number;
send_back(_bt_data: Uint8Array): number;
send(_td_packet_type: TdPacketType, _bt_data: Uint8Array): number;
recv(): T_Packet | undefined;
is_same_socket(_ws: WebSocket): boolean;
is_open(): boolean;


_cb_connect
_cb_close
_cb_read