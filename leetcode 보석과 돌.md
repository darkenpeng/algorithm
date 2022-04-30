# 보석과 돌
## 내 풀이

```javascript
// 시간복잡도 n*m
const numJewelsInStones = function (jewels, stones) {
  const charMap = new Map();
  for (const jewel of jewels) {
    for (const stone of stones) {
      if (stone === jewel) charMap.set(jewel, (charMap.get(jewel) ?? 0) + 1);
    }
  }
  return [...charMap.values()].reduce((a, b) => a + b, 0);//쩐다ㅇㅂㅇ
};
```

