# OST Shell script
## Execution of shell script
> there is three way to execute shell script
>   1. `./<filename>`
>   2. `source ./<filename>` or `source <filename>`
>   3. `base <filename>` or `base -x <filename>`<br>
>          - `base -x <filename>` show executable code

## Steps to write and execute a script
>-

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
