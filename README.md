# Restonic

'Restonic' is an Open Source CLI tool intended to solve the Cluster-Management problem for the IBM Datapower Product.

The main purpose for 'Restonic' is to be reliable for managing a cluster of datapowers, with an intention to be fast and customizeable as well.

'Restonic' lets you create, modify and delete configuration  objects on any amount of Datapowers at once without transfering from one managment tool to another.
'Restonic' also lets you copy and move configurations from one Datapower to a numerous number of Datapowers with one single command

## Getting Started

### For production use

When you want to use Restonic for production use, there are some steps I recommend doing before.

1. Create a directory to keep the executable in
2. Either add the directory to the `$PATH` variable or move the previously created directory under an existed directory within the `$PATH` variable. Example:

    **Linux**:
        ```mkdir /opt/restonic```
        ```export PATH=/opt/restonic:$PATH```

    **Windows**:
        ```mkdir C:\Program Files\Restonic```
        ```set PATH=%PATH%;C:\Program Files\Restonic```
3. Run restonic for the first time without any command. This will initialize the configuration folder in the same directory where the application was executed.Therefore, adding the directory to the path and running from there is highly recommended.

### Using the source code

In case you want to compile Restonic for yourself, all you need to do is to install ```python3```, ```pip3``` and use ```pip3 install pyinstaller``` so you can make ```restonic.py``` an executable.

To make ```restonic.py``` an executable, you can use this command:```pyinstaller --onefile restonic.py```

>Note: When using the command, it will make an executable that will only run on the same operating system as the one who will execute it. When compiling in Linux, only Linux distrobution operating systems will be able to run the output file and Vise Versa for Windows.

## TODO

### Tests

- [ ] Create a unittest structure.
- [ ] Create tests for each command in each command-set.

>Each unittest is going to be for each command-set (mpgw_commands, fsh_commands, etc.). Each test will create, list, export, save and delete the configuration.

### logging

- [ ] Implement a logging mechanism.

### config.py

- [x] Refactor the configuration file to be able to have multiple datapowers from multiple environments.
- [x] Create a function that returns an organized list of datapowers from the configuration file for an easy use in commands.

### commands

- [x] Add an option to specify which datapower apply the command to. For example: when the option '--machine' is used, check if the given value exists within the configuration as a datapower. In case the given value is 'all', apply the command to all of the datapowers from the configuration file.If the given value isnt a datapower or the word 'all', return an error message.
- [x] Remove not-needed prints.
- [ ] Pass config object as context variable and not as Gloal variable.
- [x] Add a command for manipulating files on the datapower - (filestore_commands.py).
- [ ] For each command-set, have them implement an 'export' & 'import' option.
- [ ] For each command-set, have them 'copy' the configuratoin from said datapower to another datapower.

### mpgw_commands.py

- [x] Create a function that returns a list of MultiProtocol Gateways Names from a specific datapower / environment / all of them.
- [ ] Create a function that modifies a given MultiProtocol Gateway.
- [x] Create a function for exporting given MultiProtocol Gateway.
- [ ] Create a function for importing a given MultiProtocol Gateway configuration.

### fsh_commands.py

#### http

- [ ] Create a function that Modifies a given HTTP Front Side Handler.
- [x] Create a function for exporting a given HTTP Front Side Handler.
- [ ] Create a function for importing a given HTTP Front Side Handler configuration.

#### mq

- [ ] Create a function that Modifies a given MQ Front Side Handler.
- [ ] Create a function for exporting a given MQ Front Side Handler.
- [ ] Create a function for importing a given MQ Front Side Handler configuration.

### filestore_commands.py

- [x] Create a function that returns the content of a given directory.
- [ ] Create a function for updating the content of a given file name.
- [ ] Create a function for deleting files / directories.
