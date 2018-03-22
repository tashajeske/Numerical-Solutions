# Numerical Solutions Software Manual

## **Routine Name:** Euler

**Author:** Nitasha Jeske

**Language:** C++

**Description:** Euler's method is a way to approximate the value of y in a first order differential equation using a form of numerical integration. If the initial value of the curve is given, an unkown value on the curve can be estimated using Euler's.

**Input:**  The function takes the initial value (x0, y0), the value x you want to find, delta T, the string f corresponding to the dy/dx function, the tolerance, and maximum number of iterations. 

**Output:** The function outputs a double which represents y, the value of the function at the desired x. 

**Code:**
```C++
void Euler (double x0, double y0, double x, double deltat, string f, double tol, int maxIter){
    int n=0;
    while (std::abs(x-x0) > tol && n < maxIter){
        y0=y0+(deltat*func(x0,y0, f));
        x0=x0+deltat;
        n++;
    }
    cout << "The approximate value of y at x0 = " << y0 << endl;
}
```

**Example:**
```C++

double func(double x, double y, string f){
    if (f=="f1") return pow(x,2)+2*y;
    else return 0.0;
}

int main(){
    Euler(0, 2, .5, .1, "f1", .01, 100);
}
```

**Results:**  
```
The approximate value of y at x = 0 is 5.01093
```

**Last Modification Date:** March 19, 2018
