# Part 1
## Edstem Post Example
### Student
Hello TAs. I am writing a bash script/java program that provides the following functionality: when you run the bash script, it should prompt the user for a string and use a pre-made java program to print out the string "Hello <input>!" where <input> is whatever the user types. When I attempt to run the program, I get the following output however. 

![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/e9e0e5e8-8e13-4313-9b48-49148e9623c5)

The code for both files is as follows:

print.sh

![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/f7717906-f345-4bdb-b5b5-4848c56c577b)

HelloWorld.java

![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/8df67083-db45-4943-853e-7c84c60fdc41)

### TA
There seems to be a mistake in how you assign the java_output variable. The terminal seems to be considering `java HelloWorld $name` as three separate commands rather than a `java` command followed by parameters. Try reviewing how to assign variables in bash to help with this issue.
### Student
I think I found the bug. I did not enclose `java HelloWorld $name` in `$()` and so the terminal considered `java HelloWorld $name` as three separate commands. After wrapping this statement in a `$()` grouping, this seems to have fixed the issue. The folliwng screenshot is the working code. Thank you for the help!

![image](https://github.com/thomas-rocha/cse15l-lab-reports/assets/156377384/b9369586-2af3-489f-95bd-e23da3762e22)

## File structure for the example
```
- print_statement
  - HelloWorld.java
  - print.sh
```
## Contents of HelloWorld.java before the fix
```
public class HelloWorld {
    public static void main(String[] args){
        System.out.println("Hello " + args[0] + "!");
    }
}
```

## Contents of print.sh before the fix
```
javac HelloWorld.java

echo "Enter your name:"
read name

java_output=java HelloWorld $name

echo "Java Output: $java_output"
```

## Inputs used to trigger the bug
The first command is `bash print.sh`
After being prompted for a statement, the next input was
`Thomas`

## How to fix the bug
Enter the print.sh file. Navigate to line 6 and replace `java HelloWorld $name` with `$(java HelloWorld $name)`

# Part 2
Learning about the vim editor was very interesting to me. I used to wonder how early programmers edited files before IDEs existed and if there was a better method than directly editing text files. Vim has a lot of useful functionality that must have made editing code before IDEs much easier. I thought that the amount of commands used in vim was really cool and that someone could be extremely fast at editing files if they knew all of the tricks in vim.


