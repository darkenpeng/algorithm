# 2016년

```jsx
const DAYS = ['SUN', 'MON', 'TUE', 'WED', 'THU', 'FRI', 'SAT'];

function solution(a, b) {
    return DAYS[new Date(2016, a-1, b).getDay()];
}
```
