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
