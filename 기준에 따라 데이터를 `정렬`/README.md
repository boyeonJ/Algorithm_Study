## Chapter 06. 기준에 따라 데이터를 `정렬`
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

```
#### 희정
```javascript

```
### 📌 [실전 문제] 두 배열의 원소 교체
#### 보연
```javascript

```
#### 하은
```javascript

```
#### 희정
```javascript

```
