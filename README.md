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

<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/7edb9045-70cd-47dd-a57c-978cbb083030" />

<img width="1280" height="720" alt="image" src="https://github.com/user-attachments/assets/64b437ae-a78f-4483-8e7b-f0e2d5a84528" />


## Program

NAME :	ROHIT GP
REGISTER NUMBER :	212224220082

```python
import math

arr_time = float(input("Enter the mean inter arrival time of objects from Feeder (in secs): "))
ser_time = float(input("Enter the mean inter service time of Lathe Machine (in secs) : "))
Robot_time = float(input("Enter the Additional time taken for the Robot (in secs) : "))
c = int(input("Number of service centres: "))

lam = 1 / arr_time
mu = 1 / (ser_time + Robot_time)

print("--------------------------------------------------------------")
print("Multiple Server with Infinite Capacity - (M/M/c):(∞/FIFO)")
print("--------------------------------------------------------------")
print("The mean arrival rate per second : %0.2f " % lam)
print("The mean service rate per second : %0.2f " % mu)

rho = lam / (c * mu)

sum = 0
for i in range(c):
    sum += (lam / mu) ** i / math.factorial(i)
sum += ((lam / mu) ** c / (math.factorial(c))) * (1 / (1 - rho))
P0 = 1 / sum

if rho < 1:
    Lq = (P0 * (lam / mu) ** c * rho) / (math.factorial(c) * (1 - rho) ** 2)
    Ls = Lq + lam / mu
    Ws = Ls / lam
    Wq = Lq / lam

    print("Average number of objects in the system        : %0.2f " % Ls)
    print("Average number of objects in the conveyor      : %0.2f " % Lq)
    print("Average waiting time of an object in system    : %0.2f secs" % Ws)
    print("Average waiting time of an object in conveyor  : %0.2f secs" % Wq)
    print("Probability that the system is busy            : %0.2f " % rho)
    print("Probability that the system is empty           : %0.2f " % (1 - rho))
else:
    print("Warning! System is unstable (ρ ≥ 1)")

```
## Output :

## Result : 

