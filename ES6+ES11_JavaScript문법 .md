#  ES6 + ES11 JavaScript 문법  
### 1. shorthand property names  
- 키와 값의 이름이 같으면 생략해서 작성가능하다  
```javascript 
  const person1 = {
    name: 'sage',
    age:26
  };
  const name = 'sage';
  const age = '18';

  const person2 = {
    name, // name:name
    age // age:age -> 이렇게 작성한 것과 같음
  }
  
  console.log(person1, person2);
  //{name: 'sage', age: 26}
  //{name: 'sage', age: '18'}
```
### 2. 구조 분해 할당(destructuring assignment)  
- 객체나 배열을 분해하여 변수에 할당할 수 있다.  
```javascript 
  const student = {
    name: 'sage',
    level: 1
  };

  // 일반적으로 객체의 값을 하나 하나 저장하는 방법
    const name = student.name;
    const level = student.level;
    console.log(name, level); // sage 1
  ```  
  ```javascript
    // 객체 안에 있는 키의 이름을 정의하고 해당 객체를 할당한다
    // 키의 이름은 객체 안에 있는 키의 이름과 동일하게 해준다
    const {name, level} = student;
    console.log(name, level); // sage 1

    // 키의 이름을 동적으로 변경할 수 있다
    const {name:studentName, level:studentLevel} = student;
    // 변경된 키의 이름으로 값을 불러올 수 있다.
    console.log(studentName, studentLevel); // sage 1

    // 객체 뿐만 아니라 배열에서도 사용할 수 있다
    const animals = ['cat', 'dog'];

    // const first = animals[0];
    // const second = animals[1];
    // console.log(first, second); -> cat dog

    // 객체면 중괄호{}, 배열이면 각괄호[]를 사용한다
    const [first, second] = animals;
    console.log(first, second); // cat dog
  ```
  ### 3. spread syntax(...)
 - 배열이나 객체를 복사한다.  
 - 객체가 가리키는 주소를 참조해온다
```javascript  
  // 배열 복사
  const obj1 = {key:'key1'};
  const obj2 = {key:'key2'};
  const arr = [obj1, obj2];

  // 객체의 주소값이 복사되어져 오기 때문에 원본 객체의 값을 변경하면
  // 복사한 객체의 값도 변경된다.
  const arrCopy1 = [...arr];
  // 새로운 값을 추가하고 싶다면 바로 추가가 가능하다
  const arrCopy2 = [...arr, {key:'key3'}]; 
  console.log(arrCopy2); 
  // 0: {key: 'key1'}
  // 1: {key: 'key2'}
  // 2: {key: 'key3'} -> new!! 새로운 값이 추가되었다
  ```  
  ```javascript  
  // 객체 복사
  // obj1을 복사
  const obj3 = {...obj1};
  console.log(obj3); // {key: 'key1'}

  // 두 개의 배열을 하나도 합칠 수 있다
  const fruits1 = ['apple', 'banana'];
  const fruits2 = ['lemon', 'kiwi'];
  const fruits3 = [...fruits1, ...fruits2];
  console.log(fruits3); // ['apple', 'banana', 'lemon', 'kiwi']

  // 두 개의 객체를 하나도 합치기
  const cat1 = {cat1: 'jori'};
  const cat2 = {cat2: 'cola'};
  const cats = {...cat1, ...cat2};
  console.log(cats); // {cat1: 'jori', cat2: 'cola'}
  // 주의: 키가 같은 객체를 병합한다면 뒤에 오는 키가 앞에 오는 키를 덮어 씌운다
  ```  
  ### 4. 삼항 연산자(ternary operator) : A ? true : false;
  ```javascript  
    const isCat = true;
  {
    let component;
    if(isCat){
      component = 'cat';
    } else {
      component = 'dog';
    }
    console.log(component); //cat
  }
  // 삼항 연산자 사용
  { 
    // isCat이 true면 'cat'이 false면 'dog'가 출력된다
    const component = isCat ? 'cat' : 'dog';
    console.log(component); // cat
  }
  ``` 
  ### 5. optional chaining(?.)
  - (?.)앞의 평가 대상이 null이거나 undefined이면 평가를 중단하고 undefined을 반환한다.  
  ```javascript  
    // 중첩된 프로퍼티를 가진 객체
    const person1 = {
    name:'sage',
    job:{
      title:'front-end developer',
      manager:{
        name:'Bob',
      },
    },
  };
  
  // 프로퍼티가 하나인 객체
  const person2 = {
    name:'sese'
  };
  
  // <발생할 수 있는 문제>
    {
    function printManager(person){
      console.log(person.job.manager.name);
    }
    printManager(person1); // Bob
    // printManager(person2); -> 에러-해당하는 값이 없다
  }
  
  // optional chaining(?.)을 사용
    {
    function printManager(person){
      console.log(person.job?.manager?.name);
    }
    printManager(person1); // Bob
    printManager(person2); // undefined
  }
  ```  
  ### 6. null 병합 연산자(??)  
  - A ?? B -> A가 null 이거나 undefined이면 B를 실행한다.
  ```javascript  
    // false인 값 - false, '', 0, null , undefined
  {
    // ||(or)연산자는 앞에 있는 값이 false일 때만 뒤에 있는 것이 실행된다
    const name = 'sage';
    // name이 true이므로 'person'이 아닌 'sage'가 출력된다
    const userName = name || 'person';
    console.log(userName); // sage
  }
  {
  const name = null;
  const userName = name || 'person';
  console.log(userName); // person
  // 주의 : 버그를 유발할 수 있다
  }
  ```  
  ```javascript  
    {
    const name = '';
    // name이 null이거나 undefined이면 'person'을 출력한다
    const userName = name ?? 'person';
    console.log(userName); // ''

    const num = 0;
    const msg = num ?? 'undefined';
    console.log(msg); // 0
  }
  ```  
  
