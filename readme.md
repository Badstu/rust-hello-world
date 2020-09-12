# vscode config for rust

## rust shell
```shell
cargo new greeting
cd ./greeting
cargo build
cargo run
```

## vscode

```shell
mkdir `.vscode`
cd .vscode
touch launch.json task.json
``` 

**task.json**
```json
{ 
    "version": "2.0.0", 
    "tasks": [ 
        { 
            "label": "build", 
            "type": "shell", 
            "command":"cargo", 
            "args": ["build"] 
        } 
    ] 
}
```

**launch.json**
```json
{ 
    "version": "0.2.0", 
    "configurations": [ 
        {
            "name": "(Windows) Launch",
            "type": "cppvsdbg",
            "request": "launch",
            "program": "cmd",
            "args": [
                "/C",
                "${workspaceFolder}/target/debug/${workspaceFolderBasename}.exe",
                "&",
                "pause"
            ],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole":true,
            
            "preLaunchTask": "build"
        },
        { 
            "name": "(gdb) Launch", 
            "type": "cppdbg", 
            "request": "launch", 
            "program": "${workspaceFolder}/target/debug/${workspaceFolderBasename}.exe", 
            "args": [], 
            "stopAtEntry": false, 
            "cwd": "${workspaceFolder}", 
            "environment": [], 
            "externalConsole": false, 
            "MIMode": "gdb", 
            "miDebuggerPath": "E:\\mingw-w64\\x86_64-8.1.0-posix-seh-rt_v6-rev0\\mingw64\\bin\\gdb.exe", 
            "setupCommands": [ 
                { 
                    "description": "为 gdb 启用整齐打印", 
                    "text": "-enable-pretty-printing", 
                    "ignoreFailures": true 
                } 
            ],
            "preLaunchTask": "build"
        } 
    ] 
}
```