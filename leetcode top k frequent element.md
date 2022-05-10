```Javascript
const topKFrequent = function(nums, k) {

    const numMap = new Map();
    // # counter
    for(const num of nums) {
        numMap.set(num,(numMap.get(num)|| 0) + 1 )
    }
    const numArr = [...numMap.entries()] // [ [ 1, 3 ], [ 2, 2 ], [ 3, 1 ] ]
    return numArr.sort((a,b)=> b[1]-a[1])
                  .map((x)=> x[0])
                  .slice(0,k)
};
```
