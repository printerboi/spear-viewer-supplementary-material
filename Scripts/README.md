# Script submodule

This submodule contains the scripts used to evaluate results collected during the study

## Structure

The script submodule is separated into the following two files:

- **runner.py**: Python script to execute a set of tasks repeatedly and measure the used energy for each repetition. Will yield a `result.csv` containing the calculated energy per repetition for each given task.
- **parser.py**: Python script to parse a given `result.csv` yielding a pyplot GUI with a box plot and JSON output to stdout containing the calculated average for each task and the corresponding standard deviation.

## Installation

To use the scripts, make sure python 3 is installed. We used python `3.12.7`.
Make sure `matplotlib` is installed, and you are using an Intel CPU with an architecture as recent as the Sandy-bridge architecture, as the RAPL registers are only available on some CPUs (See a list of architectures [here](https://web.eece.maine.edu/~vweaver/projects/rapl/rapl_support.html))

## Execution

To execute the scripts, use the following explanations:

### runner.py

```
sudo python3 runner.py
```
⚠️ Please execute the script using sudo, as the RAPL registers can only be read using elevated rights.

After launching the script, the application expects a path to a folder containing the tasks that should be executed via stdin.

*Example*: Given the following file structure
```
runner.py
study
|
--> result
    |
    --> Task_1
    |
    --> Task_2
    |
    --> Task_3
```

The script will expect the path `study/result/` as input


### parser.py

```
python3 parser.py
```

After launching the script, the application expects a path to a generated `result.csv` via stdin.

*Example*: Given the following file structure
```
parser.py
study
|
--> result
    |
    --> result.csv
```

The script will expect the path `study/result/results.csv` as input

