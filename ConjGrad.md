# Numerical Solutions Software Manual

## **Routine Name:** ConjGrad

**Author:** Nitasha Jeske

**Language:** C++

**Description:** Conjugate Gradient is an iterative method to solve a linear system of equations, Ax=b. Using the properties of gradients, this algorithm takes a direction from the starting point and continues iterating in an orthogonal direction until a fixed point is reached. It uses the 2 norm to calculate an error, and uses a tolerance or a max number of iterations to determine the fixed point.

**Input:**  The input is a symmetric positive definite matrix of size n x n (A), a resulting vector of size n (b), an initial guess vector of size n (x0), a tolerance, and maximum number of iterations.

**Output:** The algorithm returns a vector of doubles, which is the approximate solution.

**Code:**
```C++
// function to approximate solution to a linear system using conjugate gradient method
Vec ConjGrad(Matrix A,Vec b, Vec x0, float tol, int maxIter){
    // initialize the residual to be b- Ax0 by calling a a vector subtraction function and a matrix vector multiplication function
    Vec r0=vecsub(b, matrixvec(A, x0));
    // initialize delta0 to be r0^Tr0 or the dot product of r0 and r0
    double delta0=dotprod(r0, r0);
    // initialize b_delta to be b^Tb or the dot product of b and b
    float b_delta=dotprod(b,b);
    // initialize counter k
    int k=0;
    // take p0 to be the current residual
    Vec p0=r0;
    // this condition is for the while loop, since it won't be updated in the loop, I will just calculate it once
    double condition=tol*tol*b_delta;
    // while loop to run the iterations until the tolerance or max iter is met
    while(delta0 > condition && k<maxIter){
        // initialize a vctor s_k to be the matrix vector multiplication of A and p0
        Vec s_k=matrixvec(A, p0);
        // initialize alpha_k to be delta0 divided by the dot product of p0 and s_k
        float alpha_k=delta0/dotprod(p0,s_k);
        // new guess will be old guess added to p0 scaled by alpha_k
        Vec x1=vecadd(x0, scavec(p0, alpha_k));
        // calculate new residual
        r0=vecsub(r0, scavec(s_k, alpha_k));
        // initialize new delta to be dot product of new residuals
        double delta1=dotprod(r0, r0);
        // initialize a scalar to be ratio of new/old delta
        float scalar=delta1/delta0;
        // update p0 based on new residual and calculated scalar
        p0=vecadd(r0, scavec(p0, scalar));
        // increase counter
        k++;
        // set old x to be new x
        x0=x1;
        // set old delta to be new delta
        delta0=delta1;
    }
    cout << "k = " << k << endl;
    return x0;
}
```

**Example:**
```C++
typedef vector <vector <double>> Matrix;
typedef vector <double> Vec;

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
double dotprod(vector <double> vec1, vector <double> vec2){
    double sum=0.0;
    for (int i=0; i<vec1.size(); i++){
        sum=sum+vec1[i]*vec2[i];
    }
    return sum;
}

// function to calculate scalar multiplied by a vector
Vec scavec (Vec v1, float a){
    int n=(int)v1.size();
    for (int i=0; i<n;i++){
        v1[i]=v1[i]*a;
    }
    return v1;
}

// function to add two vectors
Vec vecadd (Vec v1, Vec v2){
    for (int i=0; i<v1.size(); i++){
        v1[i]=v1[i]+v2[i];
    }
    return v1;
}

Vec vecsub (Vec v1, Vec v2){
    for (int i=0; i<v1.size(); i++){
        v1[i]=v1[i]-v2[i];
    }
    return v1;
}

int main(){
    int n=1000;
    // initialize a symmetric positive definite matrix
    Matrix A(n, Vec(n));
    for (int i=0; i<n;i++){
        // make the diagonals random but add the number of rows to the matrix to make sure it is diagonally dominant
        A[i][i]=rand()%100/100.0+500;
        for (int j=0; j<i; j++){
            // create random entries for the lower diagonal
            A[i][j]=rand()%100/100.0;
            // set the corresponding transpose entries equal so that it is symmetric
            A[j][i]=A[i][j];
        }
    }
    // initialize a vector b of random numbers between 0 and 1
    Vec b(n);
    for (int i=0; i<n; i++){
        b[i]=rand()%100/100.0;
    }
    // initialize a vector x0 of random numbers between 0 and 1
    Vec x0(n);
    for(int i=0; i<n; i++){
        x0[i]=rand()%100/100.0;
    }
    ConjGrad(A, b, x0, .001, 1000);
}
```

**Results:**  
```
k = 6
```

**Last Modification Date:** Nov. 12, 2017
