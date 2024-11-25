# Daemons and Signals

Create a program that will run as a daemon and do the following:
1. Program should accept two folders as cli arguments and optionally an integer number.
   1. First folder is the source folder.
   2. Second folder is the target folder.
   3. If the integer number is provided, it should be used as the interval in seconds between moving files. If not provided, the default interval should be 1 second.
2. Program should monitor the first folder for new files and move them to the second folder.
3. If program receives a SIGUSR1 signal, it should log the number of files that program moved. 
4. If program receives a SIGUSR2 signal, it should change source and destination folders vice versa.
5. If program receives a SIGINT signal, it should move all remaining files from source directory to target, log `Sisyphus finished` and exit. If after `SIGINT` signal program receives `SIGUSR1` or `SIGUSR2` signal, it should ignore them. If after `SIGINT` signal program receives `SIGINT` signal again, it should log `Sisyphus gave up` and exit without moving remaining files.
6. If program receives a SIGTERM signal, it should log `Sisyphus gave up` and exit.

All logs should be written with identifier `sisyphus_daemon` in syslog.

Executable file should be named `sisyphus`.