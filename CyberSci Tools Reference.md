# CyberSci Tools Reference

## LLDB

```
# Load program into LLDB
lldb <path_to_executable>

# Set breakpoint to function
breakpoint set -n <function_name>
b <function_name>

# See all breakpoints
breakpoint list
br l

# Delete a breakpoint
br del <number>

# Start program
proces launch | run | r

# Step into (source)
step

# Step into (assm)
si

# Next instruction/step over (source)
n

# Next instruction (assm)
ni

# Step out of
finish

# Continue execution until next instruction
continue

# View the value of registers
register read

# Edit the value of a register 
register write <register_name> <value>

# Showing values of local variables and parameters
frame variable

# Reading memory
memory read <address>

# Writing memory
memory write <address> <value>

# Modifying a variable's value
expr <variable_name> = <value>

# View specific variable's value
print <variable_name>

# View specific variable's address
print &(<variable_name>)

# View both source code and assembly
disassemble --frame --mixed
```

## Asbits

- This tool allows you to convert decimal to binary on the command line

```
# Command format
asbits <decimal_value> <number_of_nibbles_displayed>

# Ex
Input: asbits 10 5
Output: 0000 0000 0000 0000 1010
```

- Note: `number_of_nibbles_displayed` can only be in the range 0-8

## Rabin2

- This tool is similar to the Linux strings tool, but it can sometimes find strings in binary files that the strings tool can’t
- Note: it can do more than just strings, but that is all I have currently used it for

```
# Command format
rabin2 -z <executable_name>

# Piping rabin output into grep to search for flag
ravin2 -z <executable_name> | grep -i "<string_to_search>"
```

## iPython3

- This tool is an interactive python terminal, similar to the normal interactive python terminal

```
# Command to run
ipython3
```

## UPX

- Tool for unpacking binaries
- To find out if a binary is packed using UPX, you can use the `strings` tool and look at the end:
    - `strings <executable_name> | tail`
- If UPX! UPX! is present, then it has been packed by UPX

```
# Command to unpack binary
upx -d <executable_name> -o <unpacked_file_name>
```

## XXD

- Tool for making a hex dump or doing the reverse

```
# Command for dumping binary to hex and ASCII
xxd -d <executable_name>
```

## Hexedit

- Another tool for viewing binary executable in hex
    - Note: Use `Ctrl + C` to exit, it is an interactive display

```
# Command
hexedit <executable_name>
```

## Checksec

- Checks the security information on an executable

```
# Command
checksec <executable_name>

# On different versions
checksec --file=<executable_name>
```

## Objdump

- Tool that shows addresses of functions and variables, as well as assembly instructions

```
# Command
objdump -d <executable_name>
```

## Readelf

- Reads the bytes of an ELF executable

```
# Command
readelf -a <executable_name>
```