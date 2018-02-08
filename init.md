# Numerical Solutions Software Manual

## **Routine Name:** init

**Author:** Nitasha Jeske

**Language:** C++

**Description:** This routine initializes the information needed for the elliptic ordinary differential equation u"=f(x), x in (a,b) with initial conditions u(a)=ua, and u(b)=ub. 

**Input:** Inputs are a string f that represents the function f(x), doubles a,b, ua, and ub that represent the ends of the interval and the values of u at those points. 

**Output:** The routine will produce a matrix containing 4 vectors. The first vector is the subdiagonal of the coefficient matrix of 2nd derivative, accuracy 1. The second vector is the main diagonal, and the third vector is the super diagonal of the coefficient matrix. The fourth vector is the b vector in the system of linear equations to be solved. 

**Code:** 
```C++
Matrix init (string f, double a, double b, double ua, double ub, int n){
    Matrix A(4, Vec (n-1));
    double h = (b-a)/n;
    for (int i=0; i<n-1;i++){
        A[0][i]=1;
        A[1][i]=-2;
        A[2][i]=1;
    }
    A[3][0]=pow(h,2)*func(f, a+h)-ua;
    A[3][n-2]=pow(h,2)*func(f, a+h*(n-2))-ub;
    for (int i=1; i<n-2;i++){
        A[3][i]=pow(h,2)*func(f, a + (i+1)*(b-a)/n);
    }
    return A;
}
```

**Example:**
```C++
#include <cmath>
#include <iostream>
#include <vector>
using namespace std;

typedef vector <vector <double>> Matrix;
typedef vector <double> Vec;

double func(string f, double x){
    if (f == "f1") {
    double y=sin(3.1415926535*x);
    return y;
    }
    else return 0.0;
}

int main(){
Printm(init ("f1", 0, 1, 2.5, 5.0, 5));
```

**Results:** 
```C++
1  1  1  1  
-2  -2  -2  -2  
1  1  1  1  
-2.47649  0.0380423  0.0380423  -4.96196  
```

**Last Modification Date:** Feb. 7, 2018
