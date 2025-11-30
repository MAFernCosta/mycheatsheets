# Windows commandline Basics

| Command      | Description                                                             | Example                                |
|--------------|-------------------------------------------------------------------------|----------------------------------------|
| `COPY`         | Copies files to another location                                        | COPY file.txt D:\Backup                |
| `DIR`          | Displays files and folders in the current directory                     | DIR C:\Users                           |
| `DEL / ERASE`  | Deletes files                                                           | DEL oldfile.txt                        |
| `EDIT`         | Starts the text editor                                                  | EDIT file.txt                          |
| `CD`           | Changes the current directory                                           | CD C:\Windows                          |
| `EXPAND`       | Decompresses compressed files                                           | EXPAND archive.cab -F:* C:\Extracted   |
| `FC`           | Compares files and shows differences                                    | FC file1.txt file2.txt                 |
| `FIND`         | Finds a text string in a file                                           | FIND "error" log.txt                   |
| `MD / MAKEDIR` | Creates a new folder                                                    | MD NewFolder                           |
| `MOVE`         | Moves files from one folder to another                                  | MOVE file.txt D:\Docs                  |
| `PRINT`        | Prints the contents of a text file                                      | PRINT file.txt                         |
| `RD / RMDIR`   | Deletes a folder                                                        | RMDIR OldFolder                        |
| `REN / RENAME` | Renames a file or folder                                                | REN old.txt new.txt                    |
| `REPLACE`      | Replaces files in one directory with files of the same name in another  | REPLACE file.txt D:\Folder1 D:\Folder2 |
| `ROBOCOPY`     | Advanced tool to copy files and directories                             | ROBOCOPY C:\Source D:\Dest /E          |
| `TREE`         | Displays the directory structure of a disk or folder                    | TREE C:\ /F                            |
| `TYPE`         | Displays the contents of text files                                     | TYPE file.txt                          |
| `OPENFILES`    | Manages opened local or network files                                   | OPENFILES /QUERY                       |
| `XCOPY`        | Copies files and directory trees, used for more complex copy operations | XCOPY C:\Source D:\Dest /E             |