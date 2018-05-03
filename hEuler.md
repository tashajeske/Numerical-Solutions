# Numerical Solutions Software Manual

## **Routine Name:** hEuler

**Author:** Nitasha Jeske

**Language:** C++

**Description:** Explicit Euler's method is a way to approximate the solution to the heat equation, a type of parabolic equation. If the initial value of the curve is given, an unkown value on the curve can be estimated using Euler's.

**Input:**  The function takes the initial value (x0, u0), the value at x you want to find, constant k, delta T, the string f corresponding to the heat equation, the tolerance, and maximum number of iterations. 

**Output:** The function outputs a double which represents y, the value of the function at the desired x. 

**Code:**
```C++
double hEuler (double x0, double u0, double x, duble k, double deltat, string f, double tol, int maxIter){
    int n=0;
    while (std::abs(x-x0) > tol && n < maxIter){
        u0=u0+(deltat*func(uxx,k, f));
        x0=x0+deltat;
        n++;
    }
    return u0;
}
```

**Example:**
```C++

double func2(double uxx, double k, string f){
    if (f=="f1") return k*uxx;
    else return 0.0;
}

int main(){
    cout << hEuler(0,1,.5,-2,.01,"f1",.01,1000);

}
```

**Results:**  
```
.64381
```

**Last Modification Date:** May 3, 2018
