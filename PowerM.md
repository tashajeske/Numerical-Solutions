# Numerical Solutions Software Manual

## **Routine Name:** PowerM

**Author:** Nitasha Jeske

**Language:** C++

**Description:** The power method approximates the largest (in absolute value) eigenvalue and the corresponding eigenvector of the matrix.

**Input:**  The input is a symmetric positive definite matrix of size n x n (A), an initial guess at the eigenvector of size n (v0), a tolerance, and maximum number of iterations.

**Output:** The algorithm prints the time it takes to run and then returns the largest in absolute value of the eigenvalues of type double. 

**Code:**
```C++
double powerM(Matrix A, Vec v0, double tol, int maxIter){
    chrono::duration<double> time1;
    auto start = chrono::high_resolution_clock::now();
    // initialize y using matrix vector multiplication function
    Vec y=matrixvec(A, v0);
    // initialize variables
    int c=0;
    double error=10*tol;
    double lambdaOld=0.0;
    int n=(int)v0.size();
    Vec x(n,0);
    double lambdaNew=0.0;
    // loop to approximate eigenvalue
    while(tol<error and c<maxIter){
        // calculate 2 norm
        double p=sqrt(dotprod(y,y));
        // normalize vector x
        for(int i=0; i<n; i++){
            x[i]=y[i]/p;
        }
        // update y
        y=matrixvec(A, x);
        // update eigenvalue
        lambdaNew=dotprod(x,y);
        // calculate error
        error=abs(lambdaNew-lambdaOld);
        // update old lambda
        lambdaOld=lambdaNew;
        c ++;
    }
    Vec eigenV=x;
    auto end=chrono::high_resolution_clock::now();
    time1=end-start;
    cout<<time1.count()<<endl;
    return lambdaNew;
}
```

**Example:**
```C++
// function to calculate matrix vector multiplication
Vec matrixvec (Matrix A, Vec v1){
    Vec prod;
    for (int i=0; i<A[0].size(); i++){
        prod.push_back(0);
    }
    for (int i=0; i<A.size(); i++){
        for (int j=0; j< v1.size(); j++){
            prod[i]+=A[i][j]*v1[j];
        }
    }
    return prod;
}

// function to calculate dot product
double dotprod(Vec vec1, Vec vec2){
    double sum=0.0;
    for (int i=0; i<vec1.size(); i++){
        sum=sum+vec1[i]*vec2[i];
    }
    return sum;
}

typedef vector <vector <double>> Matrix;
typedef vector <double> Vec;

int main(){
    // testing power method on hilbert matrix
    int n=1000;
    Matrix Hilbert (n, Vec(n));
    for (int i=0; i<n; i++){
        for (int j=0; j<n; j++){
            Hilbert[i][j]=1.0/(i+j+1);
        }
    }
    Vec v0 (n,1);
    powerM(Hilbert, v0, .01, 100);

    // testing power method on finite difference matrix
    Matrix fDiff(n, Vec(n,0));
    for (int i=0; i<n-1; i++){
        fDiff[i][i]=2;
        fDiff[i][i+1]=-1;
        fDiff[i+1][i]=-1;
    }
    fDiff[n-1][n-1]=2;
    powerM(fDiff, v0, .01, 100);
}
```

**Results:**  
```
1.563011
3.963247
```

**Last Modification Date:** Feb. 19, 2017
