`ls`
`echo $?`
will output the exit code of last command in this case 0

create a new file 
`touch newfile`

All non zero exit codes indicate the presence of a vulnerability

Best way to understand the exit codes of a tool is to read it's documentation
https://tldp.org/LDP/abs/html/exitcodes.html

The fake security tool below written as a bash script simulates the number of vulnerabilities using a random number.

If the vulnerability count is zero, the tool returns an exit code of zero, indicating success.
If the vulnerability count is not zero, then the tool returns an exit code of 99, which is a non-zero exit code, indicating failure.
![image](https://github.com/user-attachments/assets/0d7258c8-9523-470f-9861-5c40bfa793ae)

Provide executable file permissions for myfaketool.
`chmod +x myfaketool`
Run the myfaketool and review the exit code with echo $?.
`./myfaketool`

Since vulnerabilities were found, a non-zero exit code is returned.

Let’s run the myfaketool a few more times, and review the exit code.

## Exit Status of Piped Commands
It seems there might be some misunderstanding regarding what a “pipe” (|) is and what it does. Let’s clarify what a pipe is.

Put simply, a pipe is a method used to link two distinct programs in such a way that the output from the first program is directly fed into the second as its input. Imagine it as an invisible conduit that allows data to seamlessly transfer from one program to another.

Imagine you’re working with two programs, Program A and Program B. Normally, you might have Program A save its output to a file, and then have Program B read that file to get the information. However, by using a pipe, you can streamline this process. Instead of saving and reading from a file, you can directly send the output from Program A into Program B. This method is much faster and more efficient.

For example, in a command-line interface, you might see something like:

Command Output
`program_A | program_B`

Sometimes in Bash, when we’re executing commands in a pipeline (using the | symbol), we might need to check the exit status of a particular command within that pipeline. For example, imagine we’re running a long script and we want to monitor its output in real-time.
`pdso-exit.sh 2>&1 | tee script_output`

![image](https://github.com/user-attachments/assets/0a5b7b0d-df8e-4594-9f07-86e89a62af5a)


