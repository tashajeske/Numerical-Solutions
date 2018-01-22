# Numerical Solutions Software Manual

## **Routine Name:** abs_err

**Author:** Nitasha Jeske

**Language:** C++

**Description:** This routine takes the absolute difference of the approximated and actual value to find the absolute error. 

**Input:** The actual value, val, is a double and the approximated value, approx, is also a double. 

**Output:** The program produces a double, which represents the absolute error of the actual and approximated values.

**Code:** 
```C++
double abs_err(double val, double approx){
    return abs(val-approx);
}
```

**Example:**
```C++
#include <cmath>
#include <iostream>
using namespace std;

int main(){
    cout << abs_err(2,2.5);
}
```

**Results:** 
```C++
0.5
```

**Last Modification Date:** Jan. 11, 2018
