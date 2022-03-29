## 타입 스크립트를 이해하면  어떤 브라우저나 어떤 OS 어떤 자바스크립트보다 코드를 실행하기전에 당신의 시간을 절약해준다
## 그리고 완전 오픈소스이다

# TypeScript
## =Language
## =Typed Superset of JavaScript
## =compiles to plain JavaScript

* 타입스크립트는 'Programming Languge 언어' 입니다.
* 타입스크립트는 'Compiled Languge' 입니다.
* 전통적인 Compiled Languge 와는 다른 점이 많습니다.
* 그래서 'Transpile' 이라는 용어를 사용하기도 합니다.
* 자바스크립트는 ' interpreted Languge' 입니다.

# node.js
* Chrome's v8 JavaScropt Engine 을 사용하며, 자바스크립트를 해석하고 OS 레벨에서의 API를 제공하는
* 서버 사이드 용 자바스크립트 런타임 환경
# browser
### HTML 을 동적으로 만들기 위해 브라우저에서 자바스크립트를 해석하고, DOM을 제어할 수 있도록 하는 자바스크립트 런타임 환경
* 간단한 컴파일러 사용 예제
* 타입 스크립트 컴파일러를 글로벌로 설치 후,
  - cli 명령어로 파일 컴파일
  - 특정 프로젝트 폴더에서 타입 스크립트 컴ㅁ파일러 설정에 맞춰 컴파일
  - 특정 프로젝트 폴더에서 타입 스크립트 컴파일러 설정에 맞춰 컴파일 (watch 모드)
* 프로젝트에 타입 스크립트 컴파일러를 설치 후, .bin 안의 명령어로 파일 컴파일
  - npm 스크립트로 파일 컴파일
  - 프로젝트에 있는 타입스크립트 설정에 맞춰, npm 스크립트로 컴파일
  - 프로젝트에 있는 타입스크립트 설정에 맞춰, npm 스크립트로 컴파일 (watch 모드)

* 프로그램이 유용하려면, 가장 간단한 데이터 단위로 작업할 수 있어야 한다.
* :numbers, strings, structures, boolean 값 등등

* TypeScript 에서, 우리는 JavaScript 에서 기대하는 것과 동일한 타입을 지원하며, 돕기 위해 추가적인 열거타입을 제공함.

* TypeScript 에서 프로그램 작성을 위해 기본 제공하는 데이터 타입
* 사용자가 만든 타입은 결국은 이 기본 자료형들로 쪼개진다
* JavaaScript 기본 자료형을 포함(superset)
* ECMAScript 표준에 따른 기본 자료형은 6가지
	- Boolean
	- Number
	- String
	- Null
	- Undefined
	- Symbol (ECMAScript 6 에 추가)
	- Array: object 형
* 프로그래밍을 도울 몇가지 타입이 더 제공된다
	- Any, Void, Never, Unknown 
	- Enum
	- Tuple: object 형
---
# Primitve Type
* 오브젝트와 레퍼런스 형태가 아닌 실제 값을 저장하는 자료형이다.
* 프리미티브 형의 내장 함수를 사용 가능한 것은 자바스크립트 처리방식 덕분
* (ES2015 기준) 6가지
  - boolean
  - number
  - string
  - symbol (ES2015)
  - null
  - undefined

---
# Number / number

* JavaScript 와 같이, TypeScript 의 모든 숫자는 부동 소수점 값 이다.
* TypeScript는 16진수 및 10진수 리터럴 외에도, ECMAScript 2015에 도입된 2진수 및 8진수를 지원한다.
* NaN
* 1_000_000 과 같은 표기도 가능
```
let decimal: number = 6;

let hex: number = 0xf00d;

let binary: number = 0b1010;

let octal: number = 0o744;

let notANumber: number = NaN;

let underscoreNum: number = 1_000_000;
```
---
# Template String

* 행에 걸쳐있거나, 표현식을 넣을 수 있는 문자열
* 이 문자열은 backtik (=backquote) 기호에 둘러쌓여 있다.
* 포함된 표현식은 \`${expr}` 와 같은 형태로 사용된다.
```
let fullName: string = 'Mark Lee';
let age: number = 39;

let sentence: string = `Hello, my name is ${ fullName }.

I'll be ${age + 1} years old next month.`;

