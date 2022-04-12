# algorithm

```
function solution(n) {
    const startAt = 1; 
    // (자아비판) endNum을 매개변수로 넘기지못해서 아쉬운 풀이
    // 스프레드 연산자로 넘겨서 element 넣고빼는게 자유롭지가 못함
    const rangeArr = [...Array(n).keys()].map(key => key + startAt);
    return rangeArr.find((e)=> (n % e) === 1)
}
```
