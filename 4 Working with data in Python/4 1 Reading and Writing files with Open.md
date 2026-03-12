# 4.1 Reading and Writing files with Open

# Reading files with `open`

## Opening the file using Python's open function

One way to read or write a file in Python is to use the built-in `open` function. The `open` function provides a **File object** that contains the methods and attributes you need in order to read, save, and manipulate the file. It takes two primary parameters:

1. **File path**: The file path parameter consists of the filename and directory where the file is located.
2. **Mode**: The mode parameter specifies the purpose of opening the file, such as 'r' for reading, 'w' for writing, or 'a' for appending.
    
    ![Captura de pantalla 2024-12-14 a las 16.54.44.png](../img/Captura_de_pantalla_2024-12-14_a_las_16.54.44.png)
    

> **Note**: we will only cover **.txt** files.
> 

```python
# Read the Example1.txt
example1 = "example1.txt"
file1 = open(example1, "r")

# Print the path of file
file1.name #output: 'example1.txt'

# Print the mode of file, either 'r' or 'w'
file1.mode #output: 'r'

# Read the file
FileContent = file1.read()
FileContent #output: 'This is line 1 \nThis is line 2\nThis is line 3'. The /n means that there is a new line.

# Print the file
print(FileContent) # It will be printed with the new lines instead of \n.

# Type of file content
type(FileContent) #output: str

# Close the file: Essential so that resources are not wasted
file1.close()
```

## Opening the file using `with` statement

To simplify file handling and ensure proper closure of files, Python provides the `with` statement. Using the `with` statement is **better practice**, it automatically closes the file even if the code encounters an exception. The code will run everything in the indent block then close the file object. 

```python
# Open file using with

with open(example1, "r") as file1:
    FileContent = file1.read()
    print(FileContent) 
    
# Verify if the file is closed
file1.closed #output: True

# See the content of file
print(FileContent) #prints the file content
```

## Performing read operations on a file

### 1. Reading the entire content

You can read the entire content of a file using the read method, which stores the data as a string in a variable. This content can be printed or further manipulated as needed.

```python
# Reading and Storing the Entire Content of a File
# Using the read method, you can retrieve the complete content of a file
# and store it as a string in a variable for further processing or display.

# Step 1: Open the file you want to read
with open('file.txt', 'r') as file:    

# Step 2: Use the read method to read the entire content of the file    
file_stuff = file.read()    

# Step 3: Now that the file content is stored in the variable 'file_stuff',    
# you can manipulate or display it as needed.    
# For example, let's print the content to the console:    
print(file_stuff)

# Step 4: The 'with' statement automatically closes the file when it's done,
# ensuring proper resource management and preventing resource leaks.
```

**Step 1**: Involves opening the file, specifying 'file.txt' as the file to be opened for reading ('r') mode using the with context manager.

**Step 2**: Utilizes the `read()` statement on the file object (file) to read the entire file. This content is then stored in the file_stuff variable.

**Step 3**: Explain that with the content now stored in file_stuff, you can perform various operations on it. In the example provided, the code prints the content to the console, but you can manipulate, analyze, search, or process the text data in file_stuff based on your specific needs.

**Step 4**: Emphasizes that the with block automatically closes the file when done, ensuring proper resource management and preventing resource leaks. This is a crucial aspect of using the with statement when working with files.

### 3. Reading specific characters

You can specify the number of characters to read.

```python
# Read certain amount of characters

with open(example1, "r") as file1:
    print(file1.read(4))
    print(file1.read(4))
    print(file1.read(7))
    print(file1.read(15))
```

![Captura de pantalla 2024-12-14 a las 17.13.46.png](../img/Captura_de_pantalla_2024-12-14_a_las_17.13.46.png)

> **Navigate to the intended position (Optional)**
If you want to read characters from a specific position in the file, you can use the seek() method. This method moves the file pointer (like a cursor) to a particular position. The position is specified in bytes, so you'll need to know the byte offset of the characters you want to read.
`file.seek(10)  # Move to the 11th byte (0-based index)`
> 

### 2. Reading the content line by line

Python provides methods to read files line by line:

