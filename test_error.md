# Numerical Solutions Software Manual

**Description:** The code below will test the error routines of the exact solution of the simple elliptic ODE, and the finite difference method. The results show the time to compute, the vector representing the computational solution, the vector representing the solution by hand, and the three vector error norms.

**Input:** Inputs will be the mth derivative and accuracy n, both of type integer.

**Output:** The routine will produce a vector of the coefficients. 

**Testing:**
```C++
#include <cmath>
#include <iostream>
# include <vector>
using namespace std;

typedef vector <vector <double>> Matrix;
typedef vector <double> Vec;

int factorial (int n){
return (n == 1 || n == 0) ? 1 : factorial(n - 1) * n;
}

int main(){
    Vec comp_ans7 = strip(init("f1", 0, 1, 2.5, 5.0, 5));
    cout << endl;
    Print(comp_ans7);
    Vec hand_ans7 (4);
    for (int i=1; i<5; i++){
        hand_ans7[i-1]=2.5+2.5*(i*.2)-sin(3.1415926535*(i*.2))/pow(3.1415926535,2);
    }
    cout << endl;
    Print(hand_ans7);
    cout << endl;
    cout << Verror1(comp_ans7, hand_ans7) << endl;
    cout << Verror2(comp_ans7, hand_ans7) << endl;
    cout << VerrorInf(comp_ans7, hand_ans7) << endl;
}
```

**Results:** 
```C++
1.316e-06

2.93554
3.39459
3.89169
4.42682


2.94044
3.40364
3.90364
4.44044


0.0395264
0.0208408
0.0136233
```

**Last Modification Date:** Feb. 6, 2018
