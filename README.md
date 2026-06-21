# Java, only for Coding Tests

## 목차
- [🧰 코테 준비물](#-코테-준비물)
- [☕ Java 문법](#-java-문법)
- [🧩 알고리즘](#-알고리즘)
- [📐 수학](#-수학)


### 코테 준비물

| 개념 | 기억포인트 | 링크 |
|---|---|---|
| import 기본 세트 | * `java.util.*`, `java.io.*` 코테 시작 전 무조건 추가 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/1) |
| Scanner vs BufferedReader | * 코테는 BufferedReader 권장<br/>　- Scanner보다 빠름, 시간초과 시 의심 1순위<br/>* `br.readLine()`+`StringTokenizer`로 토큰 분리<br/>　- 토큰은 한 번 꺼내면 재사용 불가<br/>* 끝에 공백 있을 수 있으니 `readLine().trim()` 습관화 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/15) |
| throws Exception | * main에 붙여 예외처리 JVM에 위임<br/>　- 코테에선 try-catch 대신 간단히 사용<br/>* `BufferedReader.readLine()`은 `IOException` 발생 가능<br/>　→ 안 붙이면 "Unhandled exception type" 컴파일 에러 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/17) |
| StringBuilder | * 문자열 `+`는 매번 새 문자열 생성(느림)<br/>　- StringBuilder는 버퍼에 누적(O(1) 수준)<br/>* `append()`는 메서드 체이닝 가능<br/>　- `.append(a).append(b)` 식으로 연결<br/>* 큰 루프에서 문자열 누적할 때 거의 필수, 안 쓰면 시간초과 위험 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/19) |
| 배열 출력 디버깅 | * 1차원: `Arrays.toString(arr)` → [1, 2, 3]<br/>* 2차원:<br/>　- `for(row) println(Arrays.toString(row))`<br/>　- 또는 `Arrays.deepToString(map)` 한 줄로<br/>* 제출 전 꼭 삭제! | [정리](https://github.com/SeoMiYoung/just-do-it/issues/23) |

⬆ [목차로 돌아가기](#목차)


### Java 문법

| 개념 | 기억포인트 | 링크 |
|---|---|---|
| 최대/최소 구하기 | * `Math.max(a,b)`/`min(a,b)`로 2개 비교<br/>* 배열 초기화<br/>　- 그냥 순회: `arr[0]`<br/>　- 탐색(누적): `MIN/MAX_VALUE` | [정리](https://github.com/SeoMiYoung/just-do-it/issues/2) |
| Integer.parseInt() | * 문자열→int 변환<br/>* 공백 있으면 예외 → `trim()` 먼저 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/3) |
| split() | * 문자열을 구분자로 잘라 `String[]` 반환<br/>* 끝 공백 보존하려면 `split(" ", -1)` | [정리](https://github.com/SeoMiYoung/just-do-it/issues/4) |
| println/printf/String.format | * `println`<br/>　- 자동줄바꿈, 포맷 불가<br/>* `printf`<br/>　- 포맷팅+즉시출력, 줄바꿈은 `\n` 직접<br/>* `String.format`<br/>　- 문자열로 반환만, 출력은 안 함 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/5) |
| toUpperCase/toLowerCase | * char: `Character.toUpperCase()`<br/>* String: `s.toUpperCase()`<br/>* 알파벳만 영향, 숫자·공백은 그대로 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/6) |
| charAt() | * 인덱스로 문자 하나 꺼냄(0부터 시작)<br/>　- 빈 문자열에 호출 시 에러 주의<br/>* 숫자문자열: `line.charAt(j) - '0'`로 char→int 변환<br/>* 공백구분: `StringTokenizer`로 토큰 뽑은 후 `.charAt(0)` | [정리](https://github.com/SeoMiYoung/just-do-it/issues/7) |
| length vs length() vs size() | * 배열: `.length`(속성, 괄호X)<br/>　- 선언 크기 그대로, 실제 데이터 개수 아님<br/>* 문자열: `.length()`(메서드) — 실제 길이 반환<br/>* 리스트: `.size()` — 실제 담긴 개수, null 걱정 없음 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/8) |
| isEmpty() | * 문자열 길이 0인지 검사(`length()==0`과 동일)<br/>　- `true`/`false` 반환<br/>* split() 결과 빈 문자열에 `charAt(0)` 호출 시 에러 방지용으로 자주 씀<br/>* `null`과는 다른 개념 — null에 호출하면 `NullPointerException` | [정리](https://github.com/SeoMiYoung/just-do-it/issues/9) |
| substring() | * `substring(i)`: i부터 끝까지<br/>* `substring(i,j)`: i이상 ~ j미만(끝 미포함)<br/>* `charAt(0)`+`substring(1)` 조합<br/>　- "첫 글자만 다르게 처리" 패턴 (JadenCase 등) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/10) |
| String.join() | * `join(구분자, 배열/List)`로 합치기<br/>　- 빈 문자열("")도 자리 그대로 살림<br/>* `split`으로 나눈 걸 다시 `join`하면 원래 공백 구조 복원<br/>　→ 둘은 짝 메서드 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/11) |
| char+char vs char+String | * char는 사실 정수(유니코드 코드값)<br/>　- char+char는 숫자 더하기(int로 승격)<br/>* String이 하나라도 섞이면 전체가 문자열 결합으로 바뀜<br/>* 혼합 연산은 왼쪽부터 순서대로 계산<br/>　→ String 등장 시점부터 결합 시작 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/12) |
| Deque | * 스택(LIFO)·큐(FIFO) 둘 다 구현 가능<br/>　- 삽입 속도가 ArrayList보다 빠름<br/>* `add/remove/get`은 예외 발생<br/>　- `offer/poll/peek`은 false/null 반환 → 코테엔 후자 추천<br/>* 스택처럼: `push/pop/peek` (=addFirst/removeFirst/peekFirst)<br/>* 큐처럼: `offer/poll/peek` (=addLast/pollFirst/peekFirst) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/13) |
| String 순회 방법 | * String은 Iterable 미구현<br/>　- `for(char c : s)` 안 됨<br/>* 인덱스 불필요: `toCharArray()`+for-each (가장 간결)<br/>* 인덱스 필요(앞뒤 비교 등): `charAt(i)`+일반 for문 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/14) |
| StringTokenizer vs split() | * 구분자<br/>　- ST: 단일문자/문자열만<br/>　- split: 정규식 가능(여러 구분자 동시)<br/>* 빈문자열<br/>　- ST: 무시함<br/>　- split: 남김 ("A,,B" → ST는 2토큰, split은 빈칸 포함)<br/>* 속도는 ST가 더 빠름(정규식 파싱 없음) → 코테는 보통 ST가 더 흔함<br/>* 접근 방식: ST는 순차 접근만, split은 배열이라 인덱싱 가능 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/16) |
| int vs long | * 값이 10^9 넘으면 int 오버플로우 위험 → long 사용<br/>* 연산 전에 캐스팅해야 함<br/>　- `(long) a * b` (O)<br/>　- 곱한 후 캐스팅은 이미 망가진 값 (X)<br/>* long 리터럴엔 끝에 `L` 필수<br/>　- `12345678900L`, 안 붙이면 int 범위로 인식돼 에러 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/18) |
| 나눗셈/나머지(/,%) | * `int/int`는 소수점 버리고 정수만 반환<br/>　- 7/2 → 3, 3.5 아님<br/>* 소수점 원하면 피연산자 하나만 `(double)`로 캐스팅<br/>　- `(double)7/2` 또는 `7/(double)2`<br/>* `%`는 나머지를 정수로 반환 (7%2 → 1) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/20) |
| Math.ceil/floor/round | * 반환 타입<br/>　- `ceil`: 올림, double 반환<br/>　- `floor`: 내림, double 반환<br/>　- `round`: 반올림, long 반환(float 인자는 int)<br/>* 음수 주의<br/>　- `ceil(-3.1)` = -3.0 (큰 쪽)<br/>　- `floor(-3.1)` = -4.0 (작은 쪽)<br/>　- `round(-3.5)` = -3 (0.5는 위로 반올림)<br/>* 자리수 맞춰 출력하려면 `String.format("%.2f", ...)` | [정리](https://github.com/SeoMiYoung/just-do-it/issues/21) |
| ArrayList | * 크기 가변 배열<br/>　- 핵심 메서드: `add/get/set/remove/size/isEmpty`<br/>* `==`는 참조 비교(false)<br/>　- `equals()`는 요소+순서 비교 → 동등 비교는 꼭 `equals()`<br/>* 순서 무관 비교는 `new HashSet<>(list)` 변환 후 `equals()` | [정리](https://github.com/SeoMiYoung/just-do-it/issues/22) |
| Arrays.fill() | * `Arrays.fill(배열, 값)`로 모든 요소를 한 값으로 채움<br/>* for문으로 직접 채우는 것과 동일, 코드만 한 줄로 단축 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/24) |
| char-인덱스 변환 | * 문자→숫자: `ch - 'A'`<br/>　- 둘 다 int로 승격, 'A'=65 기준 오프셋<br/>* 숫자→문자: `(char)(idx + 'A')`<br/>　- 더하기 먼저 하고 캐스팅해야 함, 안 그러면 int로 남음 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/25) |
| == vs equals() | * 기본타입(int, char 등): `==`로 값 비교<br/>* 참조타입(String, 객체): `==`가 메모리주소 비교<br/>* String 내용 비교는 무조건 `equals()`<br/>　- `new String()`은 같은 내용도 `==`는 false<br/>* 사용자 정의 클래스는 `equals()` 직접 오버라이드 필요<br/>　- `hashCode()`도 같이 오버라이드 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/26) |
| String.contains() | * 부분 문자열 포함 여부 `boolean` 반환, 대소문자 구분함<br/>* char는 직접 안 됨<br/>　- `String.valueOf(ch)`로 변환 필요, null 넣으면 NPE<br/>* 대소문자 무시하려면 `toLowerCase()/toUpperCase()` 먼저 처리 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/27) |
| Arrays.sort/Collections.sort | * `int[]`는 reverseOrder 못 씀<br/>　→ 오름차순 후 뒤에서부터 읽기(또는 양끝 swap)<br/>* 람다 정렬 공식<br/>　- 오름차순: `o1-o2`<br/>　- 내림차순: `o2-o1`<br/>　- 다중조건: 같으면 다음 조건으로 흘려보내기<br/>　- String: `compareTo()` 사용<br/>* 뺄셈은 오버플로우 위험(21억↑)<br/>　→ `Integer.compare()` / `Double.compare()` 권장<br/>* `sort()`는 원본 직접 수정(void 반환)<br/>　- 1차원: `clone()`으로 복사<br/>　- 2차원: clone은 얕은복사라 위험 → for문으로 deep copy<br/>* ArrayList는 `Collections.sort(list,...)` 또는 `list.sort(...)`<br/>　→ 문법은 배열과 동일 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/28) |
| Math.pow() | * `Math.pow(a,b)` = a의 b제곱, 반환형은 항상 double<br/>* int/long 넣으면 자동으로 double로 승격(widening)<br/>* int로 받고 싶으면 캐스팅<br/>　- 단순 캐스팅은 정밀도/범위 문제 위험<br/>　- 범위 초과 시 클램핑됨(MAX/MIN_VALUE로), NaN은 0 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/29) |
| 배열 리터럴 `{}` | * `int[] arr = {1,2}`처럼 선언과 동시에만 축약 리터럴 가능<br/>* 메서드 인자 등 선언이 아닌 곳에서 쓰려면 `new int[]{...}` 필수<br/>　- `list.add({y,x})` (X) → `list.add(new int[]{y,x})` (O) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/30) |
| 얕은 복사 vs 깊은 복사 | * 변수엔 실제값이 아니라 참조(주소)만 담김 <br/>　→ `copy = original`은 같은 거 가리킴<br/>* 1차원 배열은 `clone()`으로 충분<br/>* 2차원 배열·객체 배열은 `clone()`해도 안쪽이 공유됨(얕은 복사)<br/>　→ 2차원: for문으로 각 행 `clone()`<br/>　→ 객체 배열: `new 객체(...)`로 새로 생성 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/31) |
| Math.abs() | * 절댓값 반환, 음수든 양수든 항상 양수로<br/>* 두 값의 차이(거리) 구할 때 자주 씀 → `Math.abs(a-b)` | [정리](https://github.com/SeoMiYoung/just-do-it/issues/32) |
| Math.sqrt() | * 제곱근 반환(항상 double, 양수만)<br/>* 제곱수 판별 패턴: `(long)Math.sqrt(n)` 구한 뒤 `r*r==n`으로 검증<br/>　- 단순 캐스팅(버림)이라 오차 가능성 있어 꼭 역검증 필요 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/33) |
| String.valueOf() | * 기본타입(int,char 등)→문자열, 객체는 내부적으로 `toString()` 호출<br/>* `null` 안전: `valueOf(null)`은 "null" 문자열 반환, 예외 없음<br/>　- 반면 `obj.toString()`은 obj가 null이면 NPE 발생 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/34) |
| HashSet | * 중복 불허, 순서 보장 안 함, add/contains/remove 다 O(1)<br/>* 핵심 메서드: `add/remove/contains/size/isEmpty/clear/iterator()`<br/>* `add()`는 중복 시도하면 `false` 반환(에러 아님)<br/>* `equals()`는 순서 무관하게 요소만 같으면 true (ArrayList와 다른 점!) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/35) |
| PriorityQueue | * 힙 기반, 기본은 최소힙(작은 값 먼저)<br/>* 최대힙 원하면 `new PriorityQueue<>(Collections.reverseOrder())`<br/>* 객체 우선순위 정하는 법<br/>　- `Comparable` 구현 (compareTo 오버라이드)<br/>　- 또는 생성자에 `Comparator` 직접 넘기기<br/>* `add`는 실패시 예외, `offer`는 false 반환(Deque와 동일 패턴) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/37) |
| Integer.bitCount() | * n을 2진수로 봤을 때 1의 개수 카운트 (`bitCount(7)`→3)<br/>* 활용 패턴<br/>　- 1의 개수 같은지 비교: `bitCount(a)==bitCount(b)`<br/>　- 부분집합 탐색: `bitCount(mask)==k`로 k개 선택된 경우 필터<br/>　- 2의 거듭제곱 판별: `bitCount(n)==1`<br/>* 확인용으로 `Integer.toBinaryString(n)`과 같이 쓰면 좋음 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/40) |
| String.replace() | * 문자열 그대로 찾아서 교체(정규식 아님)<br/>* 빈문자열("")로 바꾸면 제거 효과<br/>* 원본 불변 → 반드시 `s = s.replace(...)`로 재할당해야 적용됨<br/>* 활용: 제거 전후 `length()` 차이로 제거된 개수 계산 가능 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/41) |
| 2차원 배열 초기화<br/>(원시 vs 참조타입) | * 원시타입(int 등): 선언만으로 기본값 자동 초기화, 바로 사용 가능<br/>* 참조타입(String, Set 등): 선언 직후 전부 `null` <br/>　→ 각 칸에 `new` 직접 해줘야 함<br/>　- 안 하고 쓰면 NullPointerException<br/>* Set/List 같은 제네릭은 `new Set<T>[N][N]` 자체가 컴파일 에러<br/>　→ `new HashSet[N][N]`처럼 Raw Type으로 생성(경고만 뜸, 비대칭 선언) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/42) |
| if-else if-else | * else는 선택사항, 안 써도 문법적으로 문제없음<br/>* 모든 조건이 false면 그냥 아무것도 실행 안 하고 넘어감 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/43) |
| toString() | * `println(객체)`는 내부적으로 `객체.toString()` 자동 호출<br/>* 오버라이드 안 하면 `클래스명@해시값` 형태로 출력됨 (의미없는 값)<br/>* 커스텀 클래스 만들 때<br/>　→ `@Override toString()` 정의하면 원하는 형태로 출력 가능<br/>* List/배열도 내부 요소마다 toString() 호출해서 출력 (`[(1,2), (3,4)]`) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/44) |



