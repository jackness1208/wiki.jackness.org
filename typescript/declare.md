# typescript declare 示例汇总
## function

### simple function
#### origin
```javascript
function a() {}
```
#### declare
```typescript
type a = () => void;
```
### function with staic attribute
#### origin
```javascript
function a(argu01, argu02) {}
a.num = 1;
a.hide = function () {};
```
#### declare
```typescript
interface Ia {
  (argu01: any, argu02: any): void;
  num: number;
  hide(): void;
}
declare const a:Ia;
```

## object
### simple object
#### origin
```javascript
const options = {
  a: 1,
  b: '2',
  c: false
};
```
```typescript
interface IOptions {
  a: number;
  b: string;
  c: boolean;
}
declare const options: IOptions;
```
#### declare


### object like any
#### origin
```javascript
const options = {
  a: 1,
  b: 2,
  c: 3
  // ...
};
```
#### declare
```typescript
declare options = {
  [key: string]: any;
};
```

## class
### simple class
#### origin
```javascript
class a {
  constructor(a, b) {}
  fn1() {}
}
```
#### declare
```typescript
declare class a {
  constructor(a: any, b: any);
  fn1(): void;
}
```

### class with static attribute
#### origin
```javascript
new a();
a.isSupported
```
#### declare
```typescript
declare class a {
  static isSupported: boolean;
  constructor();
}
```

### class 方法 多态
#### origin
```javascript
new a();
a.val() // :string
a.val('abc') // :this
```
#### declare
```typescript
declare class a {
  constructor();
  public val(str: string): this
  public val(): string
}
```
#### typescript
```typescript
class a {
  public txt: string
  constructor() {
    this.txt = ''
  }
  public val(str): this
  public val(): string
  public val(str?: string) {
    if (str) {
      this.txt = str
      return this
    } else {
      return this.txt
    }
  }

}
```

## array
### 指定字段 array
#### origin
```javascript
const arr = [error, res, body];
```
#### declare
```typescript
type arr => [Error | undefined, any, any];
```

## global
### 全局变量 - function
#### origin
```javascript
window.header();
```

#### declare
```typescript
declare global {
  interface Window {
    header(): any;
  }
}
```
### 全局变量 - class
#### origin
```javascript
new hiidoEvent();
```

#### declare
```typescript
declare class IHiidoEvent {
  constructor(id: tring, type: string)
}
declare global {
  interface Window {
    hiidoEvent: typeof IHiidoEvent
  }
}
```