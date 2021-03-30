# Closest pair of Points 
## by Jungyoon Kim

분할 정복 알고리즘을 사용하여 최근접 점의 쌍 찾기 시도 했으나 실행에 실패하여 다른 방법으로 구현함.

순서대로 점들 사이의 거리를 계산하고 비교하여 최단 거리가 나오는 값을 찾음.

좌표: {(2,3), (7,1), (0,0), (4,8), (10,6), (-1,-1), (3,5)}

```
import java.util.ArrayList;
import java.util.List;

public class assign {
    public static void main (String[] args) {
        assign a = new assign();
        coor p1 = new coor(2, 3);
        coor p2 = new coor(7, 1);
        coor p3 = new coor(0, 0);
        coor p4 = new coor(4, 8);
        coor p5 = new coor(10, 6);
        coor p6 = new coor(-1,-1);
        coor p7 = new coor(-3,5);
        List<coor> list = new ArrayList<>();     
        list.add(p1); list.add(p2); list.add(p3); list.add(p4); list.add(p5); list.add(p6); list.add(p7);
        List<coor> answer=a.closest(list);
        a.show(answer);
    }

    public static class coor{
        int x,y;
        public coor(int x,int y){
            this.x=x;
            this.y=y;
        }
    }

    public List<coor> closest(List<coor> list){
        List<coor> answer=new ArrayList<>();
        int min=Integer.MAX_VALUE;
        int n=list.size();
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
        } return answer;
}

    public int distance(coor a,coor b){
        int x=a.x-b.x;
        int y=a.y-b.y;
        return x*x+y*y;
    }

    public void show(List<coor> list) {
        System.out.println();
        coor a = list.get(0);
        coor b = list.get(1);
        System.out.println("최근접 쌍: (" + a.x + ", " + a.y + ") & (" + b.x + ", " + b.y + ")");
    }
}
```

===> 최근접 쌍: (0,0) & (-1,-1)
