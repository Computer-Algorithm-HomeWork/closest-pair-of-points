# closest-pair-of-points
## 컴퓨터 알고리즘 4주차 팀과제

### 주요 소스코드 설명

**1. 분할정복을 이용한 최근접쌍 찾기**
~~~ Scanner sc = new Scanner(System.in);
        
        int N =sc.nextInt(); // N개의 점 입력
        
        position = new int[N][2]; // position을 이용하여 2차원 배열 할당
        
        double falsemin=0;
        if(min1<=min2) {
            falsemin=min1; firstNod=node11; secondNod=node12;
        }
        else {
            falsemin=min2; firstNod=node21; secondNod=node22;
        } // 평면을 2로 나누어 분할 하고 두 분할 중 최소값을 선정
        
        double realmin=falsemin;
        for(int i=0; i<DivideMed.size()-1;i++){
            for(int j=i+1; j<DivideMed.size();j++){
                int a = DivideMed.get(i);
                int b = DivideMed.get(j);
                double tmp = calDist(a,b);
                if(tmp<realmin) {
                    realmin=tmp; firstNod=a; secondNod=b;
                }
            }
        } // 중앙 부분의 최소값을 선정하여 고려
        
        
        public static double calDist(int a, int b){

        return Math.sqrt(Math.pow(position[a][0]-position[b][0],2)+Math.pow(position[a][1]-position[b][1],2));

    } // 두 점 사이의 거리를 구하는 공식
        
public static double Xmedian(int[] xArray){

        Arrays.sort(xArray);
        double answer=0;

        int size = xArray.length; // 세가지 중 가장 작은 값을 선정하여 중앙값 구함


~~~


**2. 최단거리를 이용한 최근접쌍 찾기**
~~~coor p1 = new coor(2, 3);
        coor p2 = new coor(7, 1);
        coor p3 = new coor(0, 0);
        coor p4 = new coor(4, 8);
        coor p5 = new coor(10, 6);
        coor p6 = new coor(-1,-1);
        coor p7 = new coor(-3,5);     // 임의 좌표 입력
        

for(int i=0;i<n;i++){
            for(int j=i+1;j<n;j++){
                int dist=distance(list.get(i),list.get(j));
                if(min>dist||answer.size()==0){
                    answer.clear();
                    answer.add(list.get(i));
                    answer.add(list.get(j));
                    min=dist;
                }
            }
        } return answer; // 점들 사이의 거리 비교
}
~~~



**3. bluteForce(완전 탐색)를 이용하여 최근접쌍 찾기**
~~~
static int Distance( Point p1, Point p2 )
    {
        return (p1.x-p2.x)*(p1.x-p2.x) + (p1.y-p2.y)*(p1.y-p2.y);
    } // 점과 점 사이의 거리 출력
    int lmin = Integer.MAX_VALUE;
        int h=0;
        for( int i = left; i < right; i++ ) {
            for( int j = i+1; j <= right; j++ ) {
                int d = Distance( p[i], p[j] );
                int l = fpoint4( p[i], p[j] );
                if( lmin > d )
                {
                    lmin = d;
                    h=l;
                }
            }
        }
        return h; // 중앙값 선정
        
        int size = n;
        if( size <= 3 ) {
            System.out.print("(" + bruteForce1(0, n-1) + "," + bruteForce2(0, n-1) + ")");
            System.out.println(", " + "(" + bruteForce3(0, n-1) + "," + bruteForce4(0, n-1) + ")"); // 점 개수 입력
~~~
---
1번 소스코드는 assign.md , 2번 소스코드는 ClosetPair.txt, 3번 소스코드는 closet.md에 구현되어 있습니다.
