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
  constructor(a: any, b: any): void;
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
  constructor(): void;
}
```