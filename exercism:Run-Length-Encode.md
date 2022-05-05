# [[TS exercism - encoding, decoding]]
## problem
```TS
//input
WWWWWWWWWWWWBWWWWWWWWWWWWBBBWWWWWWWWWWWWWWWWWWWWWWWWB
//output
12WB12W3B24WB
```

```TS
//pipeline
WWWWWWWWWWWWBWWWWWWWWWWWWBBBWWWWWWWWWWWWWWWWWWWWWWWWB
|> [WWWWWWWWWWWW,B,WWWWWWWWWWWW,BBB, WWWWWWWWWWWWWWWWWWWWWWWW, B]
|> [[WWWWWWWWWWWW],[B],[WWWWWWWWWWWW],[BBB], [WWWWWWWWWWWWWWWWWWWWWWWW], [B]]
 => 임의의 arr.map(char=> char.split('').length + char[0])
 => 각배열에 대해 .split('').length + 해당 문자열 한 걸
 // 근데 여기서 만약에 배열의 길이가 1이다? 그러면 length가 공백문자여야함
// arr.map(char=> char.split('').length + char[0])

return arr.map(char => char.length === 1 ? char[0] : char.split('').length + char[0])
.join('')

|> [12W,B,12W,3B, 24W, B] // .join('')
|> 12WB12W3B24WB

12WB12W3B24WB
```

## `의문`
: 어떻게 문자 별로 구분해서 배열에 넣지?
## `생각`
: 정규표현식? 아니면 split에 매개변수를 어떻게 잘?
그러면 input은 공백없이 무조건 upperCase로 들어오는 건 맞음?
: 아님. 공백도 있고 lowerCase도 있음. 그래서 lowerCase=> upperCase변환, 공백문자 " " 지워주어야 함.

```TS
function encode (input : string) : string {
const extractInput = input.toUppserCase().replace(/\s/g,'');  

  //근데 이 알파벳은 변함. 변하는 값= 변수?
  // input으로 들어오는 문자열 'AAAAABBBC'가 아니잠만 반복되는 문자를 기준으로 잘라야하잖아1
  // AAAAAA BBB C 이렇게 잘라야함
const regex = new RegExp('알파벳')

//여기서 input을 쪼개줌 뭐기준으로?알파벳기준으로 ㅇㅇ 여기서 리턴된 거 = arr
return extractInput.split(regex).map(c => c.length === 1 ?
				  c[0]:c.split('').length + c[0])
				  .join('')


}
```
### 삽질 2
뭉탱이로 자르는 게 안된다면?
구분자를 공백문자로 두어서
input.split('')
```TS
//input
WWWWWWWWWWWWBWWWWWWWWWWWWBBBWWWWWWWWWWWWWWWWWWWWWWWWB
WWWWWWWWWWWW,B,WWWWWWWWWWWW,BBB,WWWWWWWWWWWWWWWWWWWWWWWW,B

//output
인덱스를 돌면서 같은 char면 뭉탱이로 묶는다. // string일때도 가능 ㅋㅋ
//char[i] == char[i+1] 이면
//합친다 .join('')

만약 char[i] !== char[i+1]이면
나눈다 => 문자를 추가한다.

input[i] !== input[i+1]
띄어쓰기 input[i] = input[i] + ","

function addSeperator (input : string) : string {

const seperator = ','
	return inputArr.map((i,char) => char[i] !== input ?.char[i]+seperator)

}




12WB12W3B24WB
```
