# Numerical Solutions Software Manual

## **Routine Name:** Laplace5

**Author:** Nitasha Jeske

**Language:** C++

**Description:** This routine approximately solves the Laplace equation with non-homogenous solution = sin(x y). This routine first computes the 5-point mesh, and then the matrix and resultant vector b. Then a linear solver is applied to solve for U(x,y). 

**Input:** The inputs are alpha which represents the number of times you divide the grid, and a and b which are the endpoints of the x,y grid.

**Output:** The routine will produce a vector of the values which correspond to U(x,y) or the approximate value to the solution at each of the mesh points. 

**Code:** 
```C++
void Laplace5 (int alpha, int a, int b){
    auto Mesh = comMesh(alpha, a, b);
    Matrix Lap = LapMat9(alpha);
    cout << "Initialized Matrix: " << endl;
    Printm(Lap);
    Vec vb = initb(Mesh);
    cout << "Initialized b: " << endl;
    Print(vb);
    cout << "Solution: " << endl;
    Vec x = lusolve(Lap, vb);
    Print(x);
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

struct point{
    double x;
    double y;
};

vector <vector <point>> comMesh (int alpha, int a, int b){
    vector <vector <point>> Mesh (alpha, vector<point> (alpha));
    double h = (b-a)/alpha;
    for (int i=1; i< alpha; i++){
        for (int j=1; j< alpha; j++){
            Mesh[i][j].x=(a+j*h);
            Mesh[i][j].y=(a+j*h);
        }
    }
    return Mesh;
}

Matrix LapMat5 (int alpha){
    int size= pow(alpha-2, 2);
    Matrix Lap (size, Vec(size, 0));
    for (int i=0; i<size; i++){
        Lap[i][i]=-4;
    }
    for(int i=0; i<size-1; i++){
        if (i%3!=2){
            Lap[i][i+1]=1;
            Lap[i+1][i]=1;
        }
    }
    for (int i=0; i<size-3; i++){
        Lap[i+3][i]=1;
        Lap[i][i+3]=1;
    }
    return Lap;
}

Vec initb (vector <vector <point>> Mesh){
    Vec b;
    for (int i=1; i< Mesh.size() -1; i++){
        for (int j=1; j<Mesh.size()-1; j++){
            b.push_back(sin(Mesh[i][j].x*Mesh[i][j].y));
        }
    }
    return b;
}

void Printm (Matrix A){
    for (auto && e:A){
        for (auto && f:e){
            cout << f << "  " ;
        }
        cout << endl;
    }
}

void Print (Vec v){
    for (int i=0; i<v.size(); i++){
        cout << v[i] << "  " ;
    }
    cout << endl;
}

int main(){
    Laplace5(5,0,1);
}
```

**Results:** 
```C++
Initialized Matrix: 
-4  1  0  1  0  0  0  0  0  
1  -4  1  0  1  0  0  0  0  
0  1  -4  0  0  1  0  0  0  
1  0  0  -4  1  0  1  0  0  
0  1  0  1  -4  1  0  1  0  
0  0  1  0  1  -4  0  0  1  
0  0  0  1  0  0  -4  1  0  
0  0  0  0  1  0  1  -4  1  
0  0  0  0  0  1  0  1  -4  
Initialized b: 
0  0  0  0  0  0  0  0  0  
Solution: 
8.01331e-25  -8.39187e-18  8.01331e-25  -8.39187e-18  -2.77556e-17  -8.39187e-18  8.01331e-25  -8.39187e-18  8.01331e-25  
```

**Last Modification Date:** Feb. 26, 2018