- The `readlines()` method reads the file line by line and stores each line as an element in a list. The order of lines in the list corresponds to their order in the file.
- The `readline()` method reads individual lines from the file. It can be called multiple times to read subsequent lines.

```python
# Read all lines and save as a list
with open(example1, "r") as file1:
    FileasList = file1.readlines()

print(FileasList) #output: ['This is line 1 \n', 'This is line 2\n', 'This is line 3']

```

```python
# Read one line
with open(example1, "r") as file1:
    print("first line: " + file1.readline())
```

```python
# We can pass an argument to readline() to specify the number of charecters we want to read.
# Unlike read(), readline() can only read one line at most.
with open(example1, "r") as file1:
    print(file1.readline(20)) # does not read past the end of line
    print(file1.read(20)) # Returns the next 20 chars
```

```python
# Iterate through the lines
with open(example1,"r") as file1:
        i = 0;
        for line in file1:
            print("Iteration", str(i), ": ", line)
            i = i + 1
```

# Writing files with `open`

### Writing files with ‘w’ mode

We can open a file object using the method `write()` to save the text file to a list. To write to a file, the mode argument must be set to **w**. 

```python
# Write line to file
exmp2 = '/Example2.txt'
with open(exmp2, 'w') as writefile:
    writefile.write("This is line A")

# To see if it worked, we can read the file
with open(exmp2, 'r') as testwritefile:
    print(testwritefile.read()) #output: This is line A
```

```python
# Write multiple lines to file
with open(exmp2, 'w') as writefile:
    writefile.write("This is line A\n")
    writefile.write("This is line B\n")
```

The method `.write()` works similar to the method `.readline()`, except instead of reading a new line it writes a new line. The process is illustrated in the figure. The different colour coding of the grid represents a new line added to the file after each method call.

![Captura de pantalla 2024-12-14 a las 17.34.05.png](../img/Captura_de_pantalla_2024-12-14_a_las_17.34.05.png)

```python
# We write a list to a .txt file as follows:

Lines = ["This is line A\n", "This is line B\n", "This is line C\n"]

with open('/Example2.txt', 'w') as writefile:
    for line in Lines:
        print(line)
        writefile.write(line)
```

> **Note that setting the mode to w overwrites all the existing data in the file.**
> 

### Appending files with ”a” mode

```python
# Write a new line to text file

with open('/Example2.txt', 'a') as testwritefile:
    testwritefile.write("This is line C\n")
    testwritefile.write("This is line D\n")
    testwritefile.write("This is line E\n")
```

### Additional modes

`.write()` writes at a certain location in the file. `.read()` reads at a certain location in the file and so on. 

Opening the file in **w** is akin to opening the .txt file, moving your cursor to the beginning of the text file, writing new text and deleting everything that follows. Opening the file in **a** is similiar to opening the .txt file, moving your cursor to the very end and then adding the new pieces of text.

It is often very useful to know where the 'cursor' is in a file and be able to control it. The following methods allow us to do precisely this:

- `.tell()` →  returns the current position in bytes
- `.seek(offset,from)` → changes the position by 'offset' bytes with respect to 'from'. From can take the value of 0,1,2 corresponding to beginning, relative to current position and end

It's fairly inefficient to open the file in **a** or **w** and then reopening it in **r** to read any lines. Luckily we can access the file in the following modes:

- **r+** : Opens the file for **both reading and writing**. The file pointer starts at the beginning of the file. You can **read from** and **write to** the file without truncating its contents. If the file does not exist, it raises a `FileNotFoundError`.
- **w+** : Opens the file for **writing and reading**. The file is **truncated** (cleared of existing contents) when opened. If the file does not exist, it is created.
- **a+** : Opens the file for **both appending and reading**. The file pointer is placed at the end of the file, so any new data is appended. You can also read the existing content, but you might need to use `.seek(0)` to reset the pointer to the beginning. If the file does not exist, it is created.

