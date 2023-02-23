# File I/O

The code will first generate random data and write to a file `data.txt`. The next block of code will read data from `data.txt` , parse this data and print this data on the console.

> `with` keyword used in the below code ensures that the opened file is closed at the end of read or write operations.

````python
```python
import random
import time
with open("data.txt", "w") as fhandle:
    for i in range(1024):
        x1 = random.randint(1,255)
        #x2 = random.randint(1,255)
        #fhandle.write(str(x1) + "," + str(x2) + "\n")
        fhandle.write(str(x1) + "\n")

data = []
with open("data.txt", "r") as fhandle:
    for line in fhandle:
        line=line.rstrip('\n')
        line=line.rstrip('\r')
        data.append(line.split(','))

while True:
    for row in data:
        print(row)
        time.sleep(0.5)
```
````
