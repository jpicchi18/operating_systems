# Operating Systems
Course projects for the UCLA course "Operating Systems Principles"

All projects were implement in the C programming language and contain a Makefile with the following targets and more: a target to compile the executables of the program, a target to run a bash script with a series of smoke tests, a "clean" target to remove residual files from the directory, and a "dist" target to compress the program files into a distributable tarball.
The full details of each project can be seen in their respective "README" files.


[warmup project](https://github.com/jpicchi18/operating_systems/tree/main/project_0):
- Implemented a program that takes a variety of command line options and reads from stdin/writes to stdout.
- Depending on the options passed, the program also has the capability of reading input from a file, writing output to a file, generating a segfault, and catching a segfault using a signal handler.


[Project 1A: Telnet Shell with Pipe](https://github.com/jpicchi18/operating_systems/tree/main/project_1/project_1A):
- a program that sets up a parent shell and child shell session that communicate using a pipe.
- The parent shell performs full duplex, character-at-a-time I/O when no option is passed. When the "--shell=program" option is passed, the child shell process performs the "program" and sends the result back to the parent through a pipe.
  - Otherwise, the child sends the input back through the pipe as the output.
- the program also features a "--debug" option that provides additional output to discern the behaviors of the parent and child shells.
- this project uses the following system calls, among others: ```getopt_long, atexit, write, read, signal, poll, waitpid, fork, pipe```

[Project 1B: Telnet Shell with Socket and Compressed Network Communication](https://github.com/jpicchi18/operating_systems/tree/main/project_1/project_1B):
- similar to project 1A in functionality, but the parent and child shell communicate through a socket over the network, as opposed to a pipe.
- the parent and child shell send data back and forth until one of server terminating events occur
- the program has several options:
  - "--compress" --> compresses data before sending it to the server, and decompresses data after recieving it from the server
    - uses "zlib" to compress data
  - "--portnum=num" --> a required flag that spcifies the port number through which the client should connect to the socket
  - "--log=filename" --> specifies a file to which a log will be written of all data transfered to and from the server over the network.
  - "--host=hostname" --> allows the user to specify a particular hostname if the server program is running on a different machine.
  - "--debug" --> provides additional debugging dialog for program development


