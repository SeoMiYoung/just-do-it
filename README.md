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

⬆ [목차로 돌아가기](#목차)


### 알고리즘

| 개념 | 기억포인트 | 링크 |
|---|---|---|

⬆ [목차로 돌아가기](#목차)


### 수학

| 개념 | 기억포인트 | 링크 |
|---|---|---|

⬆ [목차로 돌아가기](#목차)
