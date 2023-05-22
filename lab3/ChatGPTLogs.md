# ChatGPT Logs for Lab Report 3  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/1fd1c5ec-efec-4e26-bed6-ae8c5104eae3)  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/40b8e097-f4ed-4d1a-a665-874559666e8f)  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/b746b76b-1585-48b5-bd53-2d58f7761339)  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/fbac279b-93fd-464c-a161-b209088e7ff9)  
Sure! Here are some examples of how to use each of the command line prompts I mentioned earlier:

1. `ls` - Lists the files and directories in the current directory.

```
$ ls
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
```

2. `cd` - Changes the current directory. For example, `cd Documents` changes the current directory to the "Documents" directory.

```
$ cd Documents/
$ pwd
/home/user/Documents
```

3. `mkdir` - Creates a new directory. For example, `mkdir mydirectory` creates a new directory named "mydirectory" in the current directory.

```
$ mkdir mydirectory
$ ls
Desktop  Documents  Downloads  Music  mydirectory  Pictures  Public  Templates  Videos
```

4. `touch` - Creates a new file. For example, `touch myfile.txt` creates a new file named "myfile.txt" in the current directory.

```
$ touch myfile.txt
$ ls
Desktop  Documents  Downloads  Music  mydirectory  myfile.txt  Pictures  Public  Templates  Videos
```

5. `cat` - Displays the contents of a file. For example, `cat myfile.txt` displays the contents of the "myfile.txt" file.

```
$ cat myfile.txt
This is some sample text.
```

6. `cp` - Copies a file or directory. For example, `cp myfile.txt myfolder/` copies the "myfile.txt" file to the "myfolder" directory.

```
$ mkdir myfolder
$ cp myfile.txt myfolder/
$ ls myfolder/
myfile.txt
```

7. `mv` - Moves a file or directory. For example, `mv myfile.txt myfolder/` moves the "myfile.txt" file to the "myfolder" directory.

```
$ mv myfile.txt myfolder/
$ ls myfolder/
myfile.txt
```

8. `rm` - Deletes a file or directory. For example, `rm myfile.txt` deletes the "myfile.txt" file.

```
$ rm myfile.txt
$ ls
Desktop  Documents  Downloads  Music  mydirectory  Pictures  Public  Templates  Videos
```

9. `grep` - Searches for a pattern in a file. For example, `grep "apple" myfile.txt` searches for the pattern "apple" in the "myfile.txt" file.

```
$ echo "I like apples." > myfile.txt
$ grep "apple" myfile.txt
I like apples.
```

10. `wget` - Downloads a file from the internet. For example, `wget https://example.com/myfile.txt` downloads the "myfile.txt" file from the "example.com" website.

```
$ wget https://www.gnu.org/licenses/gpl.txt
$ ls
Desktop  Documents  Downloads  gpl.txt  Music  mydirectory  Pictures  Public  Templates  Videos
```  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/b4c4cee0-ae98-4e1c-b4c8-a4d0be0edf53)  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/e1b96871-721e-4c68-b4d9-d705412b1af5)  
Certainly! The `grep -e` option allows you to specify multiple patterns to search for using a regular expression. Here are a few examples:

Example 1:
Suppose you have a file named "data.txt" with the following contents:

```
apple
banana
orange
grape
```

To search for lines containing either "apple" or "orange", you can use the `-e` option as follows:

```
grep -e "apple" -e "orange" data.txt
```

The output will be:

```
apple
orange
```

Example 2:
Let's say you have a file named "numbers.txt" with the following contents:

```
123
456
789
```

To search for lines containing numbers starting with "4" or "7", you can use the `-e` option as follows:

```
grep -e "^4" -e "^7" numbers.txt
```

The output will be:

```
456
789
```

Explanation: `^4` matches lines starting with "4", and `^7` matches lines starting with "7".

Example 3:
Suppose you have a file named "emails.txt" with the following contents:

```
john@example.com
jane@example.com
mary@example.com
```

To search for lines containing either "john" or "mary" in the email addresses, you can use the `-e` option as follows:

```
grep -e "john" -e "mary" emails.txt
```

The output will be:

```
john@example.com
mary@example.com
```

Explanation: The patterns "john" and "mary" match the lines that contain "john" and "mary" respectively.

In summary, the `grep -e` option allows you to specify multiple patterns to search for using regular expressions. You can provide multiple `-e` options to include different patterns in the search.  
![image](https://github.com/DrFreshPotato/cse15l-lab-reports/assets/57509130/7b4e6b89-20ed-4ef8-894b-6a101d8ce42a)  
The `grep -x` option is used to match the entire line, rather than just a pattern within a line. It ensures that the entire line matches the specified pattern. Here are a few examples to illustrate the usage of `grep -x`:

Example 1:
Suppose you have a file named "fruits.txt" with the following contents:

```
apple
banana
orange
```

To search for lines that exactly match the pattern "banana", you can use the `-x` option as follows:

```
grep -x "banana" fruits.txt
```

The output will be:

```
banana
```

Example 2:
Consider a file named "numbers.txt" with the following contents:

```
123
456
789
45
```

To search for lines that are exactly three digits long, you can use the `-x` option as follows:

```
grep -x '...' numbers.txt
```

The output will be:

```
123
456
789
```

Explanation: The pattern `...` matches lines that are exactly three characters long.

Example 3:
Suppose you have a file named "emails.txt" with the following contents:

```
john@example.com
jane@example.com
mary@example.com
```

To search for lines that exactly match the pattern "john@example.com", you can use the `-x` option as follows:

```
grep -x "john@example.com" emails.txt
```

The output will be:

```
john@example.com
```

In summary, the `grep -x` option ensures that the entire line matches the specified pattern. It is useful when you want to search for lines that match the pattern exactly, without any extra characters before or after the pattern.  
