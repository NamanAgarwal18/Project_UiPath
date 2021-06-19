<h1 align="Center"> UiPath Studio Project </h1>


<center><a href="https://www.youtube.com/embed/htjwrcNBgVg" target="_blank"><img src="http://img.youtube.com/vi/htjwrcNBgVg/hqdefault.jpg" 
alt="IMAGE ALT TEXT HERE" width="500" height="375" border="20" /></a></center>
[<h3>Click Here To Watch The Video Demonstration</h3>](https://youtu.be/htjwrcNBgVg)
***

### Problem Statement
Our project is aimed to help Computer professors of various colleges in their evaluation of lab programs. In the current online scenario after every lab the professor has to download programs from a long list of github links posted by students and then individually run them, check the outputs, mark the student and then save the program for record purposes. In a class generally there are around 60 students and every student does one or more problem as the part of the lab assignment every week. This work every week can add up to be a daunting task for the professors.
***
### Technologies Incorporated 
* UiPath Studio
* Microsoft OCR
* Basic Recording
* Web Recording
***
### Input Required
The only input required is a Excel File named **"Links.xlsx"** 
***
### Output Obtained
1. A folder containing
  * All the programs saved by student's name
  * Executable files for all the programs saved by the student's name
  * Output screenshot saved by the student's name  
2. An Excel sheet containg final evaluation result of all the students. There can be 4 possible outcomes for each student :
  * No Link Given = **""**
  * Problem during compilation = **Compilation Error**
  * Incorrect Output after compilation = **Incorrect Output**
  * Correct Output after compilation = **Correct**
***
### Execution Algorithm
1. Our project reads all the Github raw links from an Excel File named **"Links.xlsx"** form the **"Input"** sheet and puts it in a datatable.

 | Name          | Link                                                                          |
 | ------------- |:-----------------------------------------------------------------------------:|
 | Nimit         | https://raw.githubusercontent.com/nimitsajal99/RPA/main/program.cpp           |
 | Ritik         |                                                                               | 
 | Naman         | https://raw.githubusercontent.com/NamanAgarwal18/Project_UiPath/main/prog.cpp |
 | Ruttazeet     | https://raw.githubusercontent.com/nimitsajal99/RPA/main/correct.cpp           |

2. After that the **Web Recorder** is started. We use **Microsoft Edge** as the preferred browser. The Web Recorder executes the followinng steps:
    * It Opens all the links one by one
    * Coppies all the code (using **Get Visible Text Activity**)
    * Saves all the code by th ename of the student with the **".cpp"** extention.
    * Closes all the web windows (using **Close Tab Activity**)
    * *If there is no link present for a student then no browser is opened and no file is downloaded*
3. After that in a loop we start opening up each program indivitually and start the **Basic Recorder**. The Basic Recorder executes the following steps:
    * Makes sure the code is opened correctly in **DEV C++** compiler.
    * Starts to type (using **Type Into Activity**) the HeaderFile ```#include<bits/stdc++.h>``` at the start of the code and press ```Enter```
    * The code is ```COMPILE``` in **DEV C++**
    * Closes the window (using **Close Application Activity**)
    * *If there is no file is downloaded for a student then that student is ignored in this process*
4. After that in a loop we again start opening up each program indivitually and start the **Basic Recorder**. The Basic Recorder executes the following steps:
    * *If the file is not downloaded:*
       * Then an empty string value (i.e. ```""``` ) along with the name of the student is stored in a datatable to be appended in the output.
    * *If the file is downloaded and there is no compilation error:*
       * Then we sure the code is opened correctly in **DEV C++** compiler.
       * Then the code is ```RUN```
       * Then the output of the code is Screenshotted (using **Take Screenshot Activity**) and then saved (using **Save Image Activity**) with the respective student's name.
       * Then the window is closed (using **Close Application Activity**)
       * Then the text is retrieved from the image via **"Microsoft OCR"** and then saved in a variable.
       * Then we check if the string contains our desired output using **.Contains()** (in this case our desired output is **"Hello World"** )
       * *If the output matches:* 
           *  Then the string ```Correct``` along with the name of the student is stored in a datatable to be appended in the output.
       * *If the output does not match:* 
           *  Then the string ```Incorrect Output``` along with the name of the student is stored in a datatable to be appended in the output.
     * *If the file is downloaded and there is compilation error:*
       * Then we sure the code is opened correctly in **DEV C++** compiler.
       * Then the code is ```RUN```
       * Then we wait for the CMD run window to open for 2000 milliseconds (using **Element Exists Activity**)
       * When we don't find the element after 2 seconds then we understand that there is no compiled file and there must be a compilation error in the code.
       * Then the window is closed (using **Close Application Activity**)
       * Then the string ```Compilation Error``` along with the name of the student is stored in a datatable to be appended in the output.
     * After that the datatable variable is appended in an Excel File named **"Links.xlsx"** in the **"Checked"** Sheet.
5. The program execution ends and the output saved looks like:

 | Name          | Output            |
 | ------------- |:-----------------:|
 | Nimit         | Incorrect Output  |
 | Ritik         |                   | 
 | Naman         | Compilation Error |
 | Ruttazeet     | Correct           |
***
### Limitations of the program
* No Comments can be there in the program. 
* No headerfile should be there.
* Can only compile C++ code as of now.
* Can not add input for the code as of now. 
* Can not change the directory of the input or the output for now.

