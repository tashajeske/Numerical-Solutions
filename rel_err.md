# Numerical Solutions Software Manual

## **Routine Name:** rel_err

**Author:** Nitasha Jeske

**Language:** C++

**Description:** This routine takes the absolute difference of the approximated and actual value and then divides by the absolute actual value to find the relative error. 

**Input:** The actual value, val, is a double and the approximated value, approx, is also a double. 

**Output:** The program produces a double, which represents the relative error of the actual and approximated values.

**Code:** 
```C++
double rel_err(double val, double approx){
    return abs(val-approx)/abs(val);
}
```

**Example:**
```C++
#include <cmath>
#include <iostream>
using namespace std;

int main(){
    cout << rel_err(2,2.5);
}
```

**Results:** 
```C++
0.25
```

**Last Modification Date:** Jan. 11, 2018
