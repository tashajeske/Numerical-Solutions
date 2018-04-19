# Numerical Solutions Software Manual

## Homework 6 

### Problem 1: 

Test Explicit Euler on Example 7.1, 7.2, and 7.3:
```C++
int main() {
    cout << "Problem 1: Explicit Euler" << endl;
    // Example 7.1
    cout << Euler(0, 1, 2, .001, "f1", .001, 2000) << endl;
    // Example 7.2
    cout << Euler(0, 1, 2, .001, "f2", .001, 2000) << endl;
    // Example 7.3
    cout << Euler(0, 1, 2, .001, "f3", .001, 2000) << endl << endl;
}
```

Results:
```
Problem 1: Explicit Euler
-0.415692
-0.416163
-1.45252e+76
```


### Problem 2: 

Test Implicit Euler on Example 7.1, 7.2, and 7.3:
```C++
int main() {
    cout << "Problem 2: Implicit Euler" << endl;
    // Example 7.1
    cout << impEuler(0, 1, 2, .001, "f1", "df1", .001, 2000) << endl;
    // Example 7.2
    cout << impEuler(0, 1, 2, .001, "f2", "df2", .001, 2000) << endl;
    // Example 7.3
    cout << impEuler(0, 1, 2, .001, "f3", "df3", .001, 2000) << endl << endl;
}
```

Results:
```
Problem 2: Implicit Euler
-0.416601
-0.420292
-0.833246
```
Implicit Euler is more accurate than Explicit Euler for these specific problems. Explicit Euler provides an approximation to Example 7.3 that has an error of magnitude 10^77. While Implicit is still providing an approximation roughly twice the true value, it is much more accurate than Explicit Euler's method. These example problems show that Implicit Euler's method has a higher accuracy and is more robust/stable. 


### Problem 3: 

Test Explicit Euler with larger step sizes on Example 7.1, 7.2, and 7.3:
```C++
int main() {
    cout << "Problem 3: Explicit Euler 10^-2" << endl;
    // Example 7.1
    cout << Euler(0, 1, 2, .01, "f1", .001, 2000) << endl;
    // Example 7.2
    cout << Euler(0, 1, 2, .01, "f2", .001, 2000) << endl;
    // Example 7.3
    cout << Euler(0, 1, 2, .01, "f3", .001, 2000) << endl << endl;

    cout << "Explicit 10^-1" << endl;
    // Example 7.1
    cout << Euler(0, 1, 2, .1, "f1", .001, 2000) << endl;
    // Example 7.2
    cout << Euler(0, 1, 2, .1, "f2", .001, 2000) << endl;
    // Example 7.3
    cout << Euler(0, 1, 2, .1, "f3", .001, 2000) << endl << endl;
}
```

Results:
```
Problem 3: Explicit Euler 10^-2
-0.411589
-0.416309
-3.82603e+254

Explicit 10^-1
-0.369502
-0.41792
-6.01633e+41
```
The accuracy of Explicit Euler's method goes down as the step size increases. This can likely be assumed for other methods as well, but it is only tested on Explicit Euler as above. We can see that the accuracy of the 10^-2 step size is only slightly less acuracte than a step size of 10^-3, somewhere in the ballpark of magnitude 10^-2. Then, the accuracy further decreases when a step size of 10^-1 is used.


### Problem 4: 

Test Adam-Bashforth with Adam-Moulton corrector on Example 7.1, 7.2, and 7.3:
```C++
int main() {
    cout << "Problem 4: Adam-Bash-Moul 3 " << endl;
    // Example 7.1
    cout << AdamBashMoul3(0, 1, 2, .001, "f1") << endl;
    // Example 7.2
    cout << AdamBashMoul3(0, 1, 2, .001, "f2") << endl;
    // Example 7.3
    cout << AdamBashMoul3(0, 1, 2, .001, "f3") << endl << endl;
}
```

Results:
```
Problem 4: Adam-Bash-Moul 3 
-0.416147
-0.416147
7.69951e+283
```
The accuracy of the predictor-corrector method using Adam-Bashforth and Adam-Moulton methods is more accurate than Implicit or Explicit Euler's for the first two examples (7.1 and 7.2), however, the method does not hold stable for example 7.3. The answer to this example has very low accuracy, magnitude 10^283. So Implicit Euler method remains the most stable thus far, but this predictor-corrector method is the most accurate for the first two examples. 

### Problem 5: 

Test Runge Kutta order 4 on Example 7.1, 7.2, and 7.3:
```C++
int main() {
    cout << "Problem 5: Runge Kutta 4 " << endl;
    // Example 7.1
    cout << RungeKutta4(0, 1, 2, .001, "f1") << endl;
    // Example 7.2
    cout << RungeKutta4(0, 1, 2, .001, "f2") << endl;
    // Example 7.3
    cout << RungeKutta4(0, 1, 2, .001, "f3") << endl << endl;
}
```

Results:
```
Problem 5: Runge Kutta 4 
-0.416146
-0.416147
-0.416147
```
The Runge Kutta order 4 method is the most accurate for all three examples. This problem is stable enough to provide an accurate approximation to example 7.3 unlike the other methods. This is also a fast method to run. It is a fairly simple algebraic calculation for the computer, so the complexity of the code is low. Explicit Euler's has the shortest calculation time, followed by Runge Kutta, and then the predictor corrector method. Lastly is Implicit Euler's method which calls the newton method of approximating roots. For the accuracy Runge Kutta order 4 provides it is certainly worth the minimal difference in the time it takes to compile versus the Explicit Euler method.
