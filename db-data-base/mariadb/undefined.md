# 함수

* emplyee 테이블에서 사원명,이메일,아이디 출력
  * SELECT emp\_name, email, left(email,INSTR(email,'@')-1) AS 'id' FROM employee;
  * 위와 같이 두개를 섞어서 사용 가능
* SELECT CURDATE(), —현재 년월일 CURTIME(), —현재 시간 NOW(), — 현재 년월일 시간 SYSDATE(); — 현재 년월일 시간
*
  *

SELECT YEAR(CURDATE()), — 현재 년월일에서 년도 MONTH(CURDATE()), — 현재 년월일에서 월 DAYOFMONTH(CURDATE()); — 현재 년월일에서 일

*
  *

SELECT HOUR(CURTIME()),— 현재 시간에서 시간 MINUTE(CURTIME()),—현재 시간에서 분 SECOND(CURTIME()),— 현재 시간에서 초 MICROSECOND(CURTIME());— 현재 시간에서 마이크로초(안됨)

*
  * 키가 큰 순으로 순위를 매겨서 순위, 이름 주소 키를 조회
* 동일한 순위 이후의 등수를 동일한 인원수만큼 건너뛰고 증가 SELECT RANK() OVER(ORDER BY height DESC) AS 'rank', NAME, addr, height FROM usertbl;
*
  * 키가 큰 순으로 순위를 매겨서 순위, 이름 주소 키를 조회 -- 동일한 위 이후의 등수를 1 증가 SELECT DENSE\_RANK() OVER(ORDER BY height DESC) AS 'rank', NAME, addr, height FROM usertbl;
* PARTITION BY : 이 그룹으로 구획을 나눔(그룹화)
* 다중 조인은 한줄에 일단 버버버벅 하는게 아니라 한개의 조인을 하고 그 결과로 한개의 조인을 더 한다.

primary key 설정하는 방법

1. 테이블 생성 시 설정

```sql
class_no VARCHAR(10) PRIMARY KEY
```

2. 테이블 생성 시 추가로 지정

```sql
CREATE TABLE tb_class(
	class_no VARCHAR(10),
	PRIMARY KEY (class_no)
);

-- 이름이 이렇게 한다면 이렇게도 가능
CREATE TABLE member
(
    mem_id CHAR(8) NOT NULL,
    CONSTRAINT PRIMARY KEY PK_member_mem_id (mem_id)
);
```

3. 따로 추가로 지정

```sql
ALTER table tb_grade ADD PRIMARY KEY (tern_no); 
```

#### foreign key 설정 하는법

1. 테이블 생성시 설정

```sql
class_no VARCHAR(10) REFERENCES tb_class(class_no)
```

2. 테이블 아래에 추가로 지정

```sql
CREATE TABLE buy
(
    num INT AUTO_INCREMENT NOT NULL PRIMARY KEY,
    mem_id CHAR(8) NOT NULL,
    prod_name CHAR(6) NOT NULL,
    FOREIGN KEY(mem_id) REFERENCES member(mem_id)
);
```

3. 따로 추가로 지정

```sql
ALTER TABLE tb_grade 
ADD CONSTRAINT FOREIGN KEY (class_no) REFERENCES tb_class(class_no);
```
