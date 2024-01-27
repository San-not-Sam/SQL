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

### 1) 정수형 - 소수점이 없는 숫자 데이터&#x20;

<table><thead><tr><th width="146" align="center">데이터 타입 </th><th width="102" align="center">바이트 수</th><th align="center">표현 가능한 숫자 범위</th></tr></thead><tbody><tr><td align="center">TINYINT</td><td align="center">1</td><td align="center">-128 ~ 127</td></tr><tr><td align="center">SMALLINT</td><td align="center">2</td><td align="center"> -32.768 ~ 32.767</td></tr><tr><td align="center">MEDIUMINT</td><td align="center">3</td><td align="center">약-838백만-838백만</td></tr><tr><td align="center">INT </td><td align="center">4</td><td align="center">약-21억~+21억</td></tr><tr><td align="center">BIGINT</td><td align="center">8</td><td align="center">약-900경~ +900경</td></tr></tbody></table>

&#x20;_※ 바이트 : 컴퓨터의 저장공간 단위 중 하나_ &#x20;

### 2) 실수형 - 소수점이 있는 숫자 데이터

<table><thead><tr><th width="140">데이터 타입 </th><th width="105">바이트 수</th><th>표현 가능한 숫자 범위</th></tr></thead><tbody><tr><td>FLOAT</td><td>4</td><td>소수점 아래 7자리까지 표현</td></tr><tr><td>DOUBLE </td><td>8</td><td>소수점 아래 15자리까지 표현</td></tr></tbody></table>

### 3) 문자형

<table><thead><tr><th width="147" align="center">데이터 타입 </th><th width="146" align="center">최대 바이트 수</th><th align="center">특징</th></tr></thead><tbody><tr><td align="center">CHAR<mark style="color:red;">(n)</mark></td><td align="center">255</td><td align="center"> n을 1부터 255까지 지정 가능 지정 안 할 시 1 자동 입력 고정 길이로 문자열 저장.</td></tr><tr><td align="center"><mark style="background-color:red;">VARCHAR(n)</mark> </td><td align="center">65535</td><td align="center">n을 1부터 65535까지 지정 가능. 지정 안 할 시 사용 불가 변동 길이로 문자열 저장. </td></tr></tbody></table>

* 고정 길이 문자형 (CHAR)  - 정해진 만큼의 공간을 모두 사용
* 변동 길이 문자형 (VARCHAR)  - 필요한 만큼의 공간만 사용&#x20;



## 2. 기본적인 데이터 다뤄보기
