# Rust Lisp Interpreter

Author: Oliver Andrew Kelton \<<oakelton@gmail.com>\>

*Unfortunately, I am unable to display this repository publicly at the moment.
Those interested in seeing my work can email me at <oakelton@gmail.com> or
<oliver.kelton543@gmail.com>.*

An interpreter for "pure" common lisp, written in Rust.

([Common Lisp Reference](https://lisp-lang.org/))

The following built-in functions are supported:

- CAR
- CDR
- CONS
- NULL
- NOT
- QUOTE
- EVAL
- APPLY
- EQ
- EQUAL
- \>
- \<
- COND
- DEFUN
- SET
- SETQ
- ATOM
- SYMBOLP
- STRINGP
- LISTP
- INTEGERP
- RATIONALP
- FLOATP
- NUMBERP
- \+
- \-
- \*
- \/
- MOD
- FLOOR
- 1+
- 1-
- AND
- OR
- PRINT
- \_PRINTLN

## Dependencies

To compile the program, you will need to have the rust compiler and cargo
installed. Installation instructions can be found
[here](https://doc.rust-lang.org/cargo/getting-started/installation.html).

No non-standard crates are required for building.

## Build

To build the program, simply run the following command from within the current
directory:

```bash
cargo build --release
```

The binary executable will then be available at
target/release/rust\_lisp\_interpreter. However, the recommended way of
executing the program is given below.

## Use

By default, the program runs as a REPL cli. To run the program this way, just
execute the following command in the current directory:

```bash
cargo run
```

More advanced options are given below.

### Command Line Options

The program can be run from the command line using the following format:

```bash
cargo run -- [OPTIONS ...] [FILE_TO_EXECUTE ...]
```

If no FILE\_TO\_EXECUTE is given, the interactive REPL cli will be opened, which
can be interacted with via the terminal (stdin). Note that, while the result of
each eval will be printed in the interactive REPL, any script files passed as
command line arguments will be run silently, save for the output of PRINT and
\_PRINTLN calls.

The currently supported options are as follows:

- --load, -l PRELIMINARY\_SCRIPT\_FILE : Executes PRELIMINARY\_SCRIPT\_FILE
  before either starting the REPL or executing the file(s) passed as
  FILE\_TO\_EXECUTE. May be specified multiple times; the scripts will be
  executed in the order passed, with the global environment saved between script
  calls.
- --help, -h : Prints instructions on how to run the program, then exits.

Note: the global environment will be reset after executing each
FILE\_TO\_EXECUTE, restoring it to what it was before the first
FILE\_TO\_EXECUTE was executed, but after the last PRELIMINARY\_SCRIPT\_FILE was
executed. This means that the execution of one program should not affect the
execution of any succeeding program.

### Using the REPL

If no FILE\_TO\_EXECUTE is provided as an argument, the program will run as a
REPL, which reads statements from stdin and prints the evaluated result of each
statement to stdout. To exit the REPL, simply close stdin (^D) or kill the
program with ^C. Note that this also allows you to execute a script by piping to
stdin; unlike script files passed as command line arguments, a script passed via
stdin will print the evaluated result of each statement instead of running
silently.
