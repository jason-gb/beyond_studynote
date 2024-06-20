# 조인(Join)

* 내부조인 : 가장 보편적인 조인으로써 일반조인이라고 생각할 수 있다.
  * 조인 조건은 on절에 검색 조건은 where절에 하는게 정규식이다.
  * 내츄럴 조인을 잘 안쓰는 이유는 모든 같은 조건을 검색하기 때
* 외부조인 : 조인의 조건을 만족하지 않는 데이터들도 조회하는 조인
  * left outer join : 조건을 만족하지 않더라도 왼쪽의 데이터를 전체 조회
  * right outer join : 조건을 만족하지 않더라도 오른쪽의 데이터를 전체 조회
  * 각각 조인들은 왼쪽에 있는 테이블의 정보를 조회하는지 오른쪽의 있는 테이블의 정보를 조회하는지에 따라서 사용법이 달라진다.
* 상호조인(cross join)
  * 테이블의 각각의 행과 다른 테이블의 각각의 행을 조인함
* 자체조인(self join)
  * 동일한 테이블의 데이터를 조인하여 조인
* Where절
  * 집계함수와 같은 경우에는 having절에 써야한다.
  * like연산자는 텍스트를 중간에 뽑아낼 때 쓴다.

**WHERE**

* `WHERE` 절은 테이블에서 다양한 조건을 설정하여 데이터를 검색할 때 사용하는 구문이다.
*   두 개의 값을 비교하는 `비교 연산자`를 사용할 수 있다. (=, !=, >, <, >=, <=)

    ```
    SELECT *
    FROM employees
    WHERE emp_no = 30000;
    ```
*   여러 개의 조건 결과를 하나의 논리 결과로 만들어주는 `논리 연산자`를 사용할 수 있다. (NOT, AND, OR)

    ```
    SELECT *
    FROM employees
    WHERE emp_no >= 30000 AND emp_no <= 40000;
    ```
*   특정 값이 지정한 범위에 포함되는지 확인하는 `BETWEEN AND 연산자`를 사용할 수 있다.

    ```
    SELECT *
    FROM employees
    WHERE emp_no BETWEEN 30000 AND 40000;
    ```
*   특정 값과 일치하는 값이 목록에 있는지 확인하는 `IN 연산자`를 사용할 수 있다.

    ```
    SELECT *
    FROM employees
    WHERE hobby IN ('축구', '농구', '야구');
    ```
*   문자열을 검색할 때는 `LIKE 연산자`를 사용할 수 있다.

    \`SELECT \* FROM employees WHERE address LIKE '서울%'; -- %는 0 글자 이상을 의미

    SELECT \* FROM employees WHERE name LIKE '김\_현'; -- \_는 1 글자를 의미\`
* 마지막 순서 끝에서부터
  * order by
  * having
  * group by
