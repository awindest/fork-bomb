# How to crash your computer

<img width="789" alt="fork-bomb" src="https://github.com/user-attachments/assets/633748a8-0726-4c00-b497-849b35eb2680" />

## or what is known as a fork bomb

An insanely simple way to crash your computer from the command prompt.

The Bash command ```:(){ :|:& };:``` is a fork bomb — a type of denial-of-service attack that exploits the system by rapidly creating a large number of processes, overwhelming system resources and effectively making the machine unresponsive.

## 🧨 What the Command Does

```
:(){ :|:& };:
```

It defines a function named ```:``` that recursively calls itself twice, once in the background, and then executes the function. This leads to exponential growth in the number of processes.

## 🔍 Breakdown of Each Part

Let’s break it down character by character:

<img width="789" alt="fork-bomb1" src="https://github.com/user-attachments/assets/49db30b0-91a3-4e01-b4d0-a349412619af" />


### 1. ```:()```
This defines a function named : (yes, a colon is used as the function name — allowed, though unusual).

It’s the start of a function definition syntax in Bash.

<img width="789" alt="fork-bomb2" src="https://github.com/user-attachments/assets/ea4c3ae4-cb7a-4997-9ce8-adc05409a51d" />


### 2. ```{ :|:& }```
The function body. It contains:

```:``` — a call to the function itself (i.e., recursion).

```|``` — pipe: passes the output of the first function call to the input of the next.

```:``` — a second call to the function itself.

```&``` — runs the piped commands in the background, allowing the function to spawn child processes without waiting for them to finish.

<img width="831" alt="fork-bomb3" src="https://github.com/user-attachments/assets/4923eccc-ab61-4d1c-94d2-26641cf33a19" />

### 3. ```;```
Ends the function definition.

<img width="789" alt="fork-bomb4" src="https://github.com/user-attachments/assets/ee9f1e80-f690-432b-b380-02b81f95bec7" />


### 4. ```:```
Calls the function for the first time, initiating the fork bomb.

## ⚠️ Warning
Never run this command on a live or important system. It can lock up your machine requiring a reboot, and may cause data loss if unsaved work is present.

If you're experimenting in a controlled environment, you should always have:

Process limits (```ulimit```) set.

Root access disabled if unnecessary.

A method to kill processes (e.g., remote kill script, recovery shell).

## Summary

This is a cleverly obfuscated Bash fork bomb that abuses recursive function calls and background processing to quickly exhaust system resources. It’s a classic example of how seemingly simple Bash commands can be extremely powerful — and dangerous.
