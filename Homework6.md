# Numerical Solutions Software Manual

## Homework 6 

### Problem 1: 

Test on Excercise 7.1, 7.2, and 7.3:
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

Test on Excercise 7.1, 7.2, and 7.3:
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

### Problem 3: 

Test on Excercise 7.1, 7.2, and 7.3:
```C++
int main() {
    cout << "Problem 3: Explicit Euler 10^-2" << endl;
    // step size 10^-2
    // Example 7.1
    cout << Euler(0, 1, 2, .01, "f1", .001, 2000) << endl;
    // Example 7.2
    cout << Euler(0, 1, 2, .01, "f2", .001, 2000) << endl;
    // Example 7.3
    cout << Euler(0, 1, 2, .01, "f3", .001, 2000) << endl << endl;

    cout << "Explicit 10^-1" << endl;
    // step size 10^-1
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

### Problem 4: 

Test on Excercise 7.1, 7.2, and 7.3:
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

### Problem 5: 

Test on Excercise 7.1, 7.2, and 7.3:
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


