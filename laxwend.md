# Numerical Solutions Software Manual

## **Routine Name:** laxwend

**Author:** Nitasha Jeske

**Language:** C++

**Description:** Lax-Wendorff method is a way to approximate the solution to a hyperbolic partial differential equation, which uses a second order temporal discretization of a system of ODEs. This is done using the midpoint method. 

**Input:**  The function takes the constant k, a double a, and double h.

**Output:** The function outputs an approximate solution u(x,t) of the advection equation. 

**Code:**
```C++
Vec laxwend (double k, double a, double h){
    double val = a*k/h;
    u(I) = u(I) -.5*val*u(I+1))-u(I-1))+0.5*pow(val,2)*(u(I-1)-2*u(I)+u(I+1));
    return u(I);
}
```

**Example:**
```C++

int main(){
    laxwend(.1, 2, 1);
}
```

**Results:**  
```
1.38622
```

**Last Modification Date:** May 3, 2018
