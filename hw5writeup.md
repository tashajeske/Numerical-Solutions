# Numerical Solutions Software Manual

## Homework 5 Question 6 Write Up

Parameters | Analytic | Explicit Euler | Implicit Euler | Runge Kutta 2 | Runge Kutta 4 | Adam-Bash-Moul 3 
------------ | ------------- | ------------- | ------------- | ------------- | ------------- | -------------
alpha=1, lambda=1, t=.5 | 1.64872 | 1.62835 | 1.63635 | 1.64871 | 1.64871 | 1.64872
alpha=2, lambda=-1, t=1.5 | 0.44626 | 0.447377 | 0.454094 | 0.446271 | 0.446266 | 0.44626
alpha=.5, lambda=-100, t=1.5 | 3.58755e-66 | 0 | 7.00649e-46 | 0 | 0 | -2.77456e-16
gamma=0.1, beta=0.0001 , p0=25, t=1.5 | 28.9288 | 28.8988 | 28.9027 | 28.9288 | 28.9288 | 28.9288
gamma=0.1, beta=0.0001 , p0=40000, t=.5 | nan | 13764.8 | 14154.7 | 13787 | 13784.9 | 13783.6

Above is a table of the values produced on the test cases for each of the parameter values. We can see that the Adams-Bashforth method with an Adams-Moulton correction step has the closest approximations overall. For each of the test cases this method produces very close results, it is only slightly less accurate than the Implicit Euler method for the case when lambda is equal to -100. Overall this method is easy to code, seems to be quite robust, and is very accurate. 

The Runge Kutta methods also produce accurate results, with the order 4 Runge Kutta being slightly more accurate than the order 2. Runge Kutta method seem to be quite robust as well, the code is simply equations to implement in a for loop, and thus is easy to code. The accuracy is very high. This is a great method, second only to the Adams-Bashforth and Adams-Moulton correction method. 

The implicit Euler, or backwards Euler method, is more accurate than Explicit Euler method, however the cost for this accuracy is high. The code is more complicated than any of the other methods, since it uses the Newton method to approximate the value of the current iteration. Newton method also requires the derivative of the function. The implicit Euler method does not seem to be as robust as the above mentioned methods either. 

Then there is the Explicit Euler's method, or forward Euler's method. This method is not as accurate as any of the other methods, but it is the most simple and for basic approximations that do not need high orders of accuracy this would be a good method, since the code is so quick and easy to write. 
