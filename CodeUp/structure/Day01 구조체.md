# Week1 구조체 연습


* [3004 데이터 재정렬](#3004-데이터-재정렬)<br>
* [3170 기억력 테스트 9](#3170-기억력-테스트-9)


<br>

# 3004 데이터 재정렬

**문제로 이동** : [Code-Up 3004 데이터 재정렬](https://codeup.kr/problem.php?id=3004)

입력받은 데이터들의 정렬된 인덱스를 입력받은 값 순서로 출력하는 프로그램

<br>

**문제 해결**

- 입력 배열과 정렬 배열을 비교하여 인덱스 출력
- `인덱스와 값을 저장한 2차원 배열 이용`

<br>

**소스코드**

```
num=int(input())
inputArr = list(map(int,input().split()))
temp=[]
for i in range(0,num):
    temp.append([inputArr[i],i])
sortArr=sorted(temp)
for i in range(0,num):
    sortArr[i].append(i)
result = sorted(sortArr, key = lambda x : x[1])
for i in range(0,num):
    print(result[i][2],end=' ')
```

<br>

# 3170 기억력 테스트 9

문제로 이동 : [Code-Up 3170 기억력 테스트 9](https://codeup.kr/problem.php?id=3170)

입력받은 값과 숫자를 이용하여 값 입력시 숫자를 출력하는 프로그램

<br>

**문제 해결**
- dataclass로 struct 생성
- 2차원 배열 이용 (중복 값 처리 문제)
- `딕셔너리 이용`

<br>

**소스코드**

```
wordNum,questNum=map(int,input().split())
question=[]
dictionary={}
for i in range(wordNum):
    word, number=input().split()
    number=int(number)
    if word in dictionary:
        dictionary[word]=dictionary[word]+number
    else:
        dictionary[word]=number

#질문
answer=[]
for i in range(questNum):
    question = input()
    if question in dictionary:
        answer.append(dictionary[question])
    else:
        answer.append(0)

for i in range(questNum):
    print(answer[i])
```