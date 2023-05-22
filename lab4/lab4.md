# Lab Report 4  
## Instructions:
1. Log into ieng6
2. Clone your fork of the repository from your Github account
3. Run the tests, demonstrating that they fail
4. Edit the code file to fix the failing test
5. Run the tests, demonstrating that they now succeed
6. Commit and push the resulting change to your Github account (you can pick any commit message!)

![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/7005b965-f766-494f-8fa8-8f408da0c71a)  
**Keys Pressed**: ssh cs15lsp23nu@ieng6.ucsd.edu `<enter>` 
  I didn't have it saved on clipboard so I typed out the command to log into my ssh account then pressed enter to enter the command.
  

![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/8ef803c6-4b6d-41c2-aa6f-9709203a9042)  
**Keys Pressed**: git clone `<right click>`  
  Went to github to copy the ssh link first, then in the terminal typed git clone then pressed `<right click>` to paste. 

![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/da802440-1a9c-40d5-bd0a-874586ad4be2)  
**Keys Pressed**: cd la `<tab> <enter>` bash t `<tab> <enter>`  
  To access the test you have to enter the directory created from git clone, then the test can be ran through the bash script.  

![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/2c0303be-0616-48de-ade6-68f3b276343c)  
**Keys Pressed**: vim L `<tab>` .java `<enter>`  
  To edit the failed test, we enter the broken function's file through vim text editor  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/4b26b4f1-fe6b-4b51-9fe0-d8fc3e417041)
**Keys Pressed**: `<r2> <:wq>`  
  The image shows the after edit, but after the previous command the cursor was already perfectly in place over the error. The error was then fixed by replacing it with "2" then saving and exiting. The error was that `index2 += 1` was originally `index1 += 1` which is incorrect.   

![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/7d823451-9d52-4f0f-a112-a21c66c23d7e)  
**Keys Pressed**: `<up> <up> <enter>`  
  To rerun the test script, pressing up arrow twice would go through the command history where I last used the command.  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/32337abe-5340-4ab3-9490-dd435a4c11bb)  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/f2c06e01-3bac-46a2-b59d-de7d3c3e057f)  
**Keys Pressed**: git add L `<tab>` .java `<enter>` git commit -m "Fixed ListExamples.java" `<enter>` git push origin main `<enter>`  
  git add is to let git know that this particular file is to be updated, then git commit alongside a -m message (it can be any message) saves the changes, then finally git push origin main pushes the updated file to the origin of the repository stored in github. 


