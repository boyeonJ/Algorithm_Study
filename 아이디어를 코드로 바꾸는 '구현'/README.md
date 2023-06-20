## Chapter 04 구현
### 아이디어를 코드로 바꾸는 구현
### 📌 [예시 문제] 상하좌우
```
여행가 A는 N x N 크기의 정사각형 공간 위에 서 있다. 이 공간은 1 x 1 크기의 정사각형으로 나누어져 있다.
가장 왼쪽 위 좌표는 (1,1)이며, 가장 오른쪽 아래 좌표는 (N,N)에 해당한다. 여행가 A는 상, 하, 좌, 우 방향으로 이동할 수 있으며,
시작 좌표는 항상 (1,1)이다. 우리 앞에는 여행가 A가 이동할 계획이 적힌 계획서가 놓여있다.

계획서에는 하나의 줄에 띄어쓰기를 기준으로 하여 L, R, U, D 중 하나의 문자가 반복적으로 적혀 있다.
· L : 왼쪽으로 한 칸 이동
· R : 오른쪽으로 한 칸 이동
· U : 위로 한 칸 이동
· D : 아래로 한 칸 이동

이때 여행가 A가 N x N 크기의 정사각형 공간을 벗어나는 움직임은 무시한다. 예를 들어 (1,1)의 위치에서 L혹은 U를 만나면 무시된다.
계획서가 주어졌을 때 여행가 A가 최종적으로 도착할 지점의 좌표를 출력하는 프로그램을 작성하시오.

🌟 일련의 명령에 따라서 개체를 차례대로 이동시킨다는 점에서 **시뮬레이션 유형**으로 분류
```


#### 보연
```javascript
const solution = (number, inputArray) => {
    let x=1, y=1;
    
    for(let value of inputArray){
        let tempX=x;
        let tempY=y;
        
        if(value === 'R') tempY++;
        else if(value === 'L') tempY--;
        else if(value === 'U') tempX--;
        else if(value === 'D') tempX++;
    
        if(tempY > 0 && tempY <= number) y = tempY;
        if(tempX > 0 && tempX <= number) x = tempX;
    }
    
    return `${x} ${y}`   
}

console.log(solution(5,'RRRUDD'));
```
`상수`화 시키기..!
```javascript
const solution = (number, inputArray) => {
    let x=1, y=1;

    let directions = {
        R: [0, 1],
        L: [0, -1],
        D: [1, 0],
        U: [-1, 0],
    }
    
    for(let value of inputArray){
        console.log(value);
        const [dx, dy] = directions[value];
        if(dy+y > 0 && dy+y <= number) y += dy;
        if(dx+x > 0 && dx+x <= number) x += dx;
    }
    
    return `${x} ${y}`   
}

console.log(solution(5,'RRRUDD'));
```
#### 하은
```javascript

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
