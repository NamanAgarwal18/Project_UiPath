<h1>UiPath Studio Project</h1>


<a href="https://www.youtube.com/embed/htjwrcNBgVg" target="_blank"><img src="http://img.youtube.com/vi/htjwrcNBgVg/hqdefault.jpg" 
alt="IMAGE ALT TEXT HERE" width="500" height="375" border="20" /></a> 
[<h3>Video Demonstration</h3>](https://youtu.be/htjwrcNBgVg)


### Problem Statement
Our project is aimed to help Computer professors of various colleges in their evaluation of lab programs. In the current online scenario after every lab the professor has to download programs from a long list of github links posted by students and then individually run them, check the outputs, mark the student and then save the program for record purposes. In a class generally there are around 60 students and every student does one or more problem as the part of the lab assignment every week. This work every week can add up to be a daunting task for the professors.

### Description
1. Our project reads all the Github raw links from an Excel sheet named **"Links.xlsx"** form the **"Input"** sheet and puts it in a datatable.

 | Name          | Link                                                                          |
 | ------------- |:-----------------------------------------------------------------------------:|
 | Nimit         | https://raw.githubusercontent.com/nimitsajal99/RPA/main/program.cpp           |
 | Ritik         |                                                                               | 
 | Naman         | https://raw.githubusercontent.com/NamanAgarwal18/Project_UiPath/main/prog.cpp |
 | Ruttazeet     | https://raw.githubusercontent.com/nimitsajal99/RPA/main/correct.cpp           |

2. After that the **Web Recorder** is started. We use **Microsoft Edge** as the preferred browser. The Web Recorder executes the followinng steps:
    * It Opens all the links one by one
    * Coppies all the code
    * Saves all the code by th ename of the student with the **".cpp"** extention.
    * Closes all the web windows
3. After that in a loop we start opening up each program indivitually and start the **Basic Recorder**. The Basic Recorder executes the following steps:
    * Makes sure the code is opened correctly in **DEV C++** compiler.
    * Starts typing up the HeaderFile ```c++ #include<bits/stdc++.h> ```  
    
    



