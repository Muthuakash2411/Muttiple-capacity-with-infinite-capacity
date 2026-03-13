# Multiple server with infinite capacity - (M/M/c):(oo/FIFO)
## Aim :
To find (a) average number of materials in the system (b) average number of materials in the conveyor (c) waiting time of each material in the system (d) waiting time of each material in the conveyor, if the arrival  of materials follow poisson process with the mean interval time 10 seconds, serivice time of two lathe machine follow exponential distribution with mean serice time 1 second and average service time of robot is 7seconds.

## Software required :
Visual components and Python

## Theory:
Queuing are the most frequently encountered problems in everyday life. For example, queue at a cafeteria, library, bank, etc. Common to all of these cases are the arrivals of objects requiring service and the attendant delays when the service mechanism is busy. Waiting lines cannot be eliminated completely, but suitable techniques can be used to reduce the waiting time of an object in the system. A long waiting line may result in loss of customers to an organization. Waiting time can be reduced by providing additional service facilities, but it may result in an increase in the idle time of the service mechanism.

![image](https://user-images.githubusercontent.com/103921593/203238035-1c8109bc-cbf2-4c77-baea-c5b682a752ef.png)

## Procedure :

![image](https://user-images.githubusercontent.com/103921593/203238265-176740b0-eae2-4772-90be-5449869ac9b0.png)




## Experiment:


## Program
````
import math

# Inputs
ArrivalTime = int(input("Enter mean inter arrival time (secs): "))
MachineTime = int(input("Enter service time of Lathe Machine (secs): "))
RobotTime = int(input("Enter service time of Robot (secs): "))
c = int(input("Enter number of servers: "))

# Total service time
TotalService = MachineTime + RobotTime

# Rates
lam = 1/ArrivalTime
mu = 1/TotalService

print("Lambda =",round(lam,3))
print("Mu =",round(mu,3))

rho = lam/(c*mu)

if rho < 1:

    # P0 calculation
    sum1 = 0
    for n in range(c):
        sum1 += (lam/mu)**n / math.factorial(n)

    sum2 = ((lam/mu)**c)/(math.factorial(c)*(1-rho))

    P0 = 1/(sum1+sum2)

    # Lq
    Lq = (P0*((lam/mu)**c)*rho)/(math.factorial(c)*(1-rho)**2)

    # Ls
    Ls = Lq + lam/mu

    # Waiting times
    Wq = Lq/lam
    Ws = Wq + 1/mu

    print("Average number of materials in system =",round(Ls,2))
    print("Average number of materials in conveyor =",round(Lq,2))
    print("Waiting time in system =",round(Ws,2),"secs")
    print("Waiting time in conveyor =",round(Wq,2),"secs")

else:
    print("System is unstable")
````

## Output :
```
Enter mean inter arrival time (secs):  10
Enter service time of Lathe Machine (secs):  1
Enter service time of Robot (secs):  7
Enter number of servers:  2
Lambda = 0.1
Mu = 0.125
Average number of materials in system = 0.95
Average number of materials in conveyor = 0.15
Waiting time in system = 9.52 secs
Waiting time in conveyor = 1.52 secs
```
## Result : 

Thus,The Python Program is implemented and executed successfully.
