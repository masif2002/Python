# Files & I/O operation
When we work with files in Python or any programming language, we don't communicate with the files directly. Instead, we work with something called a **stream**.

## Stream
It contains methods that we can use in order to perform certain actions that affect the real file.
* `open()` - The very first action we have to perfrom on the stream is, connecting to it. We can do this with the open() function, which allows us to open the file. We can open a file in either _read_ mode, _write_ mode, or _update_ mode.
* `close()` - We can disconnect from the stream with the close() method.

When you open a file, Python creates a specific class based on the way that you've opened the file, either in read, write, or update mode. This class exposes some methods that you can use to interact with the stream. This class is removed when you close the connection. 

### Types of Streams
There are two types of streams that we can work with.
* **Text Stream** - contains typographical characters such as letters, digits and so on. This file is written and read character by character or line by line.

* **Binary Stream** - This can be an executable program, an image, a database file and so on. These are basically a sequence of bytes. Contents of such streams are written and read byte by byte or block by block.

## open()
We can open a stream with the open() function. 
* We first pass path of the file we create the stream for.
* Then, an optional argument specifying the mode we want to open our file in.
* And then an optional encoding argument to specify the encoding of the file.
```python
myfile = open("path/to/file", "r")
```
* In this case, we open the file in read mode

There are several modes, with which we can open a file:
* **r** - to open it in Read mode
* **w** - Write mode
* **a** - Append mode
* **r+** - Read and update mode
* **w+** - Write and update mode

When using **r** or **r+** mode, the file needs to exist, otherise the open() function will raise an error. For the other modes, the files doesn't need to exist. If it doesn't exist, Python will create the file instead.

### Modes for Binary files
* **rb** - Read mode
* **wb** - Write mode
* **ab** - Append mode
* **r+b** - Read and update mode
* **w+b** - Write and update mode

Like binary modes, we can also explicitly specify the _t_ for _text mode_ if we want. Ex:
```python
myfile = open("path/to/file", "rt")
```

## Default streams from sys module
When our program starts, there are streams that  open automatically.  We can use these streams when we import the **system module**. This module exposes three streams.
* **sys.stdin** - Responsible for reading data by the running program.
    * This stream is normally associated with the keyboard, responsible for reading data. The `input()` reads data from the **stdin** stream by default.
* **sys.stdout** - Responsible for outputting data by the running program. 
    * This stream is associated with the screen, responsible for outputting data. The `print()` uses **stdout** to output data.
* **std.err** - Responsible for errors raised by the running program.
    * This is the stream where the program sends errors when it encounters them. 

## Methods to manipulate data from files
* `read()` - Reads the content of the file and returns it as a string. By passing in the number of bytes you need to read, you can also read the data character by character.
* `readline()` - You can also read a file's contents line by line with this method. This reads a complete line from a text file and returns that as a string.
* `readlines()` - This method treats the text file as a set of lines. It reads all the file content and returns  a list of strings, each element containing each line. You can iterate over the list with a for-loop and print each line.
* `seek()` - This method sets the cursor to the index passed in as the parameter.
* `write()` - This method is used to write data to the file. The data  to be written is passed in as a string.
* `readinto()` - This method is used to read data from binary files into a byte array. The byte array must be passed in as an argument 
```python
from os import strerror

try:
    myfile = open("paragraph.txt", "r")

    print("Reading the whole content at once..")
    ok = myfile.read()
    print(ok)
    myfile.seek(0) # Sets the cursor back to index 0
    print()

    print("Reading the whole content character by character..")
    while True:    
        ok = myfile.read(1) # Number of bytes to read
        if ok == "":
            break
        print(ok)
    myfile.seek(0)
    print()

    print("Reading content line by line..")
    while True:
        ok = myfile.readline()
        if ok == "":
            break
        print(ok)
    myfile.seek(0)
    print()

    print("Reading content as set of lines...")
    ok = myfile.readlines()
    print(ok)
    for i in ok:
        print(i)

    myfile.close()
except IOError as e:
    print("I/O error occured:", strerror(e.errno))
```
It is considered good practice to always open files with a try/except block, since file permissions or name errors are encountered regularly.

## Byte Array
In some cases, we have to deal with data that has no shape or form, just a series of bytes. This type of data is called **amorphous data**. In order to handle amorphous data, we use Python's specialized class, **bytearray**.
* A byte array is an array that contains amorphous bytes. We create a byte array with the _bytearray_ constructor function. 
```python
data = bytearray(5)
print(data)
```
>Output:
```
bytearray(b'\x00\x00\x00\x00\x00')
```
* The byte array is intialized by default with just zeroes.
* Byte arrays are mutable. We can update the values, but we need to make sure that the value we assign is always an integer between 0 and 255.
```python
data = bytearray(5)
data[0] = 2
data[2] = 3

print(data)

for i in data:
    print(i)
```
>Output:
```
bytearray(b'\x02\x00\x03\x00\x00')
2
0
3
0
0
```
----
>Note: 
Some differences between Unix/Linux systems and other operating systems can make files entirely useless, if they're executed on a different operating system than what they were written for. One such difference is the EOL characters in Unix/Linux systems and other operating systems. But, Python takes care of this and allows us to write any file as if it was intended for Unix/Linux programs, which it will make sure that it can run on other OS aswell.