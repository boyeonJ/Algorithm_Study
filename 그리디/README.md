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

P: 배열의 크기 N, 숫자가 더해지는 횟수 M, 한 인덱스의 수가 연속해 더해질 수 있는 최대 횟수 K  
R: 배열 N에 큰 수의 법칙을 적용해 만들 수 있는 '가장 큰 수'  
E: N:5 M:8 K:3 / 배열: [2 4 5 4 6] 이 입력되면 46을 출력  
P: 
1. 배열에서 가장 큰 수를 K 번 더한다. 이때 더한 횟수를 누적한다.  
2. 배열에서 두번쨰로 큰 수를 1번 더한다. 더한 횟수를 누적한다.  
3. 더한 횟수가 M이 될때까지 반복한다.

```javascript
function solution(N, M, K, arr) {
    let count = 0;
    let result = 0;
    const sorted = arr.sort((a,b) => b-a); 
    
    while(count < M) {
        for(let i=0; i<K;i++) {
            result += sorted[0];
            count++;
        }
        result += sorted[1];
        count++;
    }
    return result;
}
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

P: NXM 행렬의 N과 M, 카드 배열  
R: 각 행의 최소값 중 가장 큰 값  
E: `3,3, [[3,1,2], [4,1,4], [2,2,2]]`  
P:   
1. 각 행의 최소값을 담는 배열을 만든다.  
2. 그 배열의 최댓값을 구한다.
   
```javascript
function solution(n,m, cards) {
    let mins = []; // 각 카드 행의 최소값을 담는 배열
    
    for(let row of cards) {
        // 각 행 정렬 후 가장 작은 값을 mins에 넣음
        mins.push(Math.min(...row)); 
    }
    
    return Math.max(...mins);
}
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

- P: N, K
- R: N이 1이 될 때까지 1번 혹은 2번의 과정을 수행해야하는 **최소 횟수**
- E: N이 17, K가 4라면 1번의 과정을 한 번 수행하면 N은 16이 됩니다. 이후에 2번의 과정을 두번 수행하면 N은 1이 됩니다. 
결과적으로 이 경우 전체 과정을 실행한 횟수는 3이 됩니다. 이는 N을 1로 만드는 최소 횟수입니다
- P:
1. N/K의 나머지가 0이 아니면 1번 연산을 반복한다.
2. N/K의 나머지가 0이 되면 2번 연산을 반복한다.

```javascript
function solution(N, K) {
  let result = 0;
  let number = N;
    
  while (number % K) {
    number -= 1;
    result += 1;
 }
 
  return result + (Math.log(number) / Math.log(K));
}
```

#### 희정
```javascript

```
