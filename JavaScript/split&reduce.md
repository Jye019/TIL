# split

문자열을 특정 문자를 기준으로 나눠 배열 형태로 반환한다. 

```js
const str = "one two three"
const arr1 = str.split(' ')
const arr2 = str.split('')
const arr3 = str.split()

// arr1 = ['one', 'two', 'three']
// arr2 = ['o','n','e','t','w','o','t','h','r','e','e']
// arr3 = ['one two three']
```
<br/>  

# reduce

값을 누적하여 하나의 값을 반환한다. 

```js
const arr = [1, 2, 3];
arr.reduce((acc, currentValue) => {
    return acc + currentValue
}, 0);
```
| acc | currentValue |
| --- | --- |
| 0 | 1 |
| 1 | 2 | 
| 3 | 3 | 
| 6 | |

초기값 0에 arr의 값들을 순서대로 누적한 값 `6`이 return 된다. 

```js
const arr = [1, 2, 3]
arr.reduce((acc, currentValue) => {
    return acc + currentValue
});
```
| acc | currentValue |
| --- | --- |
| 1 | 2 | 
| 3 | 3 | 
| 6 | |

초기값이 없으면 arr의 첫번째 index의 값부터 누적한 값이 return 된다.   


<br/>

### cookie parsing 예제

```js
const cookies = 'key1=value1;key2=value2';

const parseCookies = (cookies = '') => {
    cookie.split(';')
          .map( v => v.split('='))
          .map(([k, ...vs]) => [k, vs.join('=')])
          .reduce((acc, [k, v]) => {
              acc[k.trim()] = decodeURIComponent(v);
              return acc;
          }, {});
}
```
| 실행 | 결과 |
| --- | --- |
| .split(;) | ['key1=value1', 'key2=value2'] |
| .map( v => v.split('=')) | [['key1', 'value1'], ['key2', 'value2']] |
| .map(([k, ...vs]) => [k, vs.join('=')]) | [['key1', 'value1'], ['key2', 'value2']] |  


`reduce`의 callback에서 `acc[key.trim()] = decodeURIComponent(v);`는 객체에 동적으로 프로퍼티를 설정하는 것을 의미한다.   
따라서 `reduce`의 결과는 다음과 같다.

| acc | [k, v] | 
| --- | --- |
| {} | ['key1', 'value1'] | 
| { key1 = 'value1'} | ['key2', 'value2'] | 
| { key1 = 'value1', key2 = 'value2'} | |


 <br/>

 ✏ map 함수는 새로운 배열을 return 한다는 것 잊지말자!
 
