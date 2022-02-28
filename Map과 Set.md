# Map과 Set
- 객체와 비슷한 map과 배열과 비슷한 set이라는 데이터 구조가 추가되었다
### 1. Map
- 이름이 있는 데이터를 저장한다는 점에서 객체와 비슷하다  
- 메소드를 통해 값을 추가하거나 접근할 수 있다  

|메소드|기능|  
|:---:|:---|  
|map.set(key, value)|key를 이용해 value를 추가하는 메소드|  
|map.get(key)|key에 해당하는 값을 얻는 메소드. key가 존재하지 않으면 undefined를 반환|  
|map.has(key)|key가 존재하면 true, 존재하지 않으면 false를 리턴|  
|map.delete(key)|key에 해당하는 값을 삭제하는 메소드|  
|map.clear()|Map 안의 모든 요소를 제거하는 메소드|  
|map.size|요소의 개수를 반환하는 프로퍼티->메소드는 아니고 배열의 length 프로퍼티같은 역할을 한다|  

```javascript
// new 키워드로 Map 객체 생성
  const users = new Map();

  // map.set(key, value)
  users.set('name', 'sage');
  users.set('age', 26);
  users.set('job', false);
  
  // map.get(key)
  console.log(users.get('name')); // sage
  console.log(users.get('age')); // 26
  console.log(users.get('job')); // false

  // map.has(key)
  console.log(users.has('name')); // true
  console.log(users.has('isMarried')); // false

  // map.size
  console.log(users.size); // 3

  // map.delete(key)
  users.delete('job');
  console.log(users.get('job')); // undefined

  // map.clear()
  users.clear();
  console.log(users.get('name')); // undefined
  console.log(users.size); // 0
```
### 2. Set
- 여러개의 값을 순서대로 저장한다는 점에서 배열과 비슷하다  
- Map과 비슷하게 Set만의 메소드를 이용해 값을 다룬다  

|메소드|기능|  
|:---:|:---|  
|set.add(value)|값을 추가하는 메소드(메소드를 호출한 자리에는 추가된 값을 가진 set을 반환)|  
|set.has(value)|set안에 값이 존재하면 true, 아니면 false를 반환|  
|set.delete(value)|값을 제거하는 메소드(메소드를 호출한 자리에는 제거에 성공하면 true, 실패하면 false를 반환)|  
|set.clear()|set안의 모든 요소를 제거|  
|set.size|요소의 개수를 반환하는 프로퍼티(배열의 lenght 프로퍼티와 같은 역할)|  
```javascript
  const members = new Set();
  
  console.log(members.add('A')); // Set(1) {'A'}
  console.log(members.add('B')); // Set(2) {'A', 'B'}
  console.log(members.add('C')); // Set(3) {'A', 'B', 'C'}

  console.log(members.has('A')); // true
  console.log(members.has('D')); // false

  console.log(members.size); // 3

  members.delete('B');
  console.log(members.has('B')); // false
  console.log(members.size) // 2

  members.clear();
  console.log(members.size); // 0
  ```
- set은 개별값에 바로 접근하는 방법이 없다  
- set은 중복되는 값을 허용하지 않는다  
```javascript
  const numbers = new Set();

  numbers.add(1);
  numbers.add(2);
  numbers.add(3);

  console.log(numbers); // Set(3) {1, 2, 3}

  // 반복문을 통해서 전체요소를 한꺼번에 다룰 때는 그 순간 개별적으로 접근할 수 있다
  for(const num of numbers){
    console.log(num);
  }

  numbers.add(1);
  console.log(numbers); // Set(3) {1, 2, 3} -> 뒤에 추가된 1이 무시되었다
  // 최초에 추가된 순서를 유지하면서, 나중에 중복된 값을 추가하려고 하면 그 값은 무시하는 특징이 있다

  // 처음 set을 생성할 때 인수로 배열을 전달할 수도 있다
  // 이런 특징을 이용해 배열 내에서 중복을 제거한 값들의 묶음을 만들 때 set을 활용할 수 있다
  const str = ['a', 'b', 'c', 'd', 'e', 'a', 'b'];

  const newStr = new Set(str); // 인수로 배열을 넘겨준다
  console.log(newStr); // Set(5) {'a', 'b', 'c', 'd', 'e'}
  ```
