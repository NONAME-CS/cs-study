# 21.01.24



## 주요 질문



#### 💡 [Redo 란 무엇인가요?](#Redo)

```markdown
Undo는 "원상태로 되돌리다"라는 의미이다.
따라서 Undo 작업은 복구, 롤백을 의미한다.
트래잭션을 이전 상태로 되돌리는 것을 의미
작업 롤백, 읽기 일관성, 복구
사용자가 했던 작업을 반대로 진행함
```

#### 💡 [Uedo 란 무엇인가요?](#Uedo)

```markdown
이전 상태로 되돌아간 후, 실패가 발생하기 전까지의 과정을 그대로 따라가는 것을 의미합니다.
redo를 하기 위해서는 정상적으로 실행 되기까지의 과정을 기록해야 하는데, 이를 log라고 합니다.
복구의 역할, 오라클 서버에 무슨 작을 하든지 모두 redo에 기록이 됩니다.(undo포함)
사용자가 했던 작업을 그대로 다시 함
```

<br />

## ⭐ 개념 정리

### Redis(Remote Dictionary Server)

```markdown
Redis는 NOSQL로서 Key-Value타입의 저장소이다.
Redis는 Memcached와 비슷한 캐시 시스템으로서 동일한 기능을 제공하면서 영속성, 다양한 데이터 구조와 같은 부가적인 기능을 지원하고 있습니다.
레디스는 모든 데이터를 메모리에 저장하고 조회합니다. 즉, 인메모리 데이터베이스입니다.
이 말만 들으면 Redis는 모든 데이터를 메모리에 저장하는 빠른 DB가 다라고 생각할 수도 있습니다.
하지만 빠른 성능은 레디스의 특징 중 일부분 입니다. 다른 인메모리 DB들과의 가장 큰 차이점은 다양한 자료구조 입니다.
```



<br />

### Redis 자료구조

<img width="736" alt="스크린샷 2022-01-25 오전 9 22 12" src="https://user-images.githubusercontent.com/60912550/150887249-cdbb3e0a-9b33-424c-a2e4-7af180ad815e.png">

```markdown
이렇게 다양한 자료구조를 지원하게 되면 개발의 편의성도 좋아지고 난이도가 낮아진다는 장점이 있습니다.
예를들어, 어떤 데이터를 정렬해야하는 상황이 있을 때, DBMS를 이용한다면 DB에 데이터를 저장하고, 저장된 데이터를 정렬하여 다시 읽어오는 과정은 디스크에 직접 접근해야 하기 때문에 시간이 더 걸린다는 단점이 있습니다.
하지만 In-Memory DB인 Redis를 이용하고 레디스에서 제공하는 Sorted-Set이라는 자료구조를 사용하면 더 빠르고 간단하게 데이터를 정렬할 수 있습니다.
```

<br />

### Redis 특징

* 영속성을 지원하는 인메모리 데이터 저장소
* 읽기 성능 증대를 위한 서버 측 복제를 지원
* 쓰기 성능 증대를 위한 클라이언트 측 샤딩(Sharding) 지원
* 다양한 서비스에서 사용되며 검증된 기술
* 문자열, 리스트, 해시, 셋, 정렬된 셋과 같은 다양한 데이터형을 지원
* 메모리 저장소임에도 불구하고 많은 데이터형을 지원하므로 다양한 기능을 구현

<br />

### Redis 장점

* 리스트, 배열 데이터를 처리하는 데 유용
* 리스트 형 데이터 입력, 삭제가 MySQL에 비해 10배정도 빠름
* 영속적인 데이터 보존

<br />

### Redis 영속성

```markdown
Redis는 지속성을 보장하기 위해 데이터를 disk에 저장할 수 있습니다.
서버가 내려가더라도 disk에 저장된 데이터를 읽어서 메모리에 로딩을 합니다.
데이터를 disk에 저장하는 방식은 크게 두 가지 방식이 있습니다.
```

* RDB(Snapshotting) 방식
  * 순간적으로 메모리에 있는 내용을 disk에 전체를 옮겨 담는 방식
* AOF(Append On File) 방식
  * Redis의 모든 Wirte/Update 연산 자체를 모두 log파일에 기록하는 형태

### 요약

* 레디스는 고성능 키-값 저장소로서 문자열, 리스트, 해시, 셋, 정렬된 셋 형식의 데이터를 지원하는 NoSQL이다.