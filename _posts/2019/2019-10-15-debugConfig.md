---
published: true
title: VSCode C++ debug configuration
category: 杂项/Miscellany
tags: VSCode
layout: post
math: true
output: pdf_document
---

<!-- more -->

task.json

```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "task",
      "type": "shell",
      "command": "g++",
      "args": [
        "-g",
        "${file}",
        "-o",
        "${fileDirname}/${fileBasenameNoExtension}.exe"
      ],
      "group": {
        "kind": "build",
        "isDefault": true
      }
    }
  ]
}
```

launch.json

```json
{
  "version": "0.2.0",
  "configurations": [
    {
      "name": "C++ Launch",
      "type": "cppdbg",
      "request": "launch",
      "program": "${workspaceRoot}/${fileBasenameNoExtension}.exe",
      "stopAtEntry": false,
      "externalConsole": true,
      "cwd": "${workspaceFolder}",
      "preLaunchTask": "task",
      "windows": {
        "MIMode": "gdb",
        "miDebuggerPath": "replace this with your gdb path"
      }
    }
  ]
}
```

