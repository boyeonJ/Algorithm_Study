## Chapter 03 그리디
### 당장 좋은 것만 선택하는 그리디
### 📌 [실전 문제] 큰 수의 법칙
#### 보연
```javascript
const input = '5 8 3\n2 4 5 4 6'; 
const lines = input.split('\n'); 

const firstLine = lines[0]; // 첫 번째 줄
const secondLine = lines[1]; // 두 번째 줄

const [n, m, k] = firstLine.split(' ').map(Number); 
const array = secondLine.split(' ').map(Number).sort((a,b)=>b-a); 
let number = m;
let index = 0;
let count = 0;
let result = 0;

result = ((array[0]*k)+array[1])*(Math.floor(m/(k+1))) + (array[0]*(m%(k+1)));

console.log(result);
```
#### 하은
```javascript

```
#### 희정
```javascript

```

### 📌 [실전 문제] 숫자 카드 게임
#### 보연
```javascript
//각행의 최솟값 가져와서 정렬하기
//정렬한것중 최댓값
const input = '3 3\n3 1 3\n4 1 4\n2 2 2';
const lines = input.split('\n');
let array = [];

for(let i=0; i<lines[0][0]; i++){
    array.push(lines[i+1].split(' ').map(Number).sort((a,b)=>a-b)[0]);
}

const result = array.sort((a,b)=>b-a)[0];
console.log(result);
```
#### 하은
```javascript

```
#### 희정
```javascript

```
### 📌 [실전 문제] 1이 될 때까지
#### 보연
```javascript
let input = '28 5'
let [n,k] = input.split(' ').map(Number);

let count=0;

while(n>1){
  if(n%k===0){
    n=n/k;
  }else{
    n--;
  }
 count++;
}

console.log(count)
```
#### 하은
```javascript

```
#### 희정
```javascript

```
