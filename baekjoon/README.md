## Contents
* [14501. 퇴사](#14501)
* [14502. 연구소](#14502)
* [14503. 로봇청소기](#14503)
* [14890. 경사로](#14890)
* [15685. 드래곤 커브](#15685)
* [17144. 미세먼지 안녕!](#17144)
* [14888. 연산자 끼워넣기](#14888)
* [17779. 게리맨더링 2](#17779)
* [14889. 스타트와 링크](#14889)
* [14499. 주사위 굴리기](#14499)
* [15686. 치킨 배달](#15686)
* [16234. 인구 이동](#16234)
* [15683. 감시](#15683)
* [14500. 테트로미노](#14500)
* [14891. 톱니바퀴](#14891)
* [1753. 최단경로](#1753)
* [3190. 뱀](#3190)
* [17140. 이차원 배열과 연산](#17140)
* [17837. 새로운 게임 2](#17837)
* [5373. 큐빙](#5373)
* [17281. 야구](#17281)
* [17070. 파이프 옮기기 1](#17070)
* [17406. 배열 돌리기 4](#17406)
* [17136. 색종이 붙이기](#17136)
* [16236. 아기 상어](#16236)
* [16637. 괄호 추가하기](#16637)

<a name="14888"/>

## [14888. 연산자 끼워넣기](https://www.acmicpc.net/problem/14888)
`void make_order()`  
DFS 기반으로 연산자 순열을 만든다. (같은 것을 포함하는 순열)  
현재까지 만든 연산자 순열의 길이인 `k`가 `N-1`이 되면 식을 계산하기 위해 `calc_formula()`를 호출하고 재귀함수를 종료한다. 아직 연산자 순열이 완성되지 않았다면 즉 `k < N-1`인 경우 재귀호출하여 순열을 연장한다. 각각 남은 더하기, 빼기, 곱하기, 나누기 개수를 의미하는 `a`, `s`, `m`, `d`를 차례로 확인해 순열의 `k`번째 자리에 해당 연산자를 넣는다. 단 `k`번째 자리에 같은 연산자를 두 번 이상 넣지 않기 때문에 중복되는 순열은 만들어지지 않는다.  
  
`void calc_formula()`  
완성된 연산자 순열과 입력으로 받은 숫자를 차례로 조합해 식을 계산한다.  
연산자 우선순위 없이 앞에서부터 차례로 계산하여 `tmp_result`에 저장한다. 전역변수인 `max_result`와 `min_result`에 최댓값, 최솟값을 저장한다.  
  
<a name="17779"/>

## [17779. 게리맨더링 2](https://www.acmicpc.net/problem/17779)
`int make_bound()`  
다이아몬드 모양의 5번 선거구 경계를 만든다. 경계는 `x`, `y`, `d1`, `d2`로 결정된다.  
먼저 `0 <= x <= N-3`, `1 <= y <= N-2`를 만족하는 `(x, y)`를 선택할 수 있다. 한 `(x, y)`에 대하여 가능한 최대의 `d1`은 `y`, `d2`는 `N-1-y`이다. 최대의 `d1`은 0열을 향해, 최대의 `d2`는 `N-1`열을 향해 대각선으로 나아가는 것이기 때문이다. 그 다음 `d1`을 1부터 `max_d1`까지 traverse하며 가능한 `d2`를 모두 조합한다. 단 이 때 하단 꼭짓점이 도시 범위를 넘어갈 수 있기 때문에, 하단 꼭짓점의 y좌표가 `N-1`일 때의 `d2`를 구하고 (`y-d1+d2 = N-1`) `max_d2`와 비교해 더 작은 값을 `d2`로 택한다. 이렇게 `x`, `y`, `d1`, `d2`이 결정되면 `calc_area()`를 호출한다. 그리고 리턴된 값 중 최솟값을 찾아 최종 리턴한다.  
<p align="center">
<img src="/baekjoon/img/17779-1.png" alt="17779-1" height="40%" width="40%" align="middle">
</p>
  

`int calc_area()`  
1번에서 5번 선거구의 인구 수를 구하고 최대 인구수와 최소 인구수의 차를 리턴한다.  
1번 선거구의 인구 수를 먼저 구해보자. 다이아몬드에서 1번 선거구 쪽 경계를 이루는 셀에 대하여 위쪽에 있는 셀은 모두 1번 선거구이다. 그림에서 노란색이 칠해져 있는 부분이다. 2번, 3번, 4번도 비슷한 방법으로 생각할 수 있으며 각각 오른쪽, 왼쪽, 아래쪽 셀이다. 그러나 이렇게 구역을 지정해도 남는 부분이 있다. 그림에서 빗금친 부분인데, 이 직사각형 모양을 각각의 선거구에 지정한다. 1번 선거구의 빗금친 부분의 경우 0행부터 `x+d1`행 전까지, 0열부터 `y-d1`열 전까지의 직사각형으로 생각할 수 있다.  
<p align="center">
<img src="/baekjoon/img/17779-2.png" alt="17779-2" height="40%" width="40%" align="middle">
</p>

<a name="14889"/>

## [14889. 스타트와 링크](https://www.acmicpc.net/problem/14889)
`void make_team()`  
`N/2`명으로 구성된 팀을 만든다. **단 반대편 `N/2`명 팀도 자동으로 꾸려지므로 반대편 팀과 중복되지 않는 구성만 만든다.** 이를 위해 0번째 사람은 현재 만들고 있는 팀에 소속되어 있도록 한다. (초기 `mask`값이 1인 이유가 이것이다.)  
`mask`는 팀에 포함된 사람은 1, 포함되지 않은 사람은 0으로 처리된 비트마스크이다. DFS를 이용하여 `N/2`명의 팀을 꾸리고 `calc_diff()`를 호출한다.  

`void calc_diff()`  
인자로 받은 `mask`에 1로 표기된 팀을 스타트팀, 0으로 표기된 팀을 링크팀이라고 생각하고 각 팀의 시너지를 구해 차를 구한다. 링크팀의 시너지를 구하기 위해 `mask`, 스타트팀의 시너지를 구하기 위해 `~mask`를 인자로 하는 `make_pair()`를 각각 호출한다.  

`void make_pair()`  
`org_mask`에 0으로 표기된 팀에서 두 명씩 짝지은 페어들을 모두 구한다. 그리고 그 페어에 대하여 시너지를 더한다.  
예를 들어 `org_mask`(= 초기 `mask`)가 `111000`이었다고 하자. `make_pair()`는 0으로 표기된 팀에서 두 명씩 짝지은 페어를 DFS로 구한다. 예를 들어 `111110`에서 DFS는 리프에 도달하게 되며, 짝지은 페어만 1로 나타내기 위하여 `org_mask`와 `mask`를 XOR 처리한다. 즉 `111000` ^ `111110`은 `000110`이 된다. XOR의 결과에서 페어를 검출하고 시너지에 더해주게 된다. 이처럼 `org_mask`에서 0으로 표기된 팀의 시너지를 구하게 되므로 `calc_diff()`에서 `mask`에 대해 한 번, `~mask`에 대해 한 번 `make_pair()`를 호출한 것이다.  

  
<a name="14499"/>

## [14499. 주사위 굴리기](https://www.acmicpc.net/problem/14499)
`void roll()`  
`move`값에 따라 동서남북 방향으로 이동한 좌표가 바운드를 넘어가지 않는지 확인하고, 바운드 내라면 주사위 전개도를 변경한다. 그리고 주사위 바닥과 주사위가 놓여있는 칸 사이에 값을 복사한다.  
**문제에 주어져있는 전개도 모양을 적극 활용한다.** 주사위가 동서남북 방향으로 이동하면 전개도가 어떻게 변경되는지 그려서 확인한 후 코드화한다. **동서남북 모든 경우에 대하여 주사위 네 면이 서로 교환되는데, 이 때 하나의 변수 `temp`만으로 해결할 수 있다.**  
<p align="center">
<img src="/baekjoon/img/14499.png" alt="14499" height="40%" width="40%" align="middle">
</p>

<a name="15686"/>

## [15686. 치킨 배달](https://www.acmicpc.net/problem/15686)
처음 인풋을 받을 때 집과 치킨집의 좌표를 전역변수 `home`과 `chicken`에 저장했다. 그리고 집의 개수와 치킨집의 개수를 각각 `H`, `C`에 저장했다.  

`void select_chicken()`  
`C`개의 치킨집 중 `M`개의 치킨집을 고른다.  
비트마스크를 이용해 `C` combination `M`을 구했다. 단, 가령 13개의 치킨집 중 8개의 치킨집을 고른다면 5개를 골라 `mask`만 반대로 뒤집어주면 되기 때문에 `reverse` 인자를 두고 `C-M`개를 골라 `mask`를 뒤집을 것인지 그냥 `M`개를 골라 `mask`를 그대로 이용할 것인지를 알 수 있도록 하였다. 이 `reverse`가 있는 버전과 없는 버전을 비교했을 때 백준 저지에서는 4ms로 동일하게 나왔는데 `M`이 최대 13이기 때문에 큰 차이가 없는 것으로 추측된다. `M`이 큰 값이면 차이가 있을 것으로 예상된다. 이 과정을 통해 `mask`를 확정지으면 `calc_city_dist()`를 호출해 해당 `mask`에 대한 도시의 치킨 거리를 구한다.  

`int calc_city_dist()`  
도시의 치킨 거리를 구한다.  
도시의 치킨 거리는 각 집의 치킨 거리의 합과 같다. 그리고 각 집의 치킨 거리는 그 집과 `M`개의 치킨집까지의 치킨 거리의 최솟값과 같다. 따라서 `calc_home_dist()`를 이용해 각 집의 치킨 거리를 구한 다음 그것을 모두 더했다.  


`int calc_home_dist()`  
각 집의 치킨 거리를 구한다.  
`mask`에서 1인 인덱스를 가지는 `chicken`의 치킨집과 `h` 인덱스를 가지는 `home`의 집 사이의 거리를 모두 구해보고 최솟값을 반환하였다. 집과 치킨집 사이의 거리는 `calc_dist()`를 호출하여 계산하였다.  

`int calc_dist()`  
문제의 정의에 따라 두 위치 사이의 거리를 계산하였다.  

<a name="16234"/>

## [16234. 인구 이동](https://www.acmicpc.net/problem/16234)
메인함수에서 `N`, `L`, `R`과 초기의 인구 배열을 `A`에 저장하였다. 그리고 인구 이동은 더 이상 인구 이동이 없을 때까지 (`move_flag`가 `false`일 때까지) 계속된다.  
한 차례의 인구 이동은 연합 번호를 저장하는 `B`와 연합 번호 별 각 나라의 새로운 인구를 저장하는 `C`를 각각 -1과 0으로 `memset()`하는 것 부터 시작한다. 이중 for문으로 직접 초기화하는 것보다 `memset()`을 이용하는 것이 실험 상 10ms 정도 빨랐다. `unite_num`도 0으로, `move_flag`도 `false`로 해준다.  
그리고 이중 for문을 돌면서 아직 연합을 이루지 않은 나라 즉 `B[i][j]`가 `-1`인 나라를 찾아 연합을 이루기 시작한다. `make_unite(i, j, unite_num);`을 호출하며, 이는 `unite_num`에 해당하는 전체 인구수와 나라수를 pair 형태로 반환한다. 만약 `nation`이 한 번이라도 2 이상이면 인구 이동이 일어나므로 `move_flag`를 `true`로 하였다. 연합 번호 별 각 나라의 새로운 인구수를 `C[unite_num]`에 저장하였다. `move_flag`가 `true`인 경우 이 `C`를 이용해 `A`를 바꿔줄 것이기 때문이다. **원래는 `C`를 사용하지 않고 대신 그 자리에 이중 for문을 넣어 연합 번호가 `unite_num`인 나라를 찾아 `people / nation`으로 `A[i][j]`를 바꿔주었었다. 이렇게 하면 최대 `unite_num`번 이중 for문을 돌려야 한다. 그러나 `C`를 이용함으로써 한 번만 이중 for문을 돌리게 하였다.** 한편 `unite_num`은 0부터 1씩 증가하는 숫자이며, 하나의 나라로도 이룰 수 있다고 보았다.  
연합을 모두 이루면 `move_flag`를 확인하였다. `false`인 경우 인구 이동이 일어나지 않으므로 `while(true)`를 `break`하였다. `true`인 경우는 최종 출력값인 `move`를 1 더하고 `B`와 `C`를 이용하여 `A`를 변경하였다. 이 부분이 위에서 강조한 이중 for문을 한 번만 돌리는 부분이다. 연합 번호 별로 그 연합에 속하는 나라의 좌표를 vector에 저장해보기도 했는데, 오히려 시간이 매우 오래 걸렸다.  

`pair<int, int> make_unite(int x, int y, int num)`  
`(x, y)` 나라를 연합 `num`에 할당하고 즉 `B[x][y] = num`으로 하고, `(x, y)`에서 사방으로 연합을 늘릴 수 있는지 확인한다. 연합 번호 `num`의 총 인구수와 나라수를 pair 형태로 반환한다.  
사방으로 연합을 늘릴 수 있는지 확인하는 것은 델타 배열 `dx`와 `dy`를 사용하였다. 그리고 `(x, y)`로 부터 한 칸 이동한 `(temp_x, temp_y)`가 연합을 이루기 적당한지 `valid_unite()`를 호출하여 확인하였다. 연합을 이룰 수 있다면 인구수와 나라수를 업데이트 해주었다.  

`bool valid_unite(int x, int y, int temp_x, int temp_y)`  
`(x, y)`에서 한 칸 확장된 `(temp_x, temp_y)`가 함께 연합을 이룰 수 있는지 확인한다.  
함께 연합을 이룰 수 있는 조건은 세 가지이다. 1) `(temp_x, temp_y)`의 인덱스가 valid하다. 2) `(temp_x, temp_y)`가 이미 다른 연합에 속해있지 않다. 3) `(x, y)`와 `(temp_x, temp_y)`의 인구수 차이가 L 이상 R 이하이다. 이 세 가지 조건을 모두 만족하는 경우에만 `true`를 반환한다.  

<a name="15683"/>

## [15683. 감시](https://www.acmicpc.net/problem/15683)
메인함수에서 `map`에 `N` * `M`의 인풋을 저장했으며, CCTV는 구조체 `CCTV`의 전역 벡터인 `cctvs`에 저장하였다. 구조체 `CCTV`는 CCTV의 위치를 나타내는 `x`, `y`와 몇 번 CCTV인지 나타내는 `num`, CCTV를 90도로 회전한 가짓수 중 하나를 나타내는 `dir`을 멤버변수로 가진다.  

`void DFS(int k)`  
전체 CCTV에 대하여 90도로 회전한 가짓수 중 하나를 결정한다.  
`k`는 현재 새롭게 방향을 지정하려는 CCTV의 인덱스이다. CCTV의 `num`에 따라서 가능한 (회전하여 만들 수 있는) 가짓수가 다르므로 전역에 `possible_dirs`에 미리 그 가짓수를 저장해두었다. `possible_dirs`를 이용해 DFS로 모든 CCTV에 대하여 가짓수를 결정한다. 모두 결정했다면 `surveil()`을 호출한다.  

`void surveil()`  
각 CCTV의 `num`과 `dir`에 따라 오른쪽, 위쪽, 왼쪽, 아래쪽 중 감시하는 방향을 선택해 `surveil_1_dir()`을 호출한다. 단, 그 전에 `map2`에 `map`을 복사한다. 가령 1번 CCTV이고 오른쪽 방향을 감시한다면 `surveil_1_dir(x, y, RIGHT)`를 호출한다. `surveil_1_dir()`은 `map2`에 감시한 부분을 7로 변경한다. 따라서 `map2`에서 사각지대인 0인 부분의 개수를 세서 `min_blind`를 업데이트한다.  

`void surveil_1_dir(int x, int y, int dir)`  
`dir`이 `RIGHT`, `UP`, `LEFT`, `DOWN`이냐에 따라 해당 방향을 감시한다. 단, 벽이 있으면 해당 방향의 감시를 멈추며 CCTV가 있더라도 통과하여 그 부분도 감시한다고 생각한다. 감시한 부분은 `map2`에 7로 변경한다.  

<a name="14500"/>

## [14500. 테트로미노](https://www.acmicpc.net/problem/14500)
5가지 테트로미노를 회전/대칭하여 만들 수 있는 가짓수는 총 19가지이다. 1가지 모양에 대해, 내부 4개의 셀을 델타 배열처럼 표현하였다. 가령 □□□□ 모양이라면 맨 처음 셀을 기준으로 하면 (0, 0), (0, 1), (0, 2), (0, 3)이므로 dx = {0, 0, 0, 0}, dy = {0, 1, 2, 3}처럼 표현하였다. 19가지에 대하 모두 이렇게 표현하여 2차원 배열로 묶은 것이 `dx`와 `dy`이다.  
`N` * `M`의 종이 위 모든 셀을 기준으로 해 다음을 수행하였다.  
19가지의 모양 중 1가지에 대하여  
1) 4개의 셀이 모두 종이 위에 표현될 수 있는가? (인덱스)  
2) 만약 그렇다면 합을 계산하고, 최댓값을 갱신한다.  

<p align="center">
<img src="/baekjoon/img/14500.png" alt="14500" height="40%" width="40%" align="middle">
</p>

<a name="14891"/>

## [14891. 톱니바퀴](https://www.acmicpc.net/problem/14891)
톱니바퀴 정보가 띄어쓰기로 분리되어 있지 않으므로, 한 톱니바퀴에 대하여 스트링으로 받고 하나씩 파싱해 전역 `cogwheel`에 넣어주었다. 회전 정보를 받을 때마다 `rotate_check()`를 호출했다. 단 인풋으로 주어지는 톱니바퀴 번호는 1부터 시작하고, 코드에서는 0부터 시작했으므로 -1 해서 인자로 넘겨주었다.  

`void rotate_check(int cog, int cw)`  
회전시킬 톱니바퀴 번호 `cog`와 회전 방향 `cw`의 pair를 원소로 하는 queue `q`에 적절히 enque하고, enque가 끝나면 deque해가며 `rotate()`를 호출하였다.  
먼저 처음 인자로 들어왔던 `cog`와 `cw`의 페어를 먼저 `q`에 enque하였다. 그리고 `cog`보다 오른쪽 방향에 있는 톱니바퀴를 회전해야 하는지 확인하였다. 회전해야 한다면 회전시킬 톱니바퀴 번호와 직전에 회전시켰던 방향의 반대방향의 페어를 `q`에 enque하였다. 회전하지 않는다면 `break`하여 그 방향의 톱니바퀴는 더 이상 확인하지 않았다. 왼쪽 방향도 마찬가지로 진행하였다. enque 과정이 모두 끝나면 `!q.empty()`할 때까지 하나씩 deque해가며 `rotate()`를 호출해 실제로 회전시켰다.  

`void rotate(int cog, ing cw)`  
`cog`번째 톱니바퀴를 `cw` 방향으로 회전시킨 결과를 전역 `cogwheel`에 적용하였다. 단 회전시킬 때 직전 결과를 덮어쓰지 않도록 주의한다. 틀린 버전은 아래 *실수했던 부분*의 5)를 참고.  

`int calc_score()`  
회전이 모두 끝나고 모든 톱니바퀴에 대하여 12시 방향의 극을 확인하였다. S극이라면 `pow(2, i)`를 `score`에 더해주었다. for문에 간편하게 넣어주기 위해 `pow()`를 활용했다.  

*실수했던 부분*
1) 처음 인풋 받을 때 톱니바퀴 정보가 띄어쓰기로 분리되어 있지 않아서 스트링으로 받고 하나씩 파싱해주어야 했는데, 띄어쓰기로 분리되어 있지 않다는 것 자체를 생각을 못해서 시간을 많이 낭비했다. 스트링으로 한 톱니바퀴의 정보를 받은 다음, 스트링을 traverse 하면서 하나씩 얻어오고 '0'을 빼주는 것까지 해야 한다. 스트링을 파싱하면 char이기 때문이다. 
2) 인풋으로 주어지는 톱니바퀴 번호는 1부터 시작하고, 코드에서는 0부터 시작했으므로 -1 해서 `rotate_check()`의 인자로 넘겨주었어야 하는데 이걸 생각 못하고 그냥 넘겨줬었다.  
3) 양옆 방향 톱니바퀴를 회전해야 하는지 확인하고 회전해야 한다면 톱니바퀴 번호와 방향을 `q`에 enque 해주었는데, 회전 방향이 계속 반대가 되야 한다는 것을 적용해주지 않았었다. (그냥 인풋에 주어진 회전 방향의 반대 방향을 여러 톱니바퀴 회전에 그대로 적용했다.) 문제를 꼼꼼히 읽어야한다!  
4) 주변 톱니바퀴 회전 정보는 enque 해주었는데 막상 자기 자신의 회전 정보를 enque 해주지 않았다. 빼먹는 부분 없이 하자.  
5) `rotate()`에서 반시계 방향 회전은 문제가 없었는데 시계 방향 회전에서 값을 계속 덮어 써서 버그가 있었다. 회전 시 주의해야한다.   
```cpp
// 틀린 버전
for(int i=0; i<7; i++)
    cogwheel[cog][i+1] = cogwheel[cog][i];

// 맞는 버전
for(int i=6; i>=0; i--)
    cogwheel[cog][i+1] = cogwheel[cog][i];
```
6) queue에서 `q.pop()`은 아무것도 반환하지 않는다. 얻어오면서 pop도 하고 싶다면 `q.front()`로 받은 다음 `q.pop()`을 해주어야 한다.  

<a name="1753"/>

## [1753. 최단경로](https://www.acmicpc.net/problem/1753)
다익스트라 알고리즘을 이용해 한 노드에서 모든 노드로의 최단거리를 구한다. 단 `V*V`의 벡터를 잡고 sparse하게 에지 정보를 기록할 경우 메모리 초과가 난다. 따라서 에지의 개수만큼만 저장해 처리한다.  
메인함수에서 `V`, `E`, `K`를 받고 `E`개의 에지 정보를 `vector<vector<pair<int, int>> > edge(V)`에 저장한다. `edge_weight[i]`는 노드 `i`에서 출발하는 모든 에지 정보가 담겨있는 벡터이다. `dijkstra()`를 호출해 노드 `K-1`로부터 모든 노드로의 최단거리를 구하도록 하였다.  
추가) 문제에서 서로 다른 두 노드 사이에 여러 개의 간선이 있을 수 있다고 하여 `vector<unordered_map<int, int> > edge(V)`에 가장 작은 거리를 갖는 간선만 중복되지 않게 저장하였더니, 시간과 메모리 모두 오히려 증가하였다. 상황에 따라 잘 판단해야 할 듯하다.  


`void dijkstra(int V, int S, vector<vector<pair<int, int>> >& edge)`  
`dist`는 `V` 크기의 벡터로, 노드 `S`로부터 각 인덱스번째 노드로의 최단거리를 기록한다. 처음에는 모두 INF로 잡고 `dist[S]`만 0으로 초기화한다. 그리고 방문한 노드를 기록하는 unordered_set `visited`와 priority queue를 min heap으로 이용해 "아직 방문하지 않은 노드"이면서 "현재까지의 최단거리가 (다른 노드에 비해) 짧은 노드"를 계속해서 얻을 수 있도록 하였다. priority queue `pq`에는 pair가 들어가며, 인덱스가 pair.second인 노드의 (현재까지의) 최단거리를 pair.first가 되도록 push 하였다. 인덱스가 first, 최단거리가 second가 아닌 이유는 최단거리에 따라 정렬되어야 하기 때문이다. `pq`에 `(0, S)`의 pair를 넣는 것으로 시작한다. 다음 내용은 `pq`가 비어있을 때까지 반복한다.  
1) `pq.top()`의 first와 second를 각각 `d`, `u`로 받아온 후 pop한다.  
2) 만약 `visited`에 `u`가 있다면 즉 `u`를 이미 방문한 적이 있다면 더 확인할 필요가 없다. continue한다.  
3) `visited`에 `u`를 넣고, 인덱스가 `u`인 노드와 인접한 모든 노드에 대하여 최단거리를 갱신할 수 있는지 확인한다. `u` 노드부터 `u`와 인접한 어떤 노드까지의 길이에 `d`를 더한 값이 현재의 `dist`값보다 작다면 `dist`를 갱신한다. 그리고 `pq`의 pair first, second의 의미에 따라 push한다.  
위의 반복이 끝나면 최단거리를 모두 구한 것이므로 각 노드까지의 최단거리를 출력한다.  

<a name="3190"/>

## [3190. 뱀](https://www.acmicpc.net/problem/3190)
뱀의 머리와 꼬리에서 수정이 일어나므로 cpp의 링크드리스트인 `list`를 사용해보았다. list는 양방향 리스트이고, forward_list가 단방향 리스트이다. 처음 써봤는데 유용했던 것 같고, `deque`도 양방향 수정이 가능하므로 deque로 구현해도 가능했을 것 같다.  
메인에서 사과가 있는 곳을 전역 배열 `apple`에 true로 표시하였고, 뱀의 방향 변환 정보는 앞에서부터 쓰이므로 전역 queue `q`에 push하였다. 뱀은 머리부터 꼬리까지 연결된 list로 보고 처음 있는 곳인 (0, 0)을 `emplace_front()` 해주었다. 그리고 전역 배열 `map`은 현재 시점에 뱀이 존재하는 곳을 true로 한 것이다. 뱀이 벽이나 자기 자신에 부딪힐 때 게임이 종료되므로, 자기 자신에 부딪히는 것을 확인하기 위한 배열이다.  

`int dummy(list<pair<int, int> >& snake, int dir, int cur_time)`  
`snake`는 뱀의 머리부터 꼬리까지 연결되어 있는 list이고, `dir`은 현재 뱀이 바라보고 있는 방향으로 enum에 정의한 `RIGHT`, `DOWN`, `LEFT`, `UP` 중 하나이다. `cur_time`은 현재 시각이다.  
먼저 뱀이 `dir`을 따라 한 칸 더 이동했을 때의 좌표를 `nx`, `ny`로 표현하였다. 이 때 `snake`의 반복자 `begin()`을 사용하였다. 이 `nx`, `ny`가 인덱스를 벗어난다면 벽에 부딪힌 것이므로 게임이 종료되게 하였다. 또는 인덱스를 벗어나지 않지만 `map[nx][ny]`가 true라면 뱀이 자기 자신에 부딪히게 되므로 역시 게임이 종료되게 하였다.  
게임이 종료되지 않는다면 `snake.emplace_front(nx, ny)`로 새로운 머리를 추가해준다. 그리고 `map`도 업데이트해준다. 새로운 머리가 생긴 곳에 사과가 있는지 확인하고, 사과가 있다면 꼬리의 변화 없이 사과만 사라지며 사과가 없다면 `map`에서 꼬리 부분을 false로 바꾸고 `snake`에서도 `pop_back()` 해준다. 여기까지 마치면 `q.front()`를 참고하여 다음 초에서 방향이 전환되는지 확인한다. 단 방향이 전환되건 전환되지 않건 `++cur_time`이 되도록 한다. 그리고 게임이 끝날 때까지 `dummy()`를 재귀 호출한다.  

*실수했던 부분*  
1) 뱀을 하나의 객체 또는 컨테이너로 처음에는 생각하지 못했다. 그냥 `map`과 뱀의 머리 위치, 방향, 길이만 알면 된다고 생각했다. 하지만 꼬리를 자르는 과정은 list나 deque같은 컨테이너가 없으면 할 수 없었다. **처음부터 컨테이너를 잘 선택**하는 게 정말 중요한 것 같다.  
2) 뱀이 방향 전환을 할 때 왼쪽으로 90도 회전하면 (`rot_dir`이 `LEFT`일 때) `dir`이 3->2, 2->1, 1->0, 0->3으로 변경되어야 한다. 그런데 이것을 `dir = (dir - 1) % 4`로 구현하니 틀렸습니다가 나왔다. **mod 연산자 앞에 오는 수가 음수이면 무조건 mod 결과는 음수**인데 -1 % 4가 3이 나올 것이라고 생각한 것이다. 이제는 안 잊어버리겠지?  

<a name="17140"/>

## [17140. 이차원 배열과 연산](https://www.acmicpc.net/problem/17140)
`int r_arith(int r_num, int c_num)`  
R 연산은 각 행에 있는 원소들의 등장 횟수를 카운트하여 그 행의 내용을 바꾼다. 그래서 먼저 unordered_map `m`을 이용해 원소의 등장 횟수를 카운트하였고, 그것을 벡터 `v`로 옮겨 소팅하였다. 단 벡터에 페어가 있는 경우, first를 기준으로 먼저 소팅하기 때문에 등장 횟수를 first에 넣고 숫자를 second에 넣어 따로 compare 함수를 만들지 않고 처리하였다. 그리고 소팅한 내용을 해당 행에 넣고, 그 다음 원소부터 마지막 원소까지 모두 0으로 바꿔주었다. (다른 행에 의해 유효한 열의 개수가 늘어날 경우 그 부분은 0으로 처리하라고 문제에 나와 있기 때문이다.) R 연산을 수행한 다음 유효한 열의 개수는 `max_c_num`에 저장하고 이것을 메인함수로 반환하였다.  

`int c_arith(int r_num, int c_num)`  
`r_arith()`와 처리하는 내용은 비슷하되, column-wise로 접근하여 처리하였다.  

*지긋지긋한 런타임 에러*
이차원 배열을 처리할 때 벡터를 쓰면 좋을 거라 생각했다. resize() 함수로 새로 만들어진 원소를 기본값으로 초기화하는 방법을 쓰면 좋을 거라고 생각했다. (막상 짜보니 column-wise로 접근해야 하는 C 연산을 처리하기 복잡하긴 했다. 그래도 어찌저찌 짜긴 했다.) 그런데.. 테스트 케이스는 돌아가는데 계속 **런타임 에러**가 났다. 사실 왜 런타임 에러가 났는지 이유는 찾지 못했는데, 이차원 배열을 전역 어레이로 처리하니까 아무 문제 없이 맞았습니다가 떴다. 문제에서 이 이차원 배열이 계속 늘어나는 것이 아니고 행 또는 열의 개수가 100개가 넘어가면 자르라고 했으므로 충분히 배열로 처리할 수 있는 문제였다. (사실 이 생각은 처음에 하지 못했다.) **내가 공부한 내용을 써먹을 수 있을 것 같다고 방법을 선택하는 게 아니라 더 깔끔하고 실수하지 않을 방법을 선택해야 한다!!**  

<a name="17837"/>

## [17837. 새로운 게임 2](https://www.acmicpc.net/problem/17837)
전역 배열 `color`는 보드의 색깔을 `WHITE`(0), `RED`(1), `BLUE`(2) 중 하나로 표현한다. 전역 벡터 `board[i][j]`는 (0부터 셀 때) i행 j열에 놓여있는 말을 아래 깔려 있는 것부터 차례로 저장한다. 전역 벡터 `horse_info`는 현재 말들의 위치와 방향을 저장한다. 예를 들어 `horse_info[i]`는 (0부터 셀 때) i번 말의 x좌표, y좌표, 방향을 `Horse` 라는 구조체 안에서 저장한다.  
메인 함수에서는 인풋을 받으며 초기의 `board`와 `horse_info`를 저장한다. 그리고 `turn()`을 whlie문 아래에서 호출하는데, 이 `turn()`의 반환값이 false일 때 이 while문은 break 된다. `turn()`의 반환값이 false인 경우는 해당 턴을 진행하다가 한 칸에 4개 이상의 말이 겹쳐지게 되어 종료한 경우이다.  
`bool turn()`  
K개의 말을 차례로 움직이며 한 턴을 진행한다. 하나의 말에 대하여 현재의 위치를 `cx`와 `cy`, 이동할 곳의 위치를 `nx`와 `ny`에 저장한다.  

1) `nx`와 `ny`의 인덱스가 밖으로 나가거나 `color[nx][ny]`가 `BLUE`인 경우는 방향을 바꾸고 한 칸 이동한다. 문제에 명시되어 있지 않지만 **바꾼 방향으로 한 칸 이동할 때에도 그 칸의 색깔에 따라 다르게 행동해야 한다.** 따라서 (문제에 나와있는 대로) 이동할 칸이 인덱스 밖으로 나가거나 `BLUE`인 경우만 그 자리에 있도록 하고, 그렇지 않은 경우에는 변경된 `nx`, `ny`에 대하여 다시 행동하도록 해야한다. 따라서 이 경우 **`k--`를 하게 하여 큰 for문을 마치고 `k++`이 되더라도 같은 `k`에 머무를 수 있도록 하였다.**

2) `color[nx][ny]`가 `WHITE`이거나 `RED`인 경우는 `board[cx][cy]`에서 `k`가 있는 곳을 반복자로 찾은 다음, 거기부터 끝까지 `board[nx][ny]`에 emplace_back 하였다. 이 때 `board`와 `horse_info` 모두 올바르게 업데이트 되도록 하였다. 단, `RED`인 경우는 원래 반대의 순서로 emplace_back 되었어야 하므로 다시 `board[nx][ny]`에서 방금 추가한 `k`를 가리키는 반복자를 찾은 다음 거기부터 끝까지 reverse 되게 하였다. **아예 `WHITE`와 `RED`를 따로 처리해 `RED`일 경우 `board[nx][ny]`에 emplace_back 할 때부터 반대의 순서로 넣을 수도 있겠지만, 이 경우 반복자를 관리하기 어렵고 역방향 반복자 등을 사용해야 해 이렇게 처리하였다.** 그리고 `board[nx][ny]`에 emplace_back될 때 `board[nx][ny].size()`가 증가하므로, 이 값이 4 이상이 되면 false를 반환하며 종료하게 하였다. 그렇지 않은 경우에는 true를 반환하며 종료하게 하였다.  

<a name="5373"/>

## [5373. 큐빙](https://www.acmicpc.net/problem/5373)
여러 테스트 케이스를 처리해야 하므로, 전역 상수 배열 `org_cube`에 초기 색깔 세팅을 저장해두고 테스트 케이스 하나를 처리할 때마다 `cube`에 `org_cube` 내용을 저장하는 것부터 시작하였다. 각 큐브의 면의 셀은 그 면을 정면에서 바라볼 때의 순서로 저장하였다. 그리고 한 번 큐브를 돌릴 때마다 `rotate()`를 호출하였다.  

`void rotate(int side, char dir)`  
한 면을 한 번 회전시킬 때 영향을 받는 면은 총 다섯 면이다. 가령 U면을 회전시킨다면 U면의 9개의 셀은 한꺼번에 시계 방향 혹은 반시계 방향으로 회전하며, U면과 접하고 있는 L면, F면, R면, B면에서 각각 3개의 셀이 서로 회전된다. 따라서 1) 자기 자신의 9개의 셀을 회전하는 부분과 2) 접하고 있는 네 면의 3개의 셀을 서로 회전시키는 부분 두 가지로 구성하였다. **어려웠던 점은** 접하는 네 면에서 3개의 셀이 어떤 때는 그 면에서의 행이고 어떤 때는 열일 때가 있다는 것이다. 게다가 3개의 셀을 그 다음 면의 자리에 붙여넣는데 그 순서를 유지해야할 때도 있고 유지하지 않아야 할 때도 있었다. 각 면을 정면에서 바라볼 때의 순서로 유지해야 했기 때문이다. (즉 큐브를 돌려도 셀을 저장하는 시점은 항상 동일해야 했기 때문이다.) 컴팩트하게 예쁘게 짜고 싶었지만 하나의 규칙으로 짜기도 어려웠고 짠다 해도 배열의 차원이 너무 높아지는 등 어려움이 있어 그냥 하드코딩 하였다. 여튼 어려운 시뮬레이션이었다.  

<a name="17281"/>

## [17281. 야구](https://www.acmicpc.net/problem/17281)
`void dfs(unsigned int mask, int k, int prev, int order[])`  
DFS를 이용해 순열을 만든다. 조합과 달리 직전에 선택했던 것(`prev`)보다 앞에 있는 것도 선택할 수 있으므로 포문의 조건에 주의한다. (0부터 셀 때) 0번 선수는 반드시 (0부터 셀 때) 3번 타자라고 문제에서 주어졌으므로, 1번 선수 ~ 8번 선수의 순서를 만든다. 8명의 순서를 모두 만들면 `baseball()`을 호출하고 리턴되며, 이 상태에서 `order[0]` ~ `order[7]`에 1 ~ 8의 순열이 들어가있고 `order[8]`은 처음과 같이 0이다.  

`void baseball(int order[])`  
타순을 정리하고 `N` 이닝을 진행한다.  
`order`에서 3번째에 0(0번 선수)를 끼워 넣어야 한다. 그런데 `dfs()`에서 다시 `order`를 사용하므로 `order` 자체를 변경하면 안 된다. 따라서 `my_order` 라는 배열을 만들어 타순을 정리하였다. 그리고 `N` 이닝을 진행하였다. n루타를 쳤을 때 3루, 2루, 1루를 차례로 확인하여 주자가 있을 경우 n루만큼 진루시켰다. `nth_player`는 현재 몇 번 타자의 차례인지를 의미하며, `my_order[nth_player]`를 이용해 몇 번 선수인지를 찾아내었다. 한 이닝이 종료되어도 `nth_player`는 초기화하지 않으며, (0부터 셀 때) 8번 타자 다음에는 다시 0번 타자의 차례이므로 mod 연산자를 이용해 다음 타자를 정했다.  

<a name="17070"/>

## [17070. 파이프 옮기기 1](https://www.acmicpc.net/problem/17070)
전역 상수 배열 `dx`, `dy`에는 `HOR`(가로), `VIR`(세로), `DIA`(오른대각) 방향으로 이동할 때의 x좌표와 y좌표의 이동량을 델타 배열로 나타낸 것이다. 전역 상수 배열 `moving`의 `moving[i]`는 현재 방향이 `i` 방향일 때 다음 방향으로 선택할 수 있는 방향을 저장한다. 예컨대 현재 방향이 가로 방향이라면 `moving[HOR]`를 확인하여 다음 방향으로 `HOR`, `DIA`를 선택할 수 있다. -1은 ragged array가 되지 않도록 넣어준 dummy이며 `moving[i]`의 원소를 확인하다가 -1이 나오면 break 하였다.  

`void dfs(int hx, int hy, int dir)`  
인자 `hx`, `hy`는 현재 파이프의 head 부분 x좌표, y좌표이다. `dir`은 현재 파이프의 방향이다. 따라서 `hx`, `hy`, `dir`을 이용하여 현재 파이프의 tail 부분의 좌표를 알아낼 수 있으며, 이것은 곧 이동 후 파이프의 head 부분 좌표와 같다. (현재 tail 자리에 다음 head가 오는 식이다.) 따라서 그 좌표를 `next_hx`, `next_hy`로 두었다. 그리고 `moving[dir]`을 traverse 하면서 다음 이동 방향 `next_dir`을 설정했다. 그러면 다시 `next_hx`, `next_hy`, `next_dir`을 통해 이동 후 파이프의 tail 부분 좌표를 구할 수 있다. 그 좌표를 `next_tx`, `next_ty`로 두었다. 먼저 이 좌표가 인덱스 범위 밖으로 나가거나 벽에 부딪히는 경우 탐색을 멈췄다. 그리고 `next_dir`이 `DIA`일 경우는 추가로 확인해야 할 셀이 두 개 더 있으므로 이를 확인한다. 여기까지 `next_tx`와 `next_ty`를 확인했을 때 문제가 없었다면 (`N-1`, `N-1`)에 도달했는지 확인하고, 도달했다면 전체 방법의 수에 누적하고 탐색을 멈춘다. 도달하지 않았다면 `dfs()`를 재귀호출하여 탐색을 계속한다.  

<a name="17406"/>

## [17406. 배열 돌리기 4](https://www.acmicpc.net/problem/17406)
`void make_order(unsigned int mask, int k, int order[])`  
`K`개의 회전 변환 순서를 순열로 정한다. 순서 하나가 완성되면 그 순서대로 회전 변환을 수행한다. 그러나 이 때 `org_map`을 바로 회전시키면 다음에 만들어진 순서로 회전 변환을 수행할 때 영향을 받으므로, `my_map`이라는 배열을 하나 만들어 `org_map`을 복사하였다. 그리고 `K`개의 회전 변환을 수행하도록 `rotate_square()`를 호출하였다. `sx`와 `sy`는 회전할 사각형의 왼쪽 상단의 x좌표와 y좌표 (start x와 start y) 이다. `j`는 회전할 사각형의 길이보다 1 작은 수로, `sx`와 `sy`에 각각 더하면 `ex`와 `ey`가 된다. `ex`와 `ey`는 회전할 사각형의 오른쪽 하단 x좌표와 y좌표 (end x와 end y)이다. `K`번의 회전이 끝나면 `get_score()`를 호출해 현재 배열의 점수를 구한다. 문제에서는 최소 점수를 구하고자 하므로 전역 변수 `min_score`보다 작은 점수라면 업데이트한다.  

`void rotate_square(int sx, int sy, int n, int my_map[][MAXSIZE])`  
`make_order()` 설명에서 언급한대로 `ex`와 `ey`를 `sx`, `sy`, `n`으로 복구시킨다. 그리고 덮어씌워질 값을 `tmp`에 저장해두고 적절히 회전시킨다. 이 때 for문에서 `sx`, `sy`, `ex`, `ey`가 사용되었다.  

`int get_score(int my_map[][MAXSIZE])`  
문제에서 어떤 배열의 점수는 각 행의 합 중 최소인 것이라고 하였으므로 이대로 점수를 계산한다.  

*기억할 것*
1) 순열을 만들 때 직전에 뭘 선택했는지 저장하는 `prev`는 필요 없다. `prev`가 필요한 건 조합을 만들 때다.  
2) 다차원 배열을 인자로 받을 때는 첫 차원 빼고 모두 명시되어 있어야 한다. 즉 이차원 배열 `my_map`을 인자로 하는 함수에는 `int my_map[][MAXSIZE]`와 같이 명시되어 있어야 한다.  
3) 인자로 받은 배열은 포인터처럼 되기 때문에 원소의 개수를 알 수 없다. 따라서 range-based for문을 사용할 수 없다.  

<a name="17136"/>

## [17136. 색종이 붙이기](https://www.acmicpc.net/problem/17136)
요약: 이것도 완탐^^  

<a name="16236"/>

## [16236. 아기 상어](https://www.acmicpc.net/problem/16236)
아기 상어는 더 이상 먹을 물고기가 없을 때 (즉 자신보다 작은 물고기가 없거나, 작은 물고기가 있어도 닿을 수 없을 때) 까지 먹을 수 있는 물고기를 찾는다. 먹을 수 있는 물고기를 찾는 함수가 `find_fish()`이다. 먹을 수 있는 물고기는 현재 아기 상어의 위치, 사이즈를 저장하는 전역 변수 `shark_x`, `shark_y`, `shark_size`와 전역 배열 `aqua`에 따라 결정한다. `find_fish()`의 첫 번째 반환값이 true 이면 먹을 물고기를 찾았다는 뜻이므로 `shark_x`와 `shark_y`를 업데이트 해주고, `time`에 거리를 더해주고, 해당 물고기를 먹고 나면 비어있게 되므로 `aqua`의 해당 자리를 0으로 업데이트 해준다. 그리고 상어의 크기만큼 물고기 개수를 먹으면 크기가 증가하도록 해주었다.  

`tuple<bool, int, int, int> find_fish()`  
반환값은 순서대로 먹을 수 있는 물고기를 찾았는지, 찾았다면 x좌표와 y좌표, 그리고 거기까지의 거리이다. 이 함수에서는 먼저 아기 상어의 크기보다 작은 물고기의 수를 세어 `small_fish`에 저장한다. `small_fish`가 0이라면 탐색할 필요 없이 첫 번째 반환값을 false 로하여 반환하면 된다. 하지만 1 이상이라면 BFS로 먹을 수 있는 물고기를 찾는다. `q`에는 아기 상어가 네 방향으로 이동하려고 시도할 때, 아기 상어와 크기가 같거나 비어있어서 갈 수 있는 셀에 대한 정보가 담긴다. 이 `q`에서 deque하면서 그 자리에서 다시 BFS 탐색을 진행할 수 있다. `visited`는 `aqua`와 사이즈가 동일한 배열이며, 한 번 방문된 곳을 `true` 처리 한다. `q`에 아기 상어가 갈 수 있는 셀이 들어있으므로 하나씩 deque하면서 네 방향으로 탐색한다. 이 때 인덱스 아웃이 되거나, `visited`에 의해 이미 방문된 곳이거나, `shark_size` 보다 커서 갈 수 없는 곳이라면 다음 방향을 검색하도록 continue 한다. 만약 `shark_size`와  크기가 같거나 빈 공간이라면 `q`에 넣어주고 `visited`도 true 처리해준다. 마지막으로 `shark_size`보다 작은 물고기가 있다면 그 물고기까지의 거리가 현재 아기 상어의 위치에서 먹을 수 있는 물고기까지 거리의 최소이므로 (BFS로 탐색했기 때문) 검사할 마지막 거리인 `last_dist`를 현재 거리 `dist`로 업데이트 해준다. 그리고 작은 물고기가 여러 마리라면 정렬 후 하나를 고를 수 있도록 `v`에 넣어준다. 그리고 `visited`에 true 처리를 한다. 한 번 `last_dist`가 업데이트되고 나면, `q`의 셀의 마지막 int 값인 거리가 `last_dist`인 것까지만 deque하여 탐색한다. 왜냐하면 `last_dist`보다 더 멀리 있는 셀에서 다시 네 방향으로 검색을 해봐야, `last_dist`를 업데이트할 때의 그 물고기가 더 가까이 있기 때문이다. 이것이 BFS의 특징이다. 그렇게 진행해 `v`가 세팅되었다면, `v` 내부의 여러 후보 물고기 중 위에 있는 물고기, 그것도 같다면 왼쪽에 있는 물고기를 선택한다. 그것을 `compare()` 라는 함수에 나타내었다. 이 `compare()` 함수로 sort 하고 나면 맨 첫 번째에 있는 물고기를 반환해주면 된다. 그러나, `small_fish`가 0이 아니어도 실제로 먹을 수 있는 물고기가 없을 수도 있다. `shark_size` 보다는 작지만, 거기까지 가는 길이 막혀있어 도달할 수 없는 경우다. 이런 경우에는 while문을 탈출하면서도 `v`가 비어있기 때문에, 이 경우를 따로 처리해준다. 이 경우는 먹을 수 있는 물고기가 없기 때문에 첫 번째 반환값을 false로 하여 반환한다.  

*기억할 것*  
`v`가 비어있을 수도 있는 경우를 생각하지 못해서 `v`를 sort 할 때 런타임 에러가 났다. **비어있는 컨테이너의 반복자를 사용하려고 하면 런타임 에러가 난다. 기억하자! 그리고 이런 에지 케이스들이 은근히 있으니 잘 찾자.**  

<a name="16637"/>

## [16637. 괄호 추가하기](https://www.acmicpc.net/problem/16637)
처음 인풋을 받을 때 `nums` 라는 전역 배열에 숫자를, `ops` 라는 전역 배열에 연산자를 차례로 넣었다. 그리고 괄호가 시작될 수 있는 곳은 (마지막 숫자를 제외하고) 각 숫자의 앞이라고 보았다. 그래서 괄호가 시작되는 곳을 표시하는 배열 `paren`의 사이즈는 숫자 개수보다 1 작게 하였다. `paren`에 들어가는 값은, 해당 인덱스의 자리에 괄호가 없는지 (`EMPTY`==0), 괄호가 시작되었는지 (`START` == 1), 직전에 괄호가 시작되어 괄호를 만들 수 없는 상황인지 (`BLOCKED` == 2) 중 하나이다. `make_parenthesis()` 함수를 이용해 괄호를 만들 수 있는 모든 경우의 수를 만들었다.  

`void make_parenthesis(int prev, bool select, int paren[])`  
인자 `prev`는 직전에 괄호를 만들지 확인한 `paren`의 인덱스이고, `select`는 `paren`의 `prev` 인덱스에 그래서 괄호를 만들었는지 만들지 않았는지를 나타낸다. `sp`는 search point의 약자로, 어디서부터 괄호를 만들지 만들지 않을지 검색하기 시작할지를 나타내는 포인트이다. 만약 직전에 괄호가 만들어졌다면 바로 다음은 괄호를 만들 수 없어 `sp`를 `prev` + 2로 설정하였고, 직전에 괄호를 만들지 않았다면 바로 다음부터 괄호를 만들지 검색할 수 있으므로 `sp`를 `prev` + 1로 설정하였다. 만약 `sp`가 `paren_size` 이상이면 괄호 만들기의 끝에 다다른 것이므로, 만든 괄호에 따라 계산을 해주면 된다. 이 계산은 `calc()` 함수를 호출하여 하였다. 반대로 아직 괄호 만들기의 끝에 다다르지 않았다면 해당 자리에 괄호를 만들고 재귀를 한 번, 괄호를 만들지 않고 재귀를 한 번 호출하였다. 괄호를 만들지 않고 재귀를 호출하기 전에 원래 상태로 되돌렸다. `sp`에 괄호를 만드느냐 만들지 않느냐에 따라 `sp` + 1도 결정될 수 있는데, 결정하기 전 인덱스 아웃이 아닌지 확인해야 한다. (**인덱스를 확인하지 않고 접근하면 경우에 따라 런타임 에러가 발생한다.**)  

`int calc(int paren[])`  
queue `numsQ`에 숫자를, queue `opsQ`에 연산자를 차례로 넣은 다음 하나씩 빼면서 계산을 한다. 이 때 괄호가 있는 부분은 `calc_inner()`로 계산하여 한 번에 `numsQ`에 enque 하였다. `numsQ`와 `opsQ`에 enque 하는 것은 `paren[i]`의 값에 따라 달라진다. 만약 `EMPTY` 라면 그 자리의 숫자와 연산자를 각각 `numsQ`와 `opsQ`에 넣어주면 되고, `START` 라면 괄호가 시작된 것이므로 내부를 계산하여 `numsQ`에 넣어주면 되며, `BLOCKED` 라면 직전에 괄호를 계산하고 남은 연산자 하나를 `opsQ`에 넣어주면 된다. 그리고 마지막 숫자가 하나 남아있을 수도 있으므로 잘 처리해준다. `numsQ`와 `opsQ`를 완성하고 나서는 하나씩 빼면서 앞에서부터 계산해준다.  

*기억할 것*  
식의 길이 `N`이 1일 때는 숫자의 개수를 의미하는 `nums_size`가 1이 되고 그에 따라 `paren_size`는 0이 된다. 이 경우에는 `calc()` 에서 `paren[paren_size-1]`을 접근하려고 할 때 런타임 에러가 발생하게 된다. **에지 케이스에서 인덱스 에러가 일어날 수 있으므로 직접 확인하자.** (이를 해결하기 위해 메인에서 따로 예외처리를 함)  