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
```
행복 왕국의 왕실 정원은 체스판과 같은 8 × 8 좌표 평면이다. 왕실 정원의 특정한 한 칸에 나이트가 서있다.
나이트는 매우 충성스러운 신하로서 매일 무술을 연마한다
나이트는 말을 타고 있기 때문에 이동을 할 때는 L자 형태로만 이동할 수 있으며 정원 밖으로는 나갈 수 없다
나이트는 특정 위치에서 다음과 같은 2가지 경우로 이동할 수 있다

수평으로 두 칸 이동한 뒤에 수직으로 한 칸 이동하기
수직으로 두 칸 이동한 뒤에 수평으로 한 칸 이동하기

이처럼 8 × 8 좌표 평면상에서 나이트의 위치가 주어졌을 때 나이트가 이동할 수 있는 경우의 수를 출력하는
프로그램을 작성하라. 왕실의 정원에서 행 위치를 표현할 때는 1부터 8로 표현하며, 열 위치를 표현할 때는
a 부터 h로 표현한다

c2에 있을 때 이동할 수 있는 경우의 수는 6가지이다
a1에 있을 때 이동할 수 있는 경우의 수는 2가지이다
```

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
    //2칸 이동 가능한지 파악
    if(value + 2 <= BOARD_SIZE) checkSecondDeep(value2);
    if(value -2 > 0) checkSecondDeep(value2);
}

const checkSecondDeep = (value) => {
    //1칸 이동 가능한지 파악
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
```현민이는 게임 캐릭터가 맵 안에서 움직이는 시스템을 개발 중이다.
캐릭터가 있는 장소는 1 X 1 크기의 정사각형으로 이뤄진 N X M 크기의 직사각형으로,
각각의 칸은 육지 또는 바다이다. 캐릭터는 동서남북 중 한 곳을 바라본다.

맵의 각 칸은 (A, B)로 나타낼 수 있고,
A는 북쪽으로부터 떨어진 칸의 개수, B는 서쪽으로부터 떨어진 칸의 개수이다.
캐릭터는 상하좌우로 움직일 수 있고, 바다로 되어 있는 공간에는 갈 수 없다.
캐릭터의 움직임을 설정하기 위해 정해 놓은 매뉴얼은 이러하다.

1. 현재 위치에서 현재 방향을 기준으로
왼쪽 방향(반시계 방향으로 90도 회전한 방향)부터 차례대로 갈 곳을 정한다.
2. 캐릭터의 바로 왼쪽 방향에 아직 가보지 않은 칸이 존재한다면, 왼쪽 방향으로 횐전한 다음 왼쪽으로 한 칸을 전진한다.
왼쪽 방향에 가보지 않은 칸이 없다면, 왼쪽 방향으로 회전만 수행하고 1단계로 돌아간다.
3. 만약 네 방향 모두 이미 가본 칸이거나 바다로 되어 있는 칸인 경우에는,
바라보는 방향을 유지한 채로 한 칸 뒤로 가고 1단계로 돌아간다.
단, 이때 뒤쪽 방향이 바다인 칸이라 뒤로 갈 수 없는 경우에는 움직임을 멈춘다.

현민이는 위 과정을 반복적으로 수행하면서 캐릭터의 움직임에 이상이 있는지 테스트하려고 한다. 메뉴얼에 따라 캐릭터를 이동시킨 뒤에, 캐릭터가 방문한 칸의 수를 출력하는 프로그램을 만드시오.
```
#### 보연
```javascript

```
#### 하은
```javascript

```
#### 희정
```javascript

```
