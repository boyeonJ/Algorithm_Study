## Chapter 06. 정렬
### 📌 [실전 문제] 위에서 아래로
#### 보연
```javascript
function solution(inputArray){
    return array.sort((a,b)=>b-a).join(" ");
}

console.log(solution([3, 15, 27, 12]));
```
#### 하은
```javascript
function solution(arr) {
    return arr.sort((a,b) => b-a);
}
```
#### 희정
```javascript

```

### 📌 [실전 문제] 성적이 낮은 순서로 학생 출력하기
#### 보연
```javascript
const solution = (num, inputArray) => {
    const array = inputArray.map((value)=>{
        const [name, score] = value.split(" ");
        return {
            name :name,
            score: Number(score)
        }
    })

    return array.sort((a,b)=>{
        if(a.score > b.score) return 1;
        else if(a.score < b.score) return -1;
        else if(a.score === b.score) return 0;
        
    }).map((value)=>value.name).join(" ");

}

console.log(solution(2, ['홍길동 95','이순신 77', '정보연 100']));
```
#### 하은
```javascript
function solution(arr) {
    return arr.sort((a,b) => a.score - b.score);
}
```
#### 희정
```javascript

```
### 📌 [실전 문제] 두 배열의 원소 교체
#### 보연
```javascript

```
#### 하은

- P: 배열 원소 개수 n, 바꿔치기 횟수 k, 배열2개
- R: 최대 k번의 바꿔치기를 해 만들 수 있는 배열a의 합의 최대값
- E:
- P: 
    1. 배열a을 오름차순으로, 배열b를 내림차순으로 정렬한다 
    2. a, b 인덱스 처음부터 k개만큼 바꿔치기를 한다
    3. 배열 a의 합을 구한다
   
```javascript
function solution(n, k, arrA, arrB) {
    let aAsc = arrA.sort((a,b) => a-b);
    let bDesc = arrB.sort((a,b) => b-a);

    for(let i=0;i<k;i++) {
      aAsc[i] = bDesc[i];  
    }
    return aAsc.reduce((a,b)=>a+b);
}
```
#### 희정
```javascript

```