console.log(sentence)
```
---
# Symbol
* ECMAScript 2015 의 Symbol 이다.
* new Symbol 로 사용할 수 없다
* Symbol 을 함수로 사용해서 symbol 타입을 만들어 낼 수 있다.
```
let sym = Symbol( );

let obj = {
  [sym]: "value"
};
 console.log(obj[sym]);  // "value"
 ```
---
# Undefined & Null

* TypeScript 에서, undefined 와 null 은 실제로 각각 undefined 및 null 이라는 타입을 가진다.

* void 와 마찬가지로, 그 자체로는 그다지 유용하지 않다.

* 둘다 소문자만 존재

# undefined & null are subtypes of all other types.

* 설정을 하지 않으면 그렇다

* number 에 null 또는 undefined 를 할당할 수 없다

* 하지만, 컴파일 옵션에서  \`--strictNullChecks` 사용하면, null 과 undefined 는 void 나 자기 자신들에게만 할당할 수 있다.

	- 이 경우, null 과 undefined 를 할당할 수 있게 하려면, union type 을 이용해야한다.


---
# null in JavaScript

* null 이라는 값으로 할당된 것을 null 이라고 한다.
* 무언가가 있는데, 사용할 준비가 덜 된 상태.
* null 이라는 타입은 null 이라는 값만 가질 수 있다.
* 런타임에서 typeof 연산자를 이용해서 알아내면, object 이다.
---
# undefined in JavaScript

* 값을 할당하지 않은 변수는undefined 라는 값을 가진다.
* 무언가가 아예 준비가 안된 상태
* object 의 property 가 없을 때도 undefined 이다.
* 런타임에서 typeof 연산자를 이용해서 알아내면, undefined 이다.
---
# object

* "primitive type 이 아닌 것" 을 나타내고 싶을 때 사용하는 타입
---
# non-primitive type

* number, string, boolean, bigint, symbol, null, or undefined.
* 이것들이 아닌 경우를 할당할 수 있으면 오브젝트를 써라
---
# any

* 어떤 타입이어도 상관없는 타입
* 이걸 최대한 쓰지 않는게 핵심
* 왜냐, 컴파일 타임에 타입 체크가 정상적으로 이뤄지지 않기 때문
* 그래서 컴파일 옵션중에는 any를 써야하는데 쓰지 않으면 오류를 뱉도록 하는 옵션도 있다.
	- nolmplicittAny
* any 는 계속해서 개체를 통해 전파된다.
* 결국, 모든 편의는 타입 안전성을 잃는 대가로 온다는 것을 기억
* 타입 안전성은 TypeScript 를 사용하는 주요 동기 중 하나이며 필요하지 않는 경우에는 any 를 사용하지 않도록 하자
---
# unknown

