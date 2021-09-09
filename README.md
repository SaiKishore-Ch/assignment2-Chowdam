# assignment2-Chowdam

# Sai Kishore Chowdam
###### My favorite place is California
> From Hollywood dreams to Silicon Valley start-ups; from Napa Valley vineyards to miles of free beaches, California is one of the most **beautiful and livable places in America**. Whether you’re climbing the corporate ladder or El Capitan in Yosemite Valley, The Golden State is the place for you.

***

# Directions to California



1. Take a cab to Kansas airport from Maryville.
    1. Book cab in Uber/Tap ride.
    2. book your ticket to California.
2. Once you land in California.
    1. Make a mark of places you would like to visit.
    2. Take a car and visit all your favourite places.
3. Take a seflie and post.


* Cellphone is most important
* Camera
    * lens
    * tripod stand

**[Link to AboutMe.md file](AboutMe.md)**

***

# FOOD RECOMMEDATIONS
The below table has the food recommedations in maryville city. My personal choice would be Mc Chicken which is available in MC Donalds located opposite to AT & T , Coke at Mc Donalds's is simply amazing which is made me feel fresh. For dinner white sauce pasta at A&G is just mouth watering its the chef's recommdation. I would suggest everyone to try these.

| Food/Drinks  | Location | Price   |
|--------------|----------|--------:|
|Mc Chicken    |Mc Donalds|  $1.59  |
|Pasta         |  A & G   |  $ 15   |
|Coke          |Mc Donalds|  $ 1    |
|MilkShake     |   Sonic  |  $ 3    |

***

# Quotes

> "Peace is not only better than war, but infinitely more arduous." *George Bernard Shaw.*

> "When the power of love overcomes the love of power, the world will know peace." *Jimi Hendrix.*

***

# Code Fencing - Geometry Convex hull

> In geometry, the convex hull or convex envelope or convex closure of a shape is the smallest convex set that contains it. The convex hull may be defined either as the intersection of all convex sets containing a given subset of a Euclidean space, or equivalently as the set of all convex combinations of points in the subset. For a bounded subset of the plane, the convex hull may be visualized as the shape enclosed by a rubber band stretched around the subset.

> Convex hulls of open sets are open, and convex hulls of compact sets are compact. Every compact convex set is the convex hull of its extreme points. The convex hull operator is an example of a closure operator, and every antimatroid can be represented by applying this closure operator to finite sets of points. The algorithmic problems of finding the convex hull of a finite set of points in the plane or other low-dimensional Euclidean spaces, and its dual problem of intersecting half-spaces, are fundamental problems of computational geometry. They can be solved in time {\displaystyle O(n\log n)}O(n\log n) for two or three dimensional point sets, and in time matching the worst-case output complexity given by the upper bound theorem in higher dimensions.

Read More Information <https://en.wikipedia.org/wiki/Convex_hull>

```
struct pt {
    double x, y;
};

bool cmp(pt a, pt b) {
    return a.x < b.x || (a.x == b.x && a.y < b.y);
}

bool cw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) < 0;
}

bool ccw(pt a, pt b, pt c) {
    return a.x*(b.y-c.y)+b.x*(c.y-a.y)+c.x*(a.y-b.y) > 0;
}

void convex_hull(vector<pt>& a) {
    if (a.size() == 1)
        return;

    sort(a.begin(), a.end(), &cmp);
    pt p1 = a[0], p2 = a.back();
    vector<pt> up, down;
    up.push_back(p1);
    down.push_back(p1);
    for (int i = 1; i < (int)a.size(); i++) {
        if (i == a.size() - 1 || cw(p1, a[i], p2)) {
            while (up.size() >= 2 && !cw(up[up.size()-2], up[up.size()-1], a[i]))
                up.pop_back();
            up.push_back(a[i]);
        }
        if (i == a.size() - 1 || ccw(p1, a[i], p2)) {
            while(down.size() >= 2 && !ccw(down[down.size()-2], down[down.size()-1], a[i]))
                down.pop_back();
            down.push_back(a[i]);
        }
    }

    a.clear();
    for (int i = 0; i < (int)up.size(); i++)
        a.push_back(up[i]);
    for (int i = down.size() - 2; i > 0; i--)
        a.push_back(down[i]);
}
```
Read More Information <https://cp-algorithms.com/geometry/grahams-scan-convex-hull.html>