⬆ [목차로 돌아가기](#목차)


### 알고리즘

| 개념 | 기억포인트 | 링크 |
|---|---|---|
| 다익스트라 vs 플로이드워셜 | * 다익스트라: 단일 출발점→모든 정점, O((V+E)logV), 음수 가중치 불가<br/>* 플로이드워셜: 모든 정점 쌍, O(V³), 음수 가중치 허용(음의 사이클은 불가)<br/>* 선택 기준<br/>　- 정점 많고 간선 적음 + 출발점 하나 → 다익스트라<br/>　- 정점 적음(≤100) + 모든 쌍 필요 → 플로이드워셜 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/36) |
| 1차원→2차원 배열 변환 | * `n = (int)Math.sqrt(arr.length)`로 한 변의 길이 구함<br/>* `matrix[i/n][i%n] = arr[i]`로 순서대로 배치<br/>　- i/n: 몇 번째 행인지, i%n: 그 행의 몇 번째 칸인지 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/38) |
| BFS 연결요소 크기 | * 큐에 넣을 때 `visited=true` 표시 → 중복 방문 차단<br/>* count는 "꺼낼 때"(poll 시점) 증가<br/>　- visited 덕분에 각 칸은 딱 한 번만 큐에 들어갔다 나옴<br/>　→ 꺼낸 횟수 = 방문한 칸 수 = 연결된 영역 크기 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/45) |


⬆ [목차로 돌아가기](#목차)


### 수학

| 개념 | 기억포인트 | 링크 |
|---|---|---|
| 곱의 합 최소/최대 (재배열 부등식) | * 최소화: A↑ × B↓ (한쪽 오름차순, 한쪽 내림차순)<br/>* 최대화: A↑ × B↑ (둘 다 같은 순서)<br/>* 구현: 둘 다 오름차순 정렬 후, B는 `B[n-1-i]`로 역순 접근 | [정리](https://github.com/SeoMiYoung/just-do-it/issues/39) |
| 모듈러 연산 (오버플로우 방지) | * 사칙연산은 모듈러를 씌운 채로 진행해도 결과가 같음<br/>　- `(a%M+b%M)%M = (a+b)%M`, 곱셈/뺄셈도 동일<br/>* 마지막에만 % MOD 하면 늦음 → 중간 연산마다 매번 적용해야 함<br/>　- ex) `dp[i] = (dp[i-1]+dp[i-2]) % MOD` (덧셈마다 적용) | [정리](https://github.com/SeoMiYoung/just-do-it/issues/46) |





⬆ [목차로 돌아가기](#목차)
