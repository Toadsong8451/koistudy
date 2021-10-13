# 알고리즘 시험 정리
## 링크
- simple math : 81b3833e2504647f9d794f7d7b9bf341
- 정렬 : 13111c20aee51aeb480ecbd988cd8cc9 (algo#2)
- 탐색 : c3614206a443012045cfd75d2600af2d (algo#2)
- dp : d827f12e35eae370ba9c65b7f6026695 (algo#2)
- 수행 : 487d4c6a324446b3fa45b30cfcee5337, d4dd111a4fd973394238aca5c05bebe3 (2021algo#4)
http://koistudy.net/?mid=Contest_result&ContestID=

## simple math
- 경곽이와 세종이의 대결
    - 0 : n/2+1
    - 1 : y%2==0
    - 3 : a[i]==1, t==1, i!=n-1 -> k++ -> k%2==0
    - 4 : prime에 대한 구분

## 정렬
- O(n^2) 정렬 
- 버블 정렬
    - 2중 for문
    - n번동안 가장 큰 것을 오른쪽으로 민다. 
- 선택 정렬 
    - 자신보다 오른쪽을 모두 배열
- 힙 사용 (최대힙)
    - 부모 : 자식 노드의 키 값보다 적지 않아야 한다. 
- 젖소 정렬
    - 최대로 오름 차순인 수를 찾는다. -> n-r 
- 정렬된 분수 
    - 분수를 만들어서 정렬해주기
- O(nlongn) 정렬 - quick sort
    - 구간을 나누어 정렬하는 것, qsort 함수를 이분탐색처럼 사용

- 정렬 방법
    - 삽입 정렬 (n, n^2, n^2) : 앞과 비교
    - 선택정렬 (n^2, n^2, n^2) : 작은 값을 찾아 앞으로 가져오기
    - 버블정렬 (n^2, n^2, n^2) : 오른쪽으로 한칸씩 서로 비교해가며 가장 큰 값 맨 뒤로
    - 셸 정렬 (n, n^1.5, n^2) : 부분 리스트로 나누어 각각에 대해서 삽입 정렬 -> 간격을 줄이며 계속
    - 퀵 정렬 (nlogn, nlogn, n^2) : 맨 앞 pivot, 그 뒤를 내려오면서 2분할 -> 가운데와 pivot을 바꾸고 이분
    - 힙정렬 (nlogn, nlogn, nlogn) : 최대 힙에 숫자를 추가하는 식으로 진행, 가장 아래에서 출발
    - 병합정렬 (nlogn, nlogn, nlogn) : 2개의 부분 리스트로 나누어 합병 정렬 -> 둘 중 한개에서 작은 것을 뽑는다.
    - https://gmlwjd9405.github.io/tags#sort
        - 가장 정리가 잘 된 곳

## 탐색
- 가무 연습
    - `min(arr[i], cnt);` `cnt-=m;` `ans+=i*m;`
- 젖소 사진
    - 정렬을 하는데 중요한 것은 cmp 함수
    - 두 원소 사이의 관계 5개 중에 과반수인 것으로 판단
- 순차 탐색
- 이분 탐색
- 자벌레 탐색
- upper_bound, lower_bound
- 삼분탐색
- 행렬 탐색 - 대각성분을 이분탐색
- 제자리 멀리뛰기
    - 이분 탐색 (평가 함수 만들기)
- 경비행기 
    - 거리함수를 만들어 평가한다. -> 이분탐색
- 3검 무사
    - `dp[i][j]=dp[i-1][j];`
    - `dp[i][j]=min(dp[i][j], dp[i-2][j-1]+arr[i-1]-arr[i]);`
    - `ans-=dp[n][k];`
- 진격의 거인
    - 이분탐색
    - 평가함수 : `cnt+=arr[i]/x; if(arr[i]%x) cnt++;`
- KOIOI
    - 이분탐색
    - 평가 함수 : `if(str[i]=='I') cntI++; if(str[i]=='K' || (str[i]=='I' && cntI<=numI-x)) a++; else if(str[i]=='O'&& a) a--, b++; else if(str[i]=='I' && b) b--,c++;`

## DP
- Combination 
    - nCr = n-1Cr-1 + n-1Cr
- 젖소 볼링
    -  `dt[x][y] = arr[x][y]+max(f(x+1, y), f(x+1, y+1));`
- 양팔저울의 평형
    - `for(int j=-M; j<=M; j++) {`
            `if(j-arr[i]>=-M) dp[i][j+M] += dp[i-1][j-arr[i]+M];`
            `if(j+arr[i]<=M) dp[i][j+M] += dp[i-1][j+arr[i]+M];`
       `} `
- 거스름돈
    - `dp[i]=min(dp[i], dp[i-arr[j]]+1);`
- Money system
    - `dp[j]+=dp[j-arr[i]];`
- 위성 중계 방송
    - `LTS[i]=max(LTS[j]+1, LTS[i]);`
    - LTX[i]의 최댓값
- 동전줍기 large 
    - `if(j==0) dp[i][j] = max(dp[i-1][1], max(dp[i-1][2], dp[i-1][0])); else dp[i][j] = dp[i-1][j-1] + arr[i];`
- 경찰차
    - `dp[x][y]=min(f(n, y)+dist(n, x), f(x, n)+dist(n, y));`
- minimum move
    - `LTS[i]=max(LTS[j]+1, LTS[i]);`
- 돌다리 건너기
    - 3차 dp 
- 라인 월드 1
- 운송용 헬기
    - 2개의 변수로 checking
- 벽장문의 이동
    - `dp[x][y] = min(f(n, y)+ d(n, x), f(x, n) + d(n, y));`
## 수행 평가에서 내는 것
- 세족식
    - (n-k+1)^k 계산
    - 분할 정복 이용
- 똑떨
    - (ㅜ-1)%2

## vjudge 걸린 것
- 소인수분해 L
- 세족식 (http://koistudy.net/?mid=prob_page&NO=2895)
- 경곽이와 세종이의 대결 1 (http://koistudy.net/?mid=prob_page&NO=2670)
- euler phi function

## 암기해야 할 것
- 시간제한, 메모리 제한 해결 방법, 45명 이상이 푼 문제 중 2문제
- A* 휴리스틱 알고리즘 공부하기 (마지막 문제)

## 예상
- 시간 제한 문제 : 정렬 관련
- 메모리 제한 해결 : dp 저장할때 역으로 저장
- 45명 이상 문제 : 세족식, 똑떨, 꿀벌, 경세대1 중 2개
- A*알고리즘(휴리스틱) : 확실 경로 X, h(x)가 제공 -> f(x)를 계산해서 직접 채우는 듯.. 
    - 휴리스틱 함수를 이용하여 추정하여 점수를 매겨 탐색한다. 
    - 휴리스틱 함수 종류 : manhattan distance(거리 차의 절댓값 합), diagonal distance(x, y 차이 중 최대값), euclidean distance(피타고라스 거리), 등