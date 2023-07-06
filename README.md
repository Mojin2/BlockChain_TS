# TypeScript 이용한 BlockChain

TypeScript에대한 전반적인 지식 습득
<br><br>

## 🖥️ 프로젝트 소개

- TypeScript 이용한 BlockChain

### ⏱️ 프로젝트 기간

- 2023.7.01~

### ⚙️ 프로젝트 환경

- **ts-node**

```
npm i -D ts-node // 개발환경에서만 사용, comfile(build)없이 ts파일 실행
```

- **nodemon**

```
npm i nodemon // server auto restart
```

### 🗓️ 프로젝트 진행

- 프로젝트 생성 with TypeScript ✅

# Other tips

## ❗️ Create Project

```
npm init -y
npm install -D typescript

touch tsconfig.json
```

## ❗️ TypeScript

- Type의 명시적 사용

```
let bool : boolean = false;
let num : number[] = [];
```

- Optional(question mark) & readonly

```
type Age = number;
type Player = {
    readeonly name:string,
    age?:Age
}
const player : Player = {
    name:"name"
};
```

- Return value type

```
const playerMaker = (name:string) : Player => ({name})
function playerMaker(name:string) : Player {
    return {
        name
    }
}
```

- Tuple

```
const player:[string,number,boolean] = ["name",12,false];
```

- Unknown

```
let a : unknown;
is (typeof a === "number"){ //타입을 확인하는 절차를 거침
    let b = a + 1;
}
```

- void & never

```
function a : void { //아무것도 return하지 않을때
    console.log("hello")
}
function b : never { // Error컨트롤이나 parameter타입이 2가지 이상일때
    throw new Error("xxxx")
}
function c(name:name|string){
    if (typeof name === "name"){
        name
    } else if (typeof name ==="string"){
        name
    } else {
        name // typeof name === "never"
    }
}
```

- call signature

```
type Add = (a:number,b:number) => number;
const add : Add = (a,b) => a + b
```

- overloading

```
type Add = {
    (a:number,b:number) : number
    (a:number,b:string) : number
}
const add : Add = (a,b) => {
    if (typeof b === "string") return a
    return a+b
}

type Add = {
    (a:number,b:number) : number
    (a:number,b:number,c:number) : number
}
const add : Add = (a,b,c?:number) => {
    if (c) return a+b+c
    return a+b
}
```

- polymorphism (generic)

```
type SuperPrint = {
    <T,M>(arr:T[],b:M) : T
}
function superPrint<T>(arr:T[]){return arr[0]}
const superPrint : SuperPrint = (arr) => arr[0]
superPrint([1,2,3],"x")
```

- class

```
abstract class User {
    constructor(
        private firstName:string,
        protected lastName:string,
        public nickname:string
    ){}
    abstract getNickName():void
    getFullName(){
        return `${this.firstName}`
    }
}

class Player extends User{
    getNickName(){
        console.log(`${this.nickname}`)
    }

}
```

- syntax

```
type Words = {
    [key:string] : string
}
type Color = "red" | "blue" | "green"
```

- interface

```
type User = {
    nickname:string
}
type Player = User & {}

interface User {
    nickname:string
}
interface Player extends User {}
// type은 모든 concrete 및 object
// interface는 object만
```

- interface implements

```
interface User { // class의 형태를 알려주는 interface
    firstName:string,
    lastName:string,
    nickname:string
    getNickName():void
}

class Player implements User{
    constructor( // interface로 상속받은 property들은 public
        public firstName:string,
        public lastName:string,
        public nickName:string
    ){}
    getNickName(){
        console.log(`${this.nickname}`)
    }

}
// interface는 return시에 instance생성 안하고 형식에 맞추어 넣어줌
```

- interface generic

```
interface SStorage<T> {
    [key:string] : T
}
class LocalStorage<T> {
    private storage : SStorage<T> = {}
    set(key:string, value:T){
        this.storage[key] = value
    }
    remove(key:string){
        delete this.storage[key]
    }
    get(key:string):T{
        return this.storage[key]
    }
    clear(){
        this.storage = {}
    }
}
```
