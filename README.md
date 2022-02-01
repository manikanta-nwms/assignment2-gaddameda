# assignment2-gaddameda
# MANIKANTA GADDAMEDA
### McDonald's
McDonald's to near places are lot of supermarkets like **Hy-Vee** and **walmrt** and also other food places kfc and burgerking are at not more 100 meters distance


***
## Path To Nearest Airport from McDonald's maryville
#### MCI airport near to McDonald's maryville
1. Continue to Jefferson Township. Take the I-29 S/US-71 S exit from US-71 S
2. Follow I-29 S to NW 120th St in KCMO. Take exit 13 from I-29 S
3. Drive to Cookingham Dr
4. you reach MCI airport

#### i recomend food items near to McDonald's
* Big Mac®
* Quarter Pounder®* with Cheese.
* Double Quarter Pounder®* with Cheese.
* Quarter Pounder®* with Cheese Deluxe.
* McDouble®

![Mani's photo](https://github.com/manikanta-nwms/assignment2-gaddameda/blob/main/mani.jpg)


***

this table is created for sports and activity there location and price per equipments for that particular sports 

| sport/activity | Location   | Amount      |
| :---           |    :---:   |        ---: |
| Cricket        | hyd        | $80         |
| football       |  kansa     | $100        |
| hockey         | delhi      | $50         |
| baseball       | newyork    | $70         |


***
## Quotes

> “Life is what happens when you’re busy making other plans.” — *John Lennon*

> “Many of life’s failures are people who did not realize how close they were to success when they gave  up.”– *Thomas A. Edison*


***
## Code Fencing

> This optimization for dynamic programming solutions uses the concept of divide and conquer. It is only applicable for the following recurrence:

\text{dp}[i][j] = \min_{k < j}\{dp[i-1][k] + \text{C}[k][j]\}dp[i][j]= 
k<j
min
​
 {dp[i−1][k]+C[k][j]}
\text{min}[i][j] \leq \text{min}[i][j+1]min[i][j]≤min[i][j+1]
\text{min}[i][j] \text{ is the smallest k that gives the optimal answer}min[i][j] is the smallest k that gives the optimal answer
This optimization reduces the time complexity from O(KN^2)O(KN 
2
 ) to O(KN log \ N)O(KNlog N)

<https://jeffreyxiao.me/blog/divide-and-conquer-optimization>

```
int m, n;
vector<long long> dp_before(n), dp_cur(n);

long long C(int i, int j);

// compute dp_cur[l], ... dp_cur[r] (inclusive)
void compute(int l, int r, int optl, int optr) {
    if (l > r)
        return;

    int mid = (l + r) >> 1;
    pair<long long, int> best = {LLONG_MAX, -1};

    for (int k = optl; k <= min(mid, optr); k++) {
        best = min(best, {(k ? dp_before[k - 1] : 0) + C(k, mid), k});
    }

    dp_cur[mid] = best.first;
    int opt = best.second;

    compute(l, mid - 1, optl, opt);
    compute(mid + 1, r, opt, optr);
}

int solve() {
    for (int i = 0; i < n; i++)
        dp_before[i] = C(0, i);

    for (int i = 1; i < m; i++) {
        compute(0, n - 1, 0, n - 1);
        dp_before = dp_cur;
    }

    return dp_before[n - 1];
}
```
<https://cp-algorithms.com/dynamic_programming/divide-and-conquer-dp.html>