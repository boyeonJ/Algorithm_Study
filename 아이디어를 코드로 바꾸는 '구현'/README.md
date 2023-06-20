## Chapter 04 구현
### 아이디어를 코드로 바꾸는 구현
### 📌 [예시 문제] 상하좌우
#### 보연
```javascript
const solution = (number, inputArray) => {
    let x=1, y=1;
    const array = inputArray.split(' ');
    
    for(let value in array){
        const now = array[value];
        let tempX=x;
        let tempY=y;
        if(now === 'R') tempY++;
        else if(now === 'L') tempY--;
        else if(now === 'U') tempX--;
        else if(now === 'D') tempX++;
    
        if(tempY > 0 && tempY <= number) y = tempY;
        if(tempX > 0 && tempX <= number) x = tempX;
    }
    
    return `${x} ${y}`   
}

console.log(solution(5,'R R R U D D'));
```
#### 하은
```javascript
/*
P: 공간의 크기 n, 이동계획 배열 steps
R: 움직인 후 결과 좌표
E: 5/[R,R,R,U,D,D] => [3,4]
P:
1. L,R,U,D가 각각 의미하는 연산 배열. [dx, dy] 형식으로
2. steps 반복문 돌려서 연산

*/

const directions = {
    L: [0, -1],
    R: [0, 1],
    U: [-1, 0],
    D: [1, 0]
};
function solution(n, steps) {
    let res = [1,1];
    
    for(const step of steps) {
        const row = res[0]+ directions[step][0];
        const col = res[1]+ directions[step][1];

        if (row >= 1 && row <= n && col >= 1 && col <= n)
            res = [row, col]
    }
    return res
}
```
#### 희정
```javascript

```

### 📌 [실전 문제] 왕실의 나이트
#### 보연
```javascript
let count = 0;
const BOARD_SIZE = 8;

const solution = (input) => {
    const array = input.split('');
    const x = array[0].charCodeAt(0) - 96;
    const y = Number(array[1]);
    checkFirstDeep(x,y);
    checkFirstDeep(y,x);
    return count;
}

const checkFirstDeep = (value, value2) => {
    if(value + 2 <= BOARD_SIZE) checkSecondDeep(value2);
    if(value -2 > 0) checkSecondDeep(value2);
}

const checkSecondDeep = (value) => {
    if(value+1 <= BOARD_SIZE) count++;
    if(value-1 > 0) count++;
}

console.log(solution('g7'))
```
#### 하은
```javascript
// a-h 중 몇번째 인덱스인지 찾기 위함
const X = ['a', 'b', 'c', 'd', 'e', 'f', 'g','h'];
const steps = [[-2,-1], [-2,1], [-1,-2], [-1,2], [1,-2], [1,2], [2,-1], [2,1]];

function solution(knight) { 
    const [x,y] = [X.indexOf(knight[0])+1, parseInt(knight[1])]
    let result = 0;
    for (const step of steps) {
        const [nextX, nextY] = [x+step[0], y+step[1]];
        if(nextX >= 1 && nextX <=8 && nextY >= 1 && nextY <= 8)
            result++;
    }
    return result;
}
```
#### 희정
```javascript

```

### 📌 [실전 문제] 게임 개발
#### 보연
```javascript

```
#### 하은
```javascript

```
#### 희정
```javascript

```
