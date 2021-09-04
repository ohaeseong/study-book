해당 게시글에서는 일반 함수와 화살표 함수의 차이점과 this에 대한 내용을 다룹니다.

---

### 1. This란?

일반 함수와 화살표형 함수의 차이점을 알아보려면 우선, this의 개념부터 알아야 합니다.
this는 흔히 객체지향적언어(JAVA/C ... )에서는 보통 class instance 필드에 선언된 레퍼런스 변수를 뜻합니다. 하지만 Javascript에서의 this는 의미가 조금 다릅니다.

> this // window {}
브라우저 콘솔에서 this를 쳐보면 window가 뜨게됩니다.

함수안에서 this를 쳐보면, 

```
function test() {
	console.log(this)
}

test() // window {}
```

마찬가지로 this는 window로 뜹니다.

기본적으로 js는 this가 window를 가르킵니다.

그렇다면 객체 메서드를 선언 해준후 this를 찍어보겠습니다.

```javascript
const obj = {
	a: function test() {
    	console.log(this);
    }
}

obj.a() // obj
```

객체 메서드 내에서 this는 obj 객체를 가르키게 됩니다.
이는 객체 메서드를 호출 할때 this를 내부적으로 바꿔주기 때문입니다.

하지만 다음과 같이 사용한다면,
```javascript
...

const a = obj.a();

a(); // window
```

**this는 호출 할때, 호출하는 함수가 그냥 함수인지, 객체 메서드인지에 따라 변경됩니다.**

위 처럼 불러오는 방식은 obj의 a함수를 꺼내어 쓰는 것이므로 더이상 객체 메서드가 아닌 일반 함수이기 때문에 window가 찍히게 됩니다.

이번엔 생성자 함수의 경우를 보겠습니다.

```javascript
function newObject(name, age) {
	this.name = name;
    this.age = age;
    this.isWindow = function() {
    	return this === window;
    }
}

const newObj = new NewObject('홍길동', 20)
console.log(newObj.name) // 홍길동
console.log(newObj.age) // 20
console.log(newObj.isWindow()) // false
```

다음과 같이 생성자 함수는 처름 실행 할때 부터 this를 사용합니다. 생성자 함수에서 this는 new를 통해 새로 만들어지기 때문에 this는 newObject를 가르키게 됩니다.

여기서 new 키워드를 빼보면,

```javascript
function newObject(name, age) {
	this.name = name;
    this.age = age;
    this.isWindow = function() {
    	return this === window;
    }
}

const newObj = NewObject('홍길동', 20)
console.log(newObj.name) // error
console.log(newObj.age) // error
console.log(newObj.isWindow()) // error
```

new 키워드를 없애버리면 일반 함수와 동일하게 동작하게 됩니다. 때문에 newObject의 this는 window가 되고 window에서 name, age, isWindow를 참조 하려 하니 찾지 못하므로 에러가 뜨게 됩니다.

---

### function vs arrow function

자, 그렇다면 this에 대해 어느정도 알았으니 일반 함수와 화살표 함수의 차이점에서 this가 어떻게 다른건지에 대해 알아보겠습니다.

```javascript
const obj = {
	a: function () {
    	console.log(this)
    }
}

obj.a() // obj
```

위 내용에서 obj.a()는 obj를 찍게 됩니다. 그럼 function 안에 또다른 function을 선언해서 this를 찍어 보겠습니다.

```javascript
const obj = {
	a: function () {
    	b: function () {
        	console.log(this); // window
        }
        
        b();
    }
}

obj.a() // window
```

이렇게 만들어서 this를 찍어 보면 window가 나타납니다. a function의 경우 obj의 객체 메서드 이지만 b function은 무엇도 지정(바인드)되지 않았기 때문에 this가 window를 가르키게 됩니다.

여기서 b function의 this가 obj 객체를 참조하려면 별도의 상수를 선언해서 사용할 수 있습니다.

```javascript
const obj = {
    const that = this;
	a: function () {
    	b: function () {
        	console.log(that); // obj
        }
        
        b();
    }
}

obj.a() // obj
```

하지만 다음과 같이 사용하게 되면 항상 that 변수를 선언해야 합니다. 이와 다르게 bind 함수를 사용해서도 구현이 가능합니다.

```javascript
const obj = {
	a: function () {
    	b: function () {
        	console.log(this); // obj
        }.bind(this);
        
        b();
    }
}

obj.a() // obj
```

하지만 이것도 마찬가지로 항상 bind 작업을 해줘야 합니다.

**여기서 화살표 함수가 나오게 되는데 화살표 함수는 별도의 작업 없이 this에서 객체 값을 가져오게 됩니다.**

```javascript
const obj = {
     a: function () {
    	b: () => {
        	console.log(this); // obj
        }
        
        b();
    }
}

obj.a() // obj
```

---

이것이 일반 함수와 화살표 함수의 차이점 입니다. 물론 이것 외에도 화살표 함수는 new 로 생성할 수 없고, 일반 함수는 가능 하다 던가, 등에 차이점이 있지만 해당 게시글에서는 this에 관련하여 어떤 차이점이 있는지에 대해 알아보았습니다.





