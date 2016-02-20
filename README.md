EventManager
============

A type-safe event system for Unity3D based on the event listener pattern.

The code in this repository is a minor variation with added examples and tests
of the event system originally described here:
http://www.willrmiller.com/?p=87

This repository was created with Unity version 5.3.1

Features
--------

EventManager is useful when you want to keep your codebase loosely coupled.
Publishers and subscribers don't need to know anything about each other.
EventManager is not a solution for exposing callbacks in the Unity Editor,
Unity's own EventSystem may be more appropriate for that use case.

* Loosely coupled
* Type-safe
* Avoids breaking changes when new event parameters are added

Installation
------------

Install the source or build a DLL.

### Option 1: Source Installation

Copy the Assets/EventManager folder to your project's Assets folder.

#### Source and Unit Tests

NOTE: Unit tests are stored in an 'Editor' folder so they are not added to your build

    mkdir tmp
    cd tmp
    git clone https://github.com/robertwahler/EventManager
    cp -R EventManager/Assets/EventManager ~/your_unity_project/Assets/

#### Examples (optional)

    cp -R EventManager/Assets/Examples ~/your_unity_project/Assets/EventManager/

#### Record Version SHA (optional)

    git --git-dir=./EventManager/.git log --pretty=format:%h -1 > ~/your_unity_project/Assets/EventManager/VERSION

### Option 2: DLL Installation

Create a DLL and copy it to your Assets folder.  These instructions expect the
standard Mono mcs compiler.  If you need it on OS X, you can install it with
HomeBrew ```brew install mono```

    mkdir build

    mcs -recurse:'Assets/EventManager/Source/*.cs' \
        -lib:/Applications/Unity.5.3.1/Unity.app/Contents/Frameworks/ \
        -lib:/Applications/Unity.5.3.1/Unity.app/Contents/Frameworks/Managed/ \
        -r:UnityEngine \
        -r:UnityEditor \
        -target:library \
        -out:build/SDD.EventManager.dll

    mkdir Assets/Lib

    cp build/SDD.EventManager.dll ~/your_unity_project/Assets/Lib/

Testing
-------

The NUnit test framework is included in Unity 5.3 and higher.  Tests require
installation of the UnityTestTools asset for Unity 5.2 and lower.

There is no Unity hotkey for running tests. Instead, manually use this menu sequence:

    Main Menu: Window, Editor Tests Runner
    Editor Tests: Run All

Usage
-----

See Assets/Examples

License
-------

MIT, see ./LICENSE for details.
