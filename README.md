---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# 데이터베이스 다루기

## 1. 데이터 타입 알아보기&#x20;

<table><thead><tr><th width="140" align="center">데이터 타입</th><th align="center">정의 </th></tr></thead><tbody><tr><td align="center">정수형</td><td align="center">소수점이 없는 숫자 데이터 ex. 486</td></tr><tr><td align="center">실수형</td><td align="center">소수점이 있는 숫자 데이터 ex. 1.14</td></tr><tr><td align="center">문자형</td><td align="center">텍스트로 구성된 문자열 데이터 ex. "ABC", "가나다"</td></tr><tr><td align="center">날짜형</td><td align="center">날짜와 시간 데이터 ex. "2021-12-15 01:02:03"</td></tr></tbody></table>

### 1) 정수형  &#x20;

<table><thead><tr><th width="146" align="center">데이터 타입 </th><th width="102" align="center">바이트 수</th><th align="center">표현 가능한 숫자 범위</th></tr></thead><tbody><tr><td align="center">TINYINT</td><td align="center">1</td><td align="center">-128 ~ 127</td></tr><tr><td align="center">SMALLINT</td><td align="center">2</td><td align="center"> -32.768 ~ 32.767</td></tr><tr><td align="center">MEDIUMINT</td><td align="center">3</td><td align="center">약-838백만-838백만</td></tr><tr><td align="center">INT </td><td align="center">4</td><td align="center">약-21억~+21억</td></tr><tr><td align="center">BIGINT</td><td align="center">8</td><td align="center">약-900경~ +900경</td></tr></tbody></table>

&#x20;_※ 바이트 : 컴퓨터의 저장공간 단위 중 하나_ &#x20;

### 2) 실수형&#x20;

<table><thead><tr><th width="140">데이터 타입 </th><th width="105">바이트 수</th><th>표현 가능한 숫자 범위</th></tr></thead><tbody><tr><td>FLOAT</td><td>4</td><td>소수점 아래 7자리까지 표현</td></tr><tr><td>DOUBLE </td><td>8</td><td>소수점 아래 15자리까지 표현</td></tr></tbody></table>

```sql
숫자형 데이터는 '수'이므로, 데이터 간 연산이 가능하다.
SELECT 1 + 20, 80-12.3 * 5, 20.5;  
```

### 3) 문자형

<table><thead><tr><th width="147" align="center">데이터 타입 </th><th width="146" align="center">최대 바이트 수</th><th align="center">특징</th></tr></thead><tbody><tr><td align="center">CHAR<mark style="color:red;">(n)</mark></td><td align="center">255</td><td align="center"> n을 1부터 255까지 지정 가능 지정 안 할 시 1 자동 입력 고정 길이로 문자열 저장.</td></tr><tr><td align="center"><mark style="background-color:red;">VARCHAR(n)</mark> </td><td align="center">65535</td><td align="center">n을 1부터 65535까지 지정 가능. 지정 안 할 시 사용 불가 변동 길이로 문자열 저장. </td></tr></tbody></table>

* 고정 길이 문자형 (CHAR)  - 정해진 만큼의 공간을 모두 사용
* 변동 길이 문자형 (VARCHAR)  - 필요한 만큼의 공간만 사용&#x20;

<table><thead><tr><th width="156" align="center">데이터 타입 </th><th width="138" align="center">고정 바이트 수</th><th align="center">특징</th></tr></thead><tbody><tr><td align="center">TINYTEXT</td><td align="center">255</td><td align="center">255 바이트의 문자열까지 표현 가능 </td></tr><tr><td align="center">TEXT</td><td align="center">65535</td><td align="center">65535 바이트의 문자열까지 표현 가능 </td></tr><tr><td align="center">MEDIUMTEXT </td><td align="center">약 천 6백만</td><td align="center">약 천 6백만 바이트의 문자열까지 표현 가능</td></tr><tr><td align="center">LONGTEXT</td><td align="center">약 42억</td><td align="center">약 42억 약 42억 바이트의 문자열까지 표현 가능</td></tr></tbody></table>

```sql
문자형 데이터는 반드시 "" 또는 ''와 함께 쓰여야 한다. 
SELECT "id"; 
따옴표가 없는 문자는 키워드나 함수, 데이터베이스/테이블/컬럼의 이름으로 인식된다.
SELECT id; 
```

### 4)  날짜형&#x20;

