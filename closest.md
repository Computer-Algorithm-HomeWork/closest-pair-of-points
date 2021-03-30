## 202001618 김대호
Point점의 쌍 n개를 입력받아 n이 3이하일 경우 분할하지 않고 계산하여 최소 거리가 출력되고 점 두개를 출력합니다.
3보다 클경우 분할하여 거리를 계산해 출력합니다. (더큰 값에서 점 출력 실패)
ex)n=3 (3,3),(4,5),(6,6)일때
결과 : (3,3),(4,5)  ,3  (거리는 제곱된 상태로 출력합니다.)

,,,

import java.util.*;

public class Cosest {
    static Point p[];
    static Point a[];
    static class Point {
        int x,y;
        Point( int x, int y ) {
            this.x = x;
            this.y = y;
        }
    }

    static int Distance( Point p1, Point p2 )
    {
        return (p1.x-p2.x)*(p1.x-p2.x) + (p1.y-p2.y)*(p1.y-p2.y);
    }

    static int bruteForce( int left, int right ) {
        int min = Integer.MAX_VALUE;
        int h=0;
        for( int i = left; i < right; i++ ) {
            for( int j = i+1; j <= right; j++ ) {
                int d = Distance( p[i], p[j] );
                int l = fpoint1( p[i], p[j] );
                if( min > d )
                {
                    min = d;
                    h=l;
                }
            }
        }
        return h;
    }

    static int bruteForce1( int left, int right ) {
        int min = Integer.MAX_VALUE;
        int h=0;
        for( int i = left; i < right; i++ ) {
            for( int j = i+1; j <= right; j++ ) {
                int d = Distance( p[i], p[j] );
                int l = fpoint1( p[i], p[j] );
                if( min > d )
                {
                    min = d;
                    h=l;
                }
            }
        }
        return h;
    }

    static int bruteForce2( int left, int right ) {
        int lmin = Integer.MAX_VALUE;
        int h=0;
        for( int i = left; i < right; i++ ) {
            for( int j = i+1; j <= right; j++ ) {
                int d = Distance( p[i], p[j] );
                int l = fpoint2( p[i], p[j] );
                if( lmin > d )
                {
                    lmin = d;
                    h=l;
                }
            }
        }
        return h;
    }

    static int bruteForce3( int left, int right ) {
        int qmin = Integer.MAX_VALUE;
        int h=0;
        for( int i = left; i < right; i++ ) {
            for( int j = i+1; j <= right; j++ ) {
                int d = Distance( p[i], p[j] );
                int l = fpoint3( p[i], p[j] );
                if( qmin > d )
                {
                    qmin = d;
                    h=l;
                }
            }
        }
        return h;
    }

    static int bruteForce4( int left, int right ) {
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
        return h;
    }

    static int fpoint1(Point p1, Point p2) {
        int o=p1.x;
        return o;
    }

    static int fpoint2(Point p1, Point p2) {
        int o=p1.y;
        return o;
    }

    static int fpoint3(Point p1, Point p2) {
        int o=p2.x;
        return o;
    }

    static int fpoint4(Point p1, Point p2) {
        int o=p2.y;
        return o;
    }

    static int divCon( int left, int right ) {

        int size = right - left + 1;
        if( size <= 3 )
            return bruteForce( left, right );
        int mid = ( left + right ) / 2;
        int d_s_left = divCon( left, mid );
        int d_s_right = divCon( mid+1, right );

        int d_min = Math.min( d_s_left, d_s_right );

        List<Point> s_mid = new ArrayList<>();
        for( int i = left; i <= right; i++ ) {
            int d_x = p[i].x - p[mid].x;
            if( d_x * d_x < d_min )
                s_mid.add( p[i] );
        }

        Collections.sort( s_mid, ( p1,p2 ) -> p1.y - p2.y );
        int Size = s_mid.size();
        for( int i = 0; i < size-1; i++ ) {
            for( int j = i+1; j < size; j++ ) {
                int d_y = s_mid.get(j).y - s_mid.get(i).y;
                if( d_y * d_y < d_min ) {
                    int d = Distance( s_mid.get(i), s_mid.get(j) );
                    if( d_min > d ) d_min = d;
                }
                else break;
            }
        }
        return d_min;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        p = new Point[n];
        for( int i = 0; i < n; i++ )
            p[i] = new Point( sc.nextInt(), sc.nextInt() );


        Arrays.sort( p, ( p1,p2 ) -> p1.x - p2.x );

        int size = n;
        if( size <= 3 ) {
            System.out.print("(" + bruteForce1(0, n-1) + "," + bruteForce2(0, n-1) + ")");
            System.out.println(", " + "(" + bruteForce3(0, n-1) + "," + bruteForce4(0, n-1) + ")");
        }
        System.out.println( divCon( 0, n-1 ) );
        sc.close();
    }
}
,,,
