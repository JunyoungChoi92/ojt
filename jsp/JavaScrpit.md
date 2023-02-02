# JavaScrpit
## 개요
html 과 css 와 함께 웹의 동작을 구현하는 객체(object)기반의 스크립트 언어.  
주로 웹브라우저에 사용되나 Node.js같은 프레임워크를 사용하면 서버구축도 가능합니다.

## 특징

자바스크립트가 가지고 있는 언어적 특징은 다음과 같습니다.

1. 자바스크립트는 객체 기반의 스크립트 언어입니다.
2. 자바스크립트는 동적이며, 타입을 명시할 필요가 없는 인터프리터 언어입니다.
3. 자바스크립트는 객체 지향형 프로그래밍과 함수형 프로그래밍을 모두 표현할 수 있습니다.

|자바|자바스크립트|
|:---:|:---:|
|컴파일 언어|인터프리터 언어|
|타입 검사 엄격|타입 확인 X|
|클래스 객체지향|프로토타입 객체지향

# ECMA 스크립트
## 요약
1. ECMAScript(=자바스크립트)는 언어이며, ECMA-262 규격을 따른다.
2. 매년 새로운 버전이 배포되고 있으며, 현재 최신판은 ES2020이다.
3. ES6에서 중요한 기능들이 많이 추가 되었습니다 (ex. ES6에서 추가된 기능 - Promise, Class, Arrow function 등).

# Node.js 
## 개요

Node.js는 오픈 소스 JavaScript 엔진인 크롬 V8에 비동기 이벤트 처리 라이브러리인 libuv를 결합한 플랫폼이다. JavaScript로 브라우저 밖에서 서버를 구축하는 등의 코드를 실행할 수 있게 해주는 런타임 환경이다.

## 패키지 매니저

### npm 
- npm = node package manager -> node.js를 위한 패키지 매니저이자, node.js를 위한 오픈소스 생태계이다. 일반적인 경우에는 Node.js를 설치하면 자동으로 설치된다.
### package.json
- 기본적으로는 package.json은 문서다. npm에 패키지를 배포하고 npm registry에 올리기 위해서 반드시 필요한 문서파일이다.
****
- package.json 기본 구성 요소  
{  
  "name": "PROJECT_DIRECTORY",  
  "version": "1.0.0",  
  "description": "",  
  "main": "index.js",  
  "scripts": {  
    "test": "echo \"Error: no test specified\" && exit 1"  
  },  
  "keywords": [],  
  "author": "",  
  "license": "ISC"  
}  
npm을 사용하는데 기본적인 구성요소 자동생성.
****
- 상기의 목록들 보다, 개발 목적이라면 dependencies 체크
  * 해당 패키지, 프로젝트가 어떤 외부 라이브러리에 의존성(dependency)을 가지고 있는지,
프로젝트가 의존하고 있는 패키지를 일괄적으로 관리하기 위한 필드이다.  
{  
 "dependencies": {  
    "hexo": "^5.0.0",  
    "hexo-deployer-git": "^3.0.0",  
    "hexo-generator-archive": "^1.0.0",  
    "hexo-generator-category": "^1.0.0",  
    "hexo-generator-feed": "^3.0.0"  
    // ...  
  }  
}  

  * 사용법  
    사용하고자 하는 패키지를 아래와 같이 다운받으면, dependencies 필드에 자동으로 install한 ‘패키지이름’과 ‘버전’이 기록된다  
    $ npm install (package name)

****
- yarn
  * npm과 동일한 저장소를 쓰기 때문에 yarn import만 해주면 npm에서 yarn으로 쉽게 마이그레이션할 수 있다.다만 yarn의 패키지 링크 알고리즘 상 npm과는 달리 모든 환경에서 동일한 의존성을 보장한다고 한다. 

### module
프로그램을 구성하는 시스템을 기능단위로 구분지어 독립적인 부분으로 처리한 것.  
단순히 코드의 규모를 줄이기 위한 세분화 작업이 아닌, 논리적 기능과 역할을 분리함으로써 structure의 유연성 부여함.
****

## 특징
- 이벤트 기반
  * libuv 라이브러리는 노드의 특성인 이벤트 기반, 논 블로킹 I/O 모델을 구현하고 있다.
  * 이벤트 기반(Event-driven)이란 이벤트가 발생할 때 미리 지정해둔 작업을 수행하는 방식을 의미한다.
- 이벤트 루프
  * 이벤트 루프(event loop)는 여러 이벤트가 동시에 발생했을 때 어떤 순서로 콜백함수를 호출 할지를 이벤트 루프가 판단한다.
- 논 블로킹 I/O
  * 자세하게 풀어서 아야기하면 함수 호출 시 당장 실행하는 것이 아니라(동기→블로킹) 일단 어느 곳에 쌓아 놓고 동시에 요청을 처리하고(비동기→논 블로킹) 요청이 완료된 순서대로처리(스택 이용) 한다는 말이다.
- 싱글 스레드
  * 이벤트 기반, 논 블로킹 모델과 더불어 노드를 설명하는 키워드 중 하나는 싱글 스레드이다.
자바스크립트 코드는 동시에 실행될 수 없는데 그 이유는 노드가 싱글 스레드 기반이기 때문이다. Node.js는 싱글스레드, 논 블로킹 모델로 싱글 스레드가 혼자서 일을 처리하지만 들어오는 요청 순서가 아닌 논 블로킹 방식으로 이전 작업이 완료될 때까지 대기하지 않고 다음 작업을 수행한다.

## 주의점
1. 우리나라에서는 프레임워크로 표현되기도 하는데,[14] Node.js는 JavaScript 엔진인 V8에 스케쥴링 라이브러리(libuv)를 연결한 응용 런타임 플랫폼이라고 볼 수 있기 때문이다.
2. 노드는 기본적으로 오류 핸들링을 안하면 예외발생으로 프로그램이 꺼진다. 따라서 오류 핸들링을 통한 재접속을 하던가 다음 처리가 요청될 때까지 접속 끊김을 명확하게 제어해야한다.
3. Node.js는 단일 프로세스에서 작동하기 때문에 멀티코어를 완전히 사용하려면 코어 갯수만큼의 프로세스를 띄우고 라우터나 로드 밸런서 등으로 요청을 각 프로세스로 분산시켜주어야 한다.
4. 내장 HTTP 서버 라이브러리를 포함하고 있어 웹 서버에서 아파치 등의 별도 소프트웨어 없이 동작하는 것이 가능하며, 이를 통한 웹 서버의 동작에 있어 더 많은 통제에서 벗어나 여러 가지 기능을 가능하게 한다.