```python
with open('/Example2.txt', 'a+') as testwritefile:
    print("Initial Location: {}".format(testwritefile.tell()))
    
    data = testwritefile.read()
    if (not data):  #empty strings return false in python
            print('Read nothing') 
    else: 
            print(testwritefile.read())
            
    testwritefile.seek(0,0) # move 0 bytes from beginning.
    
    print("\nNew Location : {}".format(testwritefile.tell()))
    data = testwritefile.read()
    if (not data): 
            print('Read nothing') 
    else: 
            print(data)
    
    print("Location after read: {}".format(testwritefile.tell()) )
```

> Note on the difference between **w+** and **r+**. Both of these modes allow access to read and write methods, however, opening a file in **w+** overwrites it and deletes all pre-existing data. To work with a file on existing data, use **r+** and **a+**. While using **r+**, it can be useful to add a `.truncate()` method at the end of your data. This will reduce the file to your data and delete everything that follows.
> 

```python
with open('/Example2.txt', 'r+') as testwritefile:
    testwritefile.seek(0,0) #write at beginning of file
    testwritefile.write("Line 1" + "\n")
    testwritefile.write("Line 2" + "\n")
    testwritefile.write("Line 3" + "\n")
    testwritefile.write("Line 4" + "\n")
    testwritefile.write("finished\n")
    #Uncomment the line below
    testwritefile.truncate()
    testwritefile.seek(0,0)
    print(testwritefile.read())
```

## How to copy a file

```python
# Copy file to another

with open('/Example2.txt','r') as readfile:
    with open('/Example3.txt','w') as writefile:
          for line in readfile:
                writefile.write(line)
      
                
# Verify if the copy is successfully executed

with open('/Example3.txt','r') as testwritefile:
    print(testwritefile.read())
```

## Lab Exercise

Your local university's Raptors fan club maintains a register of its active members on a .txt document. Every month they update the file by removing the members who are not active. You have been tasked with automating this with your Python skills.

Given the file `currentMem`, remove each member with a 'no' in their Active column. Keep track of each of the removed members and append them to the `exMem` file. Make sure that the format of the original files in preserved. (*Hint: Do this by reading/writing whole lines and ensuring the header remains*)

```python
# Solution: 

def cleanFiles(currentMem,exMem):
    with open(currentMem,'r+') as writeFile: 
        with open(exMem,'a+') as appendFile:
            #get the data
            writeFile.seek(0)
            members = writeFile.readlines()
            #remove header
            header = members[0]
            members.pop(0)
                
            inactive = [member for member in members if ('no' in member)]
            '''
            The above is the same as 

            for member in members:
            if 'no' in member:
                inactive.append(member)
            '''
            #go to the beginning of the write file
            writeFile.seek(0) 
            writeFile.write(header)
            for member in members:
                if (member in inactive):
                    appendFile.write(member)
                else:
                    writeFile.write(member)      
            writeFile.truncate()        
```

```python
# otra solución (con ayuda/explicaciones de chatGPT)

def cleanFiles(currentMem, exMem):
    # Open currentMem in r+ mode for reading and overwriting
    with open(currentMem, 'r+') as read_file:
        # Open exMem in a+ mode for appending
        with open(exMem, 'a+') as append_file:
            # Read the header and member rows
            header = read_file.readline()  # Store the header
            all_members = read_file.readlines()  # Read the rest of the file
            
            # Create separate lists for active and inactive members
            active_members = []
            inactive_members = []
            
            # Process each member
            for member in all_members:
                if 'no' in member:  # If the member is inactive
                    inactive_members.append(member)
                else:  # If the member is active
                    active_members.append(member)
            
            # Append inactive members to exMem
            append_file.writelines(inactive_members)
            
            # Reset file pointer for currentMem and write back active members
            read_file.seek(0)
            read_file.write(header)  # Write the header back
            read_file.writelines(active_members)  # Write active members
            read_file.truncate()  # Remove any leftover lines from the file
            
# Run the cleanFiles function
memReg = '/members.txt'
exReg = '/inactive.txt'
cleanFiles(memReg, exReg)

# Viewing the files
headers = "Membership No  Date Joined  Active  \n"
with open(memReg, 'r') as read_file:
    print("Active Members: \n\n")
    print(read_file.read())

with open(exReg, 'r') as read_file:
    print("Inactive Members: \n\n")
    print(read_file.read())

```