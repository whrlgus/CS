## Differences between pointers and references in C++

https://www.educative.io/edpresso/differences-between-pointers-and-references-in-cpp

C++에서 **pointer** 는 다른 변수의 메모리 주소를 가지고 있는 변수이다. 

**reference** 는 이미 존재하는 변수의 별칭(alias)이다. 분리된 메모리 공간에 참조하는 주소를 저장하지 않는다. 한번 초기화되면 다른 변수를 참조하도록 변경할 수가 없다. 따라서, **const pointer** 와 유사하다.

| Pointer                                                      | Reference                                              |
| ------------------------------------------------------------ | ------------------------------------------------------ |
| 선언한 이후에 언제든 다른 값으로든 초기화될 수 있다.         | 반드시 선언할 때 초기화 되어야 한다.                   |
| NULL 값을 할당할 수 있다.                                    | NULL 을 참조할 수 없다.                                |
| `*` 을 사용하여 저장된 주소값에 접근할 수 있다. (dereference) | 단순히 이름만으로 사용할 수 있다.                      |
| 같은 타입의 다른 변수를 가리키도록 변경할 수 있다.           | 한번 초기화되면 다른 변수를 참조하도록 변경할 수 없다. |



## Pointers vs References in C++

https://www.geeksforgeeks.org/pointers-vs-references-cpp/

reference와 pointer는 다른 변수에 접근하기 위한 변수를 갖는다는 점에서 유사하다. 

**pointer** 는 다른 변수의 메모리 주소를 가지고 있는 변수이다. 포인터가 가리키는 메모리 위치에 접근하기 위해 `*` operator로 dereference 해야 한다. 

**reference** 변수는 이미 존재하는 변수의 alias이다. 포인터와 같이 객체의 주소를 저장하도록 구현되었다. constant pointer 로 생각할 수 있으며, compile 시에 `*` operator가 적용된다.

### Differences

#### 1. Initialization: 포인터는 다음 방식으로 초기화된다.

```c++
int a = 10;
int *p = &a;
// or
int *p;
p = &a;
// 선언과 초기화를 동시에 혹은 여러줄에 걸쳐 할 수 있다.
```

#### 2. 반면 reference는

```c++
int a = 10;
int &p = a; // 올바른 방법
// but
int &p;
p = a; // 잘못된 사용법으로 참초는 선언과 동시에 초기화를 해야한다.
```

#### 3. NOTE: 이러한 차이는 컴파일러마다 차이가 있을 수 있다.

#### 4. Reassignment: 포인터는 재할당이 가능하지만, 참조는 불가능하다.

#### 5. Memory Address: 포인터는 스택에 자신의 메모리 주소와 크기를 갖는 반면, 참조는 참조하는 변수의 메모리 주소를 공유한다. 그러나 여전히 스택에 공간은 차지한다.

그러면 스택에 어떤 식으로 데이터가 쌓이는 거지? https://stackoverflow.com/a/38310081

#### 6. NULL 값: 포인터는 NULL을 직접 할당할 수 있지만, 참조는 불가능하다. NULL할당이 불가하고, 재할당도 안되는 이런 제약은 예외 상황에 처하지 않음을 보장해준다.

#### 7. Indirections: 추가 level of indirection을 통해 포인터의 포인터를 정의할 수 있다. 반면, 참조는 한 단계의 indirection만 가능하다.

#### 8. Arithmetic operations: 포인터로 다양한 산술 연산이 가능하지만 참조는 그렇지 못하다. (그러나 참조가 가리키는 주소로는 가능하다.)

### When to use What

reference가 내부적으로 pointer처럼 구현되어 성능은 동일하다. 

- Use references:
  - 함수의 파라미터와 반환 타입에 사용
- Use pointers:
  - 배열에서와 같이 산술연산이 필요하거나 NULL 할당이 필요하면 사용
  - Linked list, tree 등 다른 구간을 가리키기 위해서는 포인터 개념을 사용