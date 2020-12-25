# Week2 재귀함수


* [3702 파스칼의 삼각형](#3702-파스칼의-삼각형)<br>
* [3733 우박수 길이](#3733-우박수-길이)


<br>

# 3702 파스칼의 삼각형

**문제로 이동** : [Code-Up 3702 파스칼의 삼각형 2](https://codeup.kr/problem.php?id=3702)

회전변환된 파스칼의 삼각형의 r행 c열의 값을 알아내는 프로그램

<br>

**문제 해결**

- 값을 저장하는 배열 생성 (메모이제이션)
- 재귀를 사용하여 r-1행 c열값과 r행 c-1열값을 더하여 저장

<br>

**소스코드**

```
pascal=[[1]*50]
for i in range(50):
    pascal.append([0]*50)
    pascal[i][0]=1
r,c = map(int,input().split())
r-=1; c-=1
def GetPascal (r, c):
    if (pascal[r][c]!=0):
        return pascal[r][c]
    else :
        pascal[r][c]=(GetPascal(r,c-1)+GetPascal(r-1,c))%100000000
        return pascal[r][c]
        
print(GetPascal(r,c))
```

<br>

# 3733 우박수 길이

문제로 이동 : [Code-Up 3733 우박수 길이(3n+1)](https://codeup.kr/problem.php?id=3733)

시작과 마지막을 입력받아 그 두 수 사이 최대 우박수 길이를 출력하는 프로그램

<br>

**문제 해결 방법**
- 저장 배열 생성 (메모이제이션)
- 2의 거듭제곱수의 우박수 길이 저장
- 짝수의 경우 n/2의 우박수 길이 +1
- 홀수의 경우 3n+1의 우박수 길이 +1

<br>

**해결 못한 원인**
 - 함수 호출에서 오류 발생
 - 시간 초과

<br>

**소스코드**

```
start,end=map(int,input().split())
route=[0]*30000000
count=1

route[1]=1
for i in range (2,30000001):
    if (i & i-1==0):
        route[i]=count+1
        count+=1


def GetRoute(num):
    if (route[num]!=0):
        return route[num]

    else:
        if(num%2==0):
            route[num]=1+GetRoute(num/2)
        else:
            route[num]=1+GetRoute(num*3+1)

for i in range(start,end+1):
    GetRoute(i)
    
maxRoute=max(route[start:end+1])
print(maxRoute)
```