# 21.01.19



## 주요 질문



#### 💡 [SubQuery이란 무엇인가요?](#SubQuery)

```markdown
SubQuery란 하나의 SQL문 안에 포함되어 있는 또 다른 SQL문을 말한다.
SubQuery는 메인쿼리가 서브쿼리를 포함하는 종속적인 관계이다.
```

#### 💡 [JOIN이란 무엇인가요?](#JOIN)

```
관계형 데이터베이스에서는 중복 데이터를 피하기 위해서 데이터를 쪼개 여러 테이블로 나눠서 저장합니다.
이렇게 분리되어 저장된 데이터에서 원하는 결과를 다시 도출하기 위해서는 여러 테이블을 조합할 필요가 있습니다.
관계형 데이터베이스에서 조인(JOIN) 연산자를 사용해 관련있는 컬럼 기준으로 행을 합쳐주는 연산입니다.
```

💡 [질문채우기](#)

<br />

## ⭐ 개념 정리

### SubQuery

```markdown
SubQuery란 하나의 SQL문 안에 포함되어 있는 또 다른 SQL문을 말한다.
SubQuery를 포함하고 있는 쿼리를 외부쿼리(outer query) 또는 메인 쿼리라고 부르며, SubQuery는 내부쿼리(inner query)라고도 부른다.
SubQuery는 비교 연산자의 오른쪽에 기술해야 하고 반드시 괄호(())로 감싸져 있어야만 한다.
```

<br />

### SubQuery의 종류

* 중첩 서브 쿼리(Nested SubQuery) : WHERE문에 작성하는 SubQuery

  1. 단일 행 : SubQuery의 결과가 단일행을 리턴
  2. 복수 행 : SubQuery의 결과가 복수행을 리턴 -> IN, ANY, ALL 사용
  3. 다중 컬럼 : SubQuery의 결과가 다중열을 리턴

* 인라인 뷰(Inline View) : FROM문에 작석하는 SubQuery

  ```
  FROM절에서 사용하는 SubQuery를 인라인 뷰(Inline View)라고 한다.
  SubQuery가 FROM절에서 사용되면 뷰(View)처럼 결과가 동적으로 생성된 테이블로 사용 가능
  임시적인 뷰이기 때문에 데이터베이스에 저장되지 않는다.
  동적으로 생성된 테이블이기 때문에 column을 자유롭게 참조 가능
  ```

* 스칼라 서브 쿼리(Scalar SubQuery) : SELECT문에 작성하는 SubQuery -> 한개의 행만 반환

<br />

### SubQuery를 사용할 때 주의할 점

1. SubQuery를 ()로 감싸서 사용한다.
2. SubQuery는 단일 행 또는 복수 행 비교 연산자와 함께 사용 가능
3. SubQuery에서는 ORDER BY를 사용하지 못한다.

<br />

### SubQuery가 사용이 가능한 곳

* SELECT
* FROM
* WHERE
* HAVING
* ORDER BY
* INSERT문의 VALUES
* UPDATE문의 SET

<br />

### JOIN

```
관계형 데이터베이스에서는 중복 데이터를 피하기 위해서 데이터를 쪼개 여러 테이블로 나눠서 저장합니다.
이렇게 분리되어 저장된 데이터에서 원하는 결과를 다시 도출하기 위해서는 여러 테이블을 조합할 필요가 있습니다.
관계형 데이터베이스에서 조인(JOIN) 연산자를 사용해 관련있는 컬럼 기준으로 행을 합쳐주는 연산입니다.
조인(JOIN)조건은 일반적으로 각 테이블의 PK 및 FK로 구성됩니다.
```

<br />

### JOIN의 종류

* 내부 조인(INNER JOIN)

  ```
  가장 일반적인 JOIN의 종류이며 교집합이다.
  동등 조인(Equi-Join)이라고도 하며, N개의 테이블 조인 시 N-1개의 조인 조건이 필요함
  ```

  * 형식

  ```sql
  select employee_id, first_name, salary, employees.department_id, department_name
  from employees, departments
  where employees.department_id = departments.department_id and employee_id = 100;
  ```

  * ON을 이용한 JOIN조건 지정

  ```sql
  select e.employee_id, e.first_name, e.salary, e.department_id, d.department_name
  from employees e inner join departments d
  on e.department_id = d.department_id // (on : 조인조건)
  where e.employee_id = 100; // (where : 일반조건)
  ```

  * USING을 이용한 JOIN조건 지정

  ```sql
  select e.employee_id, e.first_name, e.salary, e.department_id, d.department_name
  from employees e join departments d
  using (department_id) // using (공통칼럼)
  where e.employee_id = 100;
  ```

* 자연 조인(Natural JOIN)

  ```markdown
  자연 조인은 동등 조인의 한 유형으로 두 테이블의 컬럼명이 같은 기준으로 조인 조건문이 암시적으로 일어나는 내부 조인입니다.
  같은 이름을 가진 컬럼은 한번만 추출된다.(동등 조인에서는 같은 이름 컬럼이 여러번 추출된다.)
  ```

  ```sql
  select e.employee_id, e.first_name, e.salary, e.department_id, d.department_name
  from employees e natural join departments d
  where e.employee_id = 100;
  ```

  

* 외부 조인(OUTER JOIN)

  ```markdown
  어느 한쪽 테이블에는 해당하는 데이터가 존재하는데 다른쪽 테이블에는 데이터가 존재하지 않을 경우 그 데이터가 검색되지 않는 문제를 해결하기 위해 사용한다.
  ```

  <img width="992" alt="스크린샷 2022-01-19 오전 10 00 32" src="https://user-images.githubusercontent.com/60912550/150043857-05cf1d72-657e-45fa-8701-0051bb1c0c4e.png">

  * 왼쪽 (LEFT OUTER)

    * 왼쪽 외부 조인은 테이블 A의 모든 데이터와 테이블 B와 매칭이 되는 레코드를 포함하는 조인입니다.

    <img width="835" alt="스크린샷 2022-01-19 오전 10 13 51" src="https://user-images.githubusercontent.com/60912550/150044968-2270493b-b213-43e8-bfe0-c1e612df8a29.png">

  * 오른쪽 (RIGHT OUTER)

    * 오른쪽 외부 조인은 테이블 B의 모든 데이터와 테이블 A와 매칭이되는 레코드를 포함하는 조인입니다

    <img width="833" alt="스크린샷 2022-01-19 오전 10 13 22" src="https://user-images.githubusercontent.com/60912550/150044918-b884f2a6-2527-48b7-a486-090c3ce26b68.png">

  * 완전 외부 조인 (FULL OUTER JOIN)

    * 완전 외부 조인은 MySQL에서는 명시적인 SQL 구문은 지원하지 않지만, UNION을 사용해서 완전 외부 조인을 할 수 있습니다. 

    <img width="862" alt="스크린샷 2022-01-19 오전 10 15 27" src="https://user-images.githubusercontent.com/60912550/150045094-d5d13224-93b6-4ca4-8a38-780d758ab5d0.png">

* 셀프 조인 (SELF JOIN)

  * 셀프 조인은 자기 자신과 조인하는 조인입니다. 예를 들면, 임직원중에 같은 부서에서 일하는 직원을 알고 싶으면 셀프 조인을 사용하면 좋습니다. 

  <img width="836" alt="스크린샷 2022-01-19 오전 10 18 15" src="https://user-images.githubusercontent.com/60912550/150045399-f71ab1c7-4e31-49ad-9628-bb90f57a05c8.png">

* 안티 조인 (ANTI JOIN)

  * 안티 조인은 서브 쿼리내에서 존재하지 않는 데이터만 추출하여 메인 쿼리에서 추출하는 조인입니다. 간단한 예제로 부서 번호(dept_no)가 2 이상이 아닌 데이터와 임직원 번호(emp_no)가 10002이상인 임직원을 추출하기로 보겠습니다. NOT EXISTS나 NOT IN을 사용해서 작성할 수 있습니다. 

  <img width="839" alt="스크린샷 2022-01-19 오전 10 18 48" src="https://user-images.githubusercontent.com/60912550/150045524-3c0e46e0-30f5-48f7-99bc-ac070f5692eb.png">

* 세미 조인 (SEMI JOIN)

  * 세미 조인은 안티 조인과 반대로 서브 쿼리 내에서 존재하는 데이터만을 가지고 메인 쿼리에서 추출하는 방식입니다. 

  <img width="842" alt="스크린샷 2022-01-19 오전 10 19 23" src="https://user-images.githubusercontent.com/60912550/150045579-1e039070-fbd4-434a-a7de-38ea2e7eed6a.png">

<br />

### JOIN을 사용할 때 주의할 점

1. 조인의 처리는 어느 테이블을 먼저 읽을지를 결정하는 것이 중요(처리할 작업량이 상당히 달라진다.)
2. INNER JOIN : 어느 테이블을 먼저 읽어도 결과가 달라지지 않아 MySQL 옵티마이저가 조인의 순서를 조절해서 다양한 방법으로 최적화를 수행할 수 있다.
3. OUTER JOIN : 반드시 OUTER가 되는 테이블을 먼저 읽어야 하므로 옵티마이저가 조인 순서를 선택할 수 없다.