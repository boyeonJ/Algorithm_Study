## Chapter 05 DFS/BFS
### 📌 [실전 문제] 음료수 얼려 먹기
```
N * M 크기의 얼음 틀이 있다. 구멍이 뚫려 있는 부분은 0, 칸막이가 존재하는 부분은 1로 표시된다.
구멍이 뚫려 있는 부분끼리 상, 하, 좌, 우로 붙어있는 경우 서로 연결되어있는 것으로 간주한다.
이때 얼음 틀의 모양이 주어졌을 떄 생성되는 총 아이스크림의 개수를 구하는 프로그램을 작성하시오.
다음의 4 * 5 얼음틀 예시에서는 아이스크림이 총 3개 생성된다.
```
#### 보연
```javascript
// 1. array만큼 visit을 만든후 false로 채운다.
// 2. array만큼 돌면서 
//     2-1. array의 값이 0이고
//     2-2. visit이 false라면
//     count ++ 해주고, dfs 호출

// 1. dfs에서 받은 값을 visit ture 해주고
// 2. 상하좌우로 검사한다. 만약 상하좌우에서
//     2-1. array 범위에 들어왔고
//     2-2. array의 값이 0이고
//     2-3. visit이 false라면
//     dfs 호출(count ++ 은 안해줌)

const directions = [[-1,0],[1,0],[0,1],[0,-1]];

const dfs = (curRow, curCol, array, visit) => {
    
    visit[curRow][curCol] = true;    

    for(let [dx, dy] of directions){
        const tempRow = dx + curRow;
        const tempCol = dy + curCol;
        

        if(tempRow >=0 && tempRow < array.length
           && tempCol >=0 && tempCol < array[0].length
           && array[tempRow][tempCol] === 0
           && visit[tempRow][tempCol] === false
          ){
            dfs(tempRow, tempCol, array, visit);
          }
    }
};

const solution = (row, col, arrayInput) => {
    const array = arrayInput.split('\n').map(row => row.split('').map(Number));
    const visit = new Array(row).fill(null).map(()=>new Array(col).fill(false));
    let count = 0;
    
    for(let x=0; x<array.length; x++){
        for(let y=0; y<array[0].length; y++){
            if(array[x][y] === 0 && visit[x][y] === false){
                count++;
                dfs(x, y, array, visit);
            }
        }
    }

    return count;
}

const input = `00000111100000
11111101111110
11011101101110
11011101100000
11011111111111
11011111111100
11000000011111
01111111111111
00000000011111
01111111111000
00011111111000
00000001111000
11111111110011
11100011111111
11100011111111`;

console.log(solution(15,14,input));
```
#### 하은
```javascript

```
#### 희정
```javascript

```

### 📌 [실전 문제] 미로 탈출
#### 보연
```javascript

```
#### 하은
```javascript

```
#### 희정
```javascript

```