* 응용프로그램을 작성할 때 모르는 변수의 타입을 묘사해야할 수도 있다
* 이러한 값은 동적 콘텐츠(예: 사용자로부터, 또는 우리 API의 모든 값을 의도적으로 수락하기를 원할 수 있다.
* 이 경우, 컴파일러와 매리의 코드를 읽는 사람에게 이 변수가 무엇이든 될 수 있음을 알려즈는 타입의 제공하기를 원하므로 unknown 타입을 제공한다.

* Typescript 3.0 버전부터 지원
* any 와 짝으로 any 보다 Type-safe 한 타입
	- any 와 같이 아무거나 할당할 수 있다.
	- 컴파일러가 타입을 추론할 수 있게끔 타입의 유형을 좁히거나 타입을 확정해주지 않으면 다른곳에 할당할 수 없고, 사용할 수 없다.
* unkniwn 타입을 사용하면 runtime error 를 줄일 수 있을 것이다.
	- 사용전에 데이터의 일부 유형의 검사를 수행해야 함을 알리는 API에 사용될 수 있을 것이다.

---
# never

* never 타입은 모든 타입의 subtype 이며, 모든 타입에 할당할 수 없다.
* 하지만, never 에는 그 어떤 것도 할당할 수 없다.
* any 조차도 never 에게 할당될 수 없다.
* 잘못된 타입을 넣는 실수를 막고자 할 때 사용되기도 한다.
---
# nomplicitAny 옵션을 켜면

* 타입을 명시적으로 지정하지 않은 경우, 타입스크립트가 추론 중 'any' 라고 판단하게 되면,
* 컴파일 에러를 발생시켜 명시적으로 지정하도록 유도한다.
---
# strictNullChecks 옵션을 켜면

- 모든 타입에 자동으로 포함되어 있는 'null' 과 'undefined' 를 제거해 준다.
---
# nolmplicitReturns 옵션을 켜면

* 함수 내에서 모든 코드가 값을 리턴하지 않으면, 컴파일 에러를 발생시킨다
---
# structural type system 
- 구조가 같으면, 같은 타입이다.

# nominal type system
- 구조가 같아도 이름이 다르면, 다른 타입이다.

# duck typing
- 만약 어떤 새가 오리처럼 걷고, 헤엄치고, 꽥꽥거리는 소리를 낸다면 나는 그 새를 오리라고 부를 것이다.
---
# 타입 호환성
1. 같거나 서브 타입인 경우, 할당이 가능하다. => 공변

2. 함수의 매개변수 타입만 같거나 슈퍼타입인 경우, 할당이 가능하다. => 반병

3. strictFunctionTypes 옵션을 켜면
함수를 할당할 시에 함수의 매개변수 타입이 같거나 슈퍼타입인 경우가 아닌 경우, 에러를 통해 경고한다.
---
# 타입 별칭

* interface 랑 비슷해 보인다.
* Primitive, Union Type, Tuple, Function
* 기타 직접 작성해야하는 타입을 다른 이름을 지정할 수 있다.
* 만들어진 타입의 refer 로 사용하는 것이지 타입을 만드는 것은 아니다.
---
# 최상위 프로퍼티

* compileOnSave
* extends
* compileOptions
* files
* include
* exclude
* references
* typeAcquisition
* tsNpde

---
# compileOnSave
* true / false (default false)
* 누가 ??
	- Visual Studio 2015 with TypeScript 1.8.4 이상
	- atom-typescript 플러그인
	
*	https://github.com/TypeStrong/atom-typescript#compil-on-save

---
# extends

* 파일 (상대) 경로명: string
* TypeScript 2.1 New Spec

* \`npm install --save-dev @tsconfig/deno`
---
# files, include, exclude

* 셋다 설정이 없으면, 전부다 컴파일
* files
	- 상대 혹은 절대 경로의 리스트 배열이다.
	- exclude 보다 쎄다.
* include, exclude
	- glob 패턴(마치 .gitnore)
	- include
* exclude 보다 약하다.
* *같은걸 사용하면, /ts/ .tsx./ .d.ts 만 include (allowJS)
	
  - exclude
* 설정 안하면 4가지 (node_modules, bower_components, jspm_packages, \<outDir>)를 default 로 제외한다.
* \<outDir>은 항상 제외한다. (include 에 있어도)
---
# compileOptions

## -typeRoots, types
### @ types
* TypeScript 2.0 부터 사용 가능해진 내장 type definition 시스템
* 아무 설정 안하면?
	- node_modules/@types 라는 모든 경로를 찾아서 사용
* typeRoots 를 사용하면?
	- 배열 안에 들어있는 경로들 아래서만 가져온다.
* types 를 사용하면 ?
	- 배열 안의 모듈 혹은 ./node_modules/@types/ 안의 모듈 이름에서 찾아온다.
	- [ ] 빈 배열을 넣는다는건 이 시스템을 이용하지 않겠다는 것 이다.
* typeRoots 와 types 를 같이 사용하지 않는다.
---
# compileOptions
## -target 과 lib

* target
	- 빌드의  결과물을 어떤 버전으로 할 것이냐
	- 지정하지 않으면 es3 이다.
* lib
	- 기본 type definition 라이브러리를 어떤것을 사용할 것이냐
	- lib를 지정하지 않을 때,
* target 이 'es3' 이고, 디폴트로 lib.d.ts 를 사용한다.
* target 이 'es5' 이면, 디폴트로 dom, es5, scripthost 를 사용한다.
* target 이 'es6' 이면, 디폴트로 dom, es6, dom.iterable, scripthost 를 사용한다
	- lib 를 지정하면 그 lib 배열로만 라이브러리를 사용한다.
* 빈 [ ] => 'no definition found 어쩌구'
---
# compileOptions
  - outDir, outFile, rootDir

---
# compileOptions
## -strict

* Enble all strict type checking options.  
--nolmplicitAny  
--nolmplicitThis  
--strictNullChecks  
--strictFunctionTypes  
--strictPropertyinInitialization  
--strictBindCallApply  
--alwaysStrict
---
# --nolmplicitAny

명시적이지 않게 any 타입을 사용하여, 표현식과 선언에 사용하면, 에러를 발생

* 입스크립트가 추론을 실패한 경우, any 가 맞으면, any 라고 지정하라
* 무것도 쓰지 않으면, 에러를 발생
*  오류를 해결하면, any 라고 지정되어 있지 않은 경우는 any 가 아닌 것이다. (타입 추론이 되었으므로)
---
# --nolmplicitThis

### 명시적이지 않게 any 타입을 사용하여, this 표현식에 사용하면, 에러를 발생합니다.

* 번째 매개변수 자리에 this 를 놓고, this 에 대한 타입을 어떤 것이라도 표현하지 않으면, nolmplicitAny가 오류를 발생시킨다.
* JavaScript 에서는 매개변수에 this 를 대체하여 콜을 하는 용도로도 쓰인다.
* call / apply / bind 와 같이 this 를 대체하여 함수 콜을 하는 용도로도 쓰인다.
* 그래서 this 를 any 로 명시적으로 지정하는 것은 합리적이다. (물론 구체적인 사용처가 있는 경우 타입을 표현하기도 한다.)
* class 에서는 this 를 사용하면서, nolmplicitThis 와 관련한 에러가 나지 않습니다.(당연)
* class 에서 constructor 를 제외한 멤버 함수의 첫번째 매개 변수도 일반 함수와 마찬가지로 this 를 사용할 수 있다.
---
# --strictNullChecks

* strictNullChecks 모드에서는, null 및 undefined 값이 모든 유형의 도메인에 속하지 않으며, 그 자신을 타입으로 가지거나, any 일 경우에만 할당이 가능하다.
* 한가지 예외는 undefined 에 void 할당 가능

* strictNullChecks 를 적용하지 않으면,
	- 모든 타입은 null, undefined 값을 가질 수 있다.
	- string 으로 타입을 지정해도, null 혹은 undefined 값을 할당 할 수 있다는 것이다.
* strictNullChecks 를 적용하지 않고, 어떤 값이 null 과 undefined 를 가진다는 것을 암묵적으로 인정하고
계속 사용하다 보면, 정확히 어떤 타입이 오는지를 개발자 스스로가 간과할 수 있다.
* 정말로 null 과 undefined 를 가질 수있는 경우, 해방 값을 조건부로 제외하고 사용하는것이 좋다.
* 이 옵션을 켜고 사용하는 경우,
* 사용하려는 함수를 선언할 때부터 매개변수와 리턴 값에 정확한 타입을 지정하려는 노력을 기울여야하고, 기울이게 될것이다.
---
# --strictFunctionTypes

## (Animal -> Greyhound) <: (Dog -> Dog)
* 반환타입은 공변적(covariat)
* 인자 타입은 반공변적(contravariant)
* 그런데 타입스크립트에서 인자 타입은 공변적이면서, 반공변적인게 문제
* 이 문제를 해결하는 옵션이 strictFunctionTypes
* 이 옵션을 켜면, 에러가 안나던걸 에러 나게함.
---
# --strictPropertyinInitialization

### 정의되지 않은 클래스의 속성이 생성자에서 초기화 되었는지 확인한다.
이 옵션을 사용하려면 --strictNullChecks를 사용하도록 설정해야 한다.

* 보통 다른 함수로 이니셜라이즈 하는 경우 (async 함수)
* constructor 에는 async 를 사용할 수 없다.
# --strictBindCallApply
* Function 의 내장 함수인 bind / call / apply 를 사용할 때, 엄격하게 체크하도록 하는 옵션.
* bind 는 해당 함수안에서 사용할 this 와 인자를 성정해주는 역할을 하고, call 과 apply 는 this 와 인자를 설정한 후, 실행까지 한다
* call 과 apply는 인자를 설정하는 방식에서 차이점이 있다.
  - call 은 함수의 인자를 여러 인자의 나열로 넣어서 사용하고, apply는 모든 인자를 배열 하나로 넣어서 사용한다.