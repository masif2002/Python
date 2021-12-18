# OS Module

Python allows us to interact with the operating system using the _os module_.

## Methods
* **uname()** - Returns information about the current operating system.
    * This prints an object containing:
        * name of the OS
        * machine name and the network
        * release of the OS
        * version of the OS
        * and the hardware identifier
    * `os.uname()` is only available on a subset of Unix distributions/versions.
    ```python
    import os
    print(os.uname())
    ```
* **name** - Returns the name of the operating system.
    *  With the name **property** (not a method), you can get one of three outputs.
        * 'posix' if you're using Linux
        * 'nt' if you're using Windows
        * 'java' if you're using something like Jython
    ```python
    import os
    print(os.name)
    ```
* **mkdir()** - Creates a new directory.
    ```python
    import os

    os.mkdir("new_directory")
    # os.mkdir("./new_directory") # Does the same
    ```
    * This way, we create a directory in the current working directory.

    ```python
    import os
    os.mkdir("../new_directory")
    ```
    * Here, a new directory is created in the current working directory's parent directory.
    * You can also pass in a new path to create a directory in that path.
* **listdir()** - Returns a list of all the files and folders in the current working directory.
    ```python
    import os
    os.listdir()
    ```
* **makedirs()** - This method is used to create subfolders.
    ```python
    import os
    os.makedirs("new_folder/new_sub_folder")
    ```
* **chdir()** - This method is used to change the current working directory to the specified directory.
    ```python
    import os
    os.chdir("new_folder")
    ```
* **getcwd()** - Returns the current working directory.
    ```python
    import os
    os.getcwd()
    ```
* **rmdir()** - Deletes the directory specified. But, it only works on empty directories, othwerwise Python throws an error.
    ```python
    import os
    os.rmdir("new_folder")
    ```
* **removedirs()** - Deletes directories and subdirectories.
    ```python
    import os
    os.removedirs("new_folder/sub_folder1/another_sub_folder")
    ```
* **system()** - This method allows us to pass a system command to the command line (cmd). It returns the exit status of the process.
    * 0 for success
    * 1 for error
    ```python
    import os
    os.system("mkdir new_folder")
    ```