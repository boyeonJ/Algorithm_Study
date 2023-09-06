## Chapter 07. 이진탐색
### 📌 [실전 문제] 부품찾기
#### 보연
```javascript
const confirmProduct = (array, target, start, end) => {
    if(start>end) return 'no';
    
    let mid = Math.floor((start + end)/2);
    if(array[mid]===target) return 'yes';
    else if(array[mid]>target){
        return confirmProduct(array, target, start, mid-1);
    }
    else{
        return confirmProduct(array, target, mid+1, end);
    }
}

const solution = () => {
    const N = 5;
    const product = [8,3,7,9,2].sort((a,b)=>a-b);
    const M = 3;
    const request = [5,7,9];
    const resultArray = [];
    
    for(const val of request){
        resultArray.push(confirmProduct(product, val, 0, N-1));
    }

    return resultArray.join(' ');
}
```
#### 하은
```javascript
```
#### 희정
```javascript

```

### 📌 [실전 문제] 떡볶이 떡 만들기
#### 보연
```javascript
```
#### 하은
```javascript
```
#### 희정
```javascript

```