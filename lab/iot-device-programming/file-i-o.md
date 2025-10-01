# File I/O

The code will first generate random data and write to a file `data.txt`. The next block of code will read data from `data.txt` , parse this data and print this data on the console.

> `with` keyword used in the below code ensures that the opened file is closed at the end of read or write operations.

> Feather Sense may not allow writing of file at runtime. To resolve this, remove file-writing part of the code and manually create `data.txt` file in `CIRCTUITPY` drive.

```python
file = open("data.txt", "r")  # Open the file for reading
for line in file:  # Loop through each line in the file
    values = line.strip().split(",")  # Split the line into a list of values
    tup = tuple(values)  # Convert the list of values into a tuple
    print(tup)  # Print the tuple
file.close()  # Close the file

```

1. `file = open("data.txt", "r")`: This line opens the file called `data.txt` in read-only mode ("r") and assigns it to the variable `file`. The file is now ready to be read from.
2. `for line in file:`: This line starts a `for` loop that loops through each line in the file. The loop iterates over each line in the file, and assigns each line to the variable `line`.
3. `values = line.strip().split(",")`: This line strips any leading or trailing whitespace from the line using the `strip()` method, and then splits the line into a list of values using the `split(",")` method. The `split()` method takes a delimiter as an argument and splits the string at each occurrence of the delimiter. In this case, the delimiter is a comma (","), so the line is split into a list of values wherever there's a comma.
4. `tup = tuple(values):` This line creates a tuple called `tup` from the list of `values`. The `tuple()` function takes an iterable (in this case, a list) as an argument and returns a tuple with the same elements. In Python, a tuple is a collection of values, just like an array. However, unlike arrays, tuples are immutable, which means that once a tuple is created, it cannot be modified. We can access the values in the tuple using indexing, just like with an array: `print(my_tuple[0]) # prints 1`
5. `print(tup)`: This line prints the tuple to the console.
6. `file.close()`: This line closes the file after we've finished reading from it. This is important to release any system resources used by the file and prevent any potential issues with the file in the future.

Overall, this code opens a file, reads each line from the file, splits each line into a list of values using a comma as a delimiter, converts the list of values into a tuple, and then prints each tuple to the console. It's a simple way to read a CSV file in Python and work with the data in a structured format.

Sample data.txt

```
1,2,3,4,5,6
7,8,9,10,11,12
13,14,15,16,17,18
19,20,21,22,23,24
25,26,27,28,29,30
```

Another version of the file reading code

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
