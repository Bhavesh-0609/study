# OST Shell script
## Execution of shell script
> there is three way to execute shell script
>   1. `./<filename>`
>   2. `source ./<filename>` or `source <filename>`
>   3. `base <filename>` or `base -x <filename>`<br>
>          - `base -x <filename>` show executable code

## Steps to write and execute a script
>-    Open the terminal. Go to the directory where you want to create your script.
>-    Create a file with .sh extension.
>-    Write the script in the file using an editor.
>-    Make the script executable with command chmod +x <fileName>.
>-    Run the script using ./<fileName>.
>
>-    `Note: In the last step you have to mention the path of the script if your script is in other directory.`


## Shell script parameters
>A bash shell script have parameters. These parameters start from $1 to $9.
>
>When we pass arguments into the command line interface, a positional parameter is assigned to these arguments through the shell.
>
>The first argument is assigned as $1, second argument is assigned as $2 and so on...
>
>If there are more than 9 arguments, then tenth or onwards arguments can't be assigned as $10 or $11.
>
>You have to either process or save the $1 parameter, then with the help of shift command drop parameter 1 and move all other arguments down by one. It will make $10 as $9, $9 as $8 and so on. 
> ### Shell Parameters
>
>- **$1-$9**    Represent positional parameters for arguments one to nine
>
>- **${10}-${n}** 	Represent positional parameters for arguments after nine
>
>- **$0**         	Represent name of the script
>
>- **$∗**        	Represent all the arguments as a single string
>
>- **$@**        	Same as $∗, but differ when enclosed in (")
>
>- **$#**        	Represent total number of arguments
>
>- **$$**        	PID of the script
>
>- **$?**        	Represent last return code
>
> ### Example:
> ![1](https://static.javatpoint.com/linux/ss/images/script-parameters1.png)
> 
> Look at the above snapshot, this is the script we have written to show the different parameters.
> 
> ![2](https://static.javatpoint.com/linux/ss/images/script-parameters2.png)
>
> Look at the above snapshot, we have passed arguments 1, 5, 90. All the parameters show their value when script is run.

## Shell Scripting Shift Through Parameters
> Shift command is a built-in command. Command takes number as argument. Arguments shift down by this number.
>
> For example, if we give 2 parameters to the programme than in loops first iteration $1 = first given argument and in second iteration it will be $1 = second given argument
>
> For example, if number is 5, then $5 become $1, $6 become $2 and so on.
> ### Example:
> The shift command is mostly used when arguments are unknown. Arguments are processed in a while loop with a condition of (( $# )). this condition holds true as long as arguments are not zero. Number of arguments are reduced each time as the shift command executes.
> ![3](https://static.javatpoint.com/linux/ss/images/shift-through-parameters1.png)
