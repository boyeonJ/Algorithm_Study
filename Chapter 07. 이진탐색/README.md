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
const findLength = (request, range, target, start, end)=>{
	if (start > end) {
        return end; 
    }

	const mid = Math.floor((start + end)/2);

	let sum = 0;
	
	for(let val of request){
		if(val-range[mid] > 0) sum += val-range[mid];
	}

	if(sum === target) return range[mid];
	else if(sum > target) return findLength(request, range, 6, mid+1, end);
	else return findLength(request, range, 6, start, mid-1);
}

const solution = ()=>{
	const n = 4;
	const m = 6;
	const request = [19, 15, 10, 17].sort((a,b)=>a-b);

	let range = [];

	for(let i=request[0]; i<request[request.length-1]+1; i++){
		range.push(i);
	}	

	findLength(request, range, 6, 0, range.length-1);
}

console.log(solution());
```
#### 하은
```javascript
```
#### 희정
```javascript

```
