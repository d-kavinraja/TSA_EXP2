### Name: Kavinraja D
### Register number: 212222240047
# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
Date:27/2/2024
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
Import necessary libraries (NumPy, Matplotlib)

Load the dataset

Calculate the linear trend values using least square method

Calculate the polynomial trend values using least square method

End the program
### PROGRAM:


## A - LINEAR TREND ESTIMATION
```py
#Trend equation using Linear Equation

import numpy as np
from tabulate import tabulate
x = list(map(int, input("Enter a list of years").split()))
y = list(map(int, input("Enter a list of observation").split()))
# x = [2010, 2012, 2014, 2016, 2018]
# y = [18, 21, 23,27,16]
X = [i - x[len(x)//2] for i in x] 
x2 = [i ** 2 for i in X]
xy = [i * j for i, j in zip(X, y)]

table = [[i, j, k, l, m] for i, j, k, l, m in zip(x, y, X, x2, xy)]

print(tabulate(table, headers=["Year", "Prod", "X=x-2014", "X^2", "xy"], tablefmt="grid"))



n=len(x)
b=(n*sum(xy)-sum(y)*sum(X))/(n*sum(x2)-(sum(X)**2))
a=(sum(y)-b*sum(X))/n
print("a,b",a,b)
l=[]
for i in range(n):
  l.append(a+b*X[i])
print(l)
print("Trend Equation : y=%d+%.2fx"%(a,b))
import matplotlib.pyplot as plt
plt.title("Linear Trend Graph")
plt.xlabel("Year")
plt.ylabel("Production")
plt.plot(x,l)
# print("Trend Equation : y=%d+%.2fx"%(a,b))

```

## B- POLYNOMIAL TREND ESTIMATION
```py
## Polynomial TRend EStimation 4th degree

import numpy as np
from tabulate import tabulate
# x = list(map(int, input("Enter a list of years").split()))
# y = list(map(int, input("Enter a list of observation").split()))
x = [2011,2012,2013,2014,2015,2016]
y = [100,107,128,140,181,192]
X = [2*(i-(sum(x)/len(x))) for i in x]
print(X)
x2 = [i ** 2 for i in X]
xy = [i * j for i, j in zip(X, y)]
x3 = [i ** 3 for i in X]
x4 = [i ** 4 for i in X]
x2y=[i*j for i,j in zip(x2,y)]

table = [[i, j, k, l, m,n,o,p] for i, j, k, l, m,n,o,p in zip(x, y, X, x2, x3,x4,xy,x2y)]

print(tabulate(table, headers=["Year", "Prod", "X=x-2013", "X^2", "X^3","X^4","xy","x2y"], tablefmt="grid"))
coeff=[[len(X),sum(X)],[sum(X),sum(x2)]]

coeff=[[len(x),sum(X),sum(x2)],[sum(X),sum(x2),sum(x3)],[sum(x2),sum(x3),sum(x4)]]
Y=[sum(y),sum(xy),sum(x2y)]
A=np.array(coeff)
B=np.array(Y)
try:
  solution=np.linalg.solve(A,B)
  # print(solution)
except:
  print("error")
a,b,c=solution
# print(a,b,c)
print("Polynomial trend equation y=%.2f+%0.2fx+%.2fx^2"%(a,b,c))

```

### OUTPUT
A- LINEAR TREND ESTIMATION

![WhatsApp Image 2024-03-04 at 19 28 01_f016ddeb](https://github.com/d-kavinraja/TSA_EXP2/assets/119875375/7c289e1a-1baf-4631-93d5-dd510c28f7a1)
![WhatsApp Image 2024-03-04 at 19 28 23_b1f13096](https://github.com/d-kavinraja/TSA_EXP2/assets/119875375/c70340e0-b858-456f-a87e-98771b105d4b)


B- POLYNOMIAL TREND ESTIMATION
![WhatsApp Image 2024-03-04 at 19 37 39_71e5efb2](https://github.com/d-kavinraja/TSA_EXP2/assets/119875375/b7e2f200-95f3-47c2-b226-caebaeade389)

![WhatsApp Image 2024-03-04 at 19 38 35_bf8ccd53](https://github.com/d-kavinraja/TSA_EXP2/assets/119875375/158a9807-2cc3-409f-b232-b3961ef74097)



### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