<table><thead><tr><th width="134" align="center">데이터 타입 </th><th width="107" align="center">바이트 수</th><th align="center">표현 가능 범위</th></tr></thead><tbody><tr><td align="center">DATE </td><td align="center">3</td><td align="center">0000-00-00-9999-12-31 </td></tr><tr><td align="center">DATETIME </td><td align="center">3</td><td align="center">0000-00-00 00:00:00~9999-12-31 23:59:59</td></tr><tr><td align="center">TIME </td><td align="center">4</td><td align="center"> -838:59:59-838:59:59 </td></tr><tr><td align="center">YEAR </td><td align="center">1</td><td align="center">1901-2155</td></tr></tbody></table>



## 2. 기본적인 데이터 다뤄보기

### 데이터 타입 간 타입 변화

```sql
숫자형, 문자형, 날짜형 데이터는 함수를 사용하여 서로 타입 변환이 가능 합니다.

1. 숫자를 문자로 변환
SELECT CAST(123 AS CHAR(5)); -- 숫자 123을 5자리 문자열로 변환합니다.

2. 문자를 숫자로 변환
SELECT CONVERT('1004', INT); -- 문자열 '1004'를 정수형으로 변환합니다.

3. 문자를 날짜로 변환
SELECT DATE_FORMAT('20211225', '%Y-%m-%d'); -- 문자열 '20211225'를 'YYYY-MM-DD' 형식의 날짜로 변환합니다.
```



## 3. DB, 테이블, 컬럼&#x20;

### 1) 명명 규칙

1. 문자, 숫자를 사용합니다.
2. 이름에 쓰이는 문자는 주로 영문 소문자를 사용합니다.&#x20;
   * 한글도 사용은 가능하지만 인코딩 이슈로 주로 영문 사용 .&#x20;
   * 보통 키워드나 함수명은 대문자, 사용자가 정의한 이름에는 소문자 사용
3. 예약어는 사용할 수 없습니다.&#x20;
   * 예약어 : 이미 키워드, 함수명 등의 문법적인 용도로 사용되고 있기 때문에 이름으로 사용할 수 없는 단어&#x20;
4. 단어와 단어 사이에는 빈칸 대신 \_ 를 사용합니다.
5. 문자로 시작합니다.&#x20;
   * 숫자로 시작하지 않습니다.
6. 데이터베이스 이름은 중복될 수 없습니다.&#x20;
   * 테이블 이름은 하나의 데이터베이스 내에서는 중복될 수 없습니다. &#x20;
   * 컬럼 이름은 하나의 테이블 내에서는 중복될 수 없습니다.

### 2) DB&#x20;

<pre class="language-sql"><code class="lang-sql"><strong>1. 만들기 
</strong>CREATE DATABASE [데이터 베이스 이름]; 

2. 목록 보기 
SHOW DATABASES; -- S를 꼭 붙여야 함! 

3. 사용
USE [데이터 베이스 이름]; 

4. 지우기 
DROP DATABASE [데이터 베이스 이름]; -- DB를 삭제
DROP DATABASE IF EXISTS [데이터 베이스 이름]; -- DB가 존재한다면 삭제
</code></pre>

### 3) 테이블

<pre class="language-sql"><code class="lang-sql">1. 만들기 
CREATE TABLE idol ( 
<strong>        name VARCHAR(20), 
</strong><strong>        age INT,
</strong><strong>        group VARCHAR(50)
</strong>);

2. 지우기 
DROP TABLE [테이블 이름]; -- 테이블을 통째로 삭제 
DROP TABLE IF EXISTS [테이블 이름]; -- 테이블이 존재하다면, 통째로 삭제 

3. 테이블의 값만 지우기    
TRUNCATE TABLE [테이블 이름]; -- 테이블은 유지하고, 값만 삭제

4. 이름 변경 
ALTER TABLE [테이블 이름] RENAME [새로운 테이블 이름];
ALTER TABLE costomor RENAME customers; 
</code></pre>

### 4)  컬럼&#x20;

```sql
1. 기존 컬럼의 타입 변경 
ALTER TABLE [테이블 이름] MODIFY COLUMN [컬럼 이름] [새로운 데이터 타입];
ALTER TABLE customers MODIFY COLUMN age FLOAT;

2. 기존 컬럼의 이름과 타입 변경 
ALTER TABLE [테이블 이름] CHANGE COLUMN [현재 컬럼 이름] [새로운 컬럼 이름] [새로운 데이터 타입];
ALTER TABLE customers CHANGE COLUMN age new_age FLOAT;

3. 새 컬럼 추가 
ALTER TABLE [테이블 이름] ADD COLUMN [컬럼 이름] [데이터 타입];
ALTER TABLE customers ADD COLUMN age INT;

4. 컬럼 지우기
ALTER TABLE [테이블 이름] DROP COLUMN [컬럼 이름];
ALTER TABLE customers DROP COLUMN new_age;
```









