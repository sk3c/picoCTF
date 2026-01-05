# Log Hunt

Our server seems to be leaking pieces of a secret flag in its logs. The parts are scattered and sometimes repeated. Can you reconstruct the original flag?


## Solution

### Step 1: Analysis
First, we need to analyze the log file to understand what we are dealing with. By examining the file, we can observe that the flag is split into multiple pieces across different lines. Each piece is marked with the identifier `INFO FLAGPART:`.

### Step 2: Retrieving the Flag
To extract all the flag fragments, we can search the log file for lines containing `FLAGPART`. This can be done using the `cat` and `grep` commands:

```sh
cat server.log | grep FLAGPART
```
This command outputs all lines that contain parts of the flag. From these results, we can collect the unique flag fragments and remove any duplicates.

Finally, we can reconstruct the complete flag by arranging the pieces according to the expected flag format—for example, a flag that starts with pico and ends with }.
