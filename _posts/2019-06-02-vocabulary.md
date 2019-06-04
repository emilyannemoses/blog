---
layout: post
title:  "Vocabulary"
---

I'd never travel to an other country without learning the basic vocabulary of the host language, therefore I'd never begin teaching you to code without first giving you necessary words to navigate our new world.

This list will go over definitions of general computer hardware and software concepts. Part two will review more specific programming language terminology.

-   <details>
    <summary>hardware</summary>
    <br>
    All of the physical devices or components that a computer is made of. This includes the CPU, main memory and secondary storage devices.
    <br><br>
    </details>
    - <details>
        <summary>central processing unit (CPU)</summary>
        <br>
        The Central Processing Unit is the part of a computer that actually runs programs. It's the most important component in a computer; without it, your computer could not run software.
        <br><br>
        CPUs are small chips known as <i>microprocessors</i>.
        <br><br>
        </details>
    - <details>
        <summary>main memory</summary>
        <br>
         The main memory is where the computer stores a program while the program is runnig, along with the data that the pogram is working with. This is refered to as RAM, or random access memory.
         <br><br>
         The CPU is able to quickly access data stored at any random location in RAM. RAM is volitile; it is only used for temporary storage. When the computer is turned off, the contents of RAM are erased.
        <br><br>
        </details>
    - <details>
        <summary>secondary storage devices</summary>
        <br>
        This type of memory holds data in your computer for long periods of time, even when there is no power to the computer. The disk drive is a common type of secondary storage. Another popular secondary storage drive is the solid state drive. External hard drives can be used as secondary storage devices as well - this includes USB (thumb) drives.
        <br><br>
        </details>
    - <details>
        <summary>input devices</summary>
        <br>
        A device that collects user input such as your computers keyboard or mouse.
        <br><br>
        </details>
    - <details>
        <summary>output devices</summary>
        <br>
        A device that produces output for the user, such as speakers, printers or monitors.
        <br><br>
        </details>
- <details>
    <summary>software</summary>
    <br>
    Everything a computer does depends on the software installed on that computer. A computer cannot do anything without software. Generally, there are to categories of software: system software and application software.
    <br><br>
    </details>
    - <details>
        <summary>system software</summary>
        <br>
        Operating systems such as Windows 10 or OSX are examples of system software. It's the most fundimental set of programs on a computer which controls the internal operations of the computer's hardware and manages all of the devices connected to the computer.
        <br><br>
        Utility programs perform a specialized task for the computer, such as a virus scanner.
        <br>
        Software development tools refer to specific programs that programmers use to create, modify and test software.
        <br><br>
        </details>
    - <details>
        <summary>application software</summary>
        <br>
        These are programs that users spend most of their time running. These include Microsoft Word, Pages, web browsers such as Chrome and installed game programs.
        <br><br>
        </details>
- <details>
    <summary>binary</summary>
    <br>
    Every computer stores data using binary - a sequence of 0s and 1s.
    <br><br>
    The only language a computer understands is machine language, so every programming language has to be eventually reduced to 0s and 1s for a computer to execute its instructions.
    <br><br>
    </details>
    - <details>
        <summary>bytes</summary>
        <br>
        Memory within your computer is divided into small storage locations called bytes. One byte can store one letter of the alphabet, or one small number. Todays computers have billions of bytes of memory.
        <br><br>
        When a piece of data is stored in a byte, the computer sets the eight bits to an on/off (1/0) pattern that represents the data.
        <br><br>
        </details>
    - <details>
        <summary>bits</summary>
        <br>
        Bits represent a binary digit. 8 bits are equal to 1 byte.
        <br><br>
        A binary number looks something like this:
        10011101 - there are eight columns and in each column is a 0 or a 1. Each column has a numerical value that we can use to calculate what integer it is.
        <br><br>
        128 | 64 &nbsp;| 32 &nbsp;| 16 &nbsp;&nbsp;|&nbsp; 8 &nbsp;|&nbsp; 4 &nbsp;| 2 &nbsp;| 1<br>
        &nbsp;1&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;0&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;0&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;1&nbsp;&nbsp;&nbsp;|&nbsp;1&nbsp;&nbsp;&nbsp;|&nbsp;1&nbsp;&nbsp;&nbsp;|&nbsp;0&nbsp;&nbsp;|&nbsp;1
          <hr>
          To know what number this is, we need to add all of the numbers that are corresponding to "1" values.
          <br>
          <pre>128 + 16 + 8 + 4 + 1 = 157</pre>
          Therefore <pre>10011101</pre> is equal to <pre>157</pre>
        <br><br>
        </details>
    - <details>
        <summary>ASCII</summary>
        <br>
        ASCII stands for the American Standard Code for Information Interchange. It is a set of 128 numeric codes that represent the English letters, punctuation marks and other characters. The ASCII code for uppercase A is 65. So, when you type an uppercase A on your computer keyboard, the number 65 is stored in memory as binary number 01000001.
        <br><br>
        In order to know which code is assigned to which character, there are plenty of charts online you can refert to. Simply Google "ASCII Table"
        <br><br>
        </details>
    - <details>
        <summary>converting negative numbers and real numbers to binary</summary>
        <br>
        Negative numbers and real numbers (such as 3.14159) cannot be represented using the simple binary numbering technique.
        <br><br>
        Computers use encoding schemes along with the binary numbering system. Negative numbers are encoded using a technique known as <i>two's complement</i> and real numbers are encoded in <i>floating point notation</i>. Since these are used to convert these numbers to binary format, software developers have to account for floating point number precision problems in their programs.
        <br><br>
        </details>
- <details>
    <summary>CPU lifecycle</summary>
    <br>
    Known as the <i>fetch-decode-execute cycle</i>, the lifecycle begins when the CPU executes instructions in a software program and it repeats these steps for each instruction in the software pogram.
    <br><br>
    </details>
    - <details>
        <summary>Fetch</summary>
        <br>
        The first step is to fetch, or read, the next instructino from memory into the CPU.
        <br><br>
        </details>
    - <details>
        <summary>Decode</summary>
        <br>
        In this step the CPU decodes the instruction that was just fetched from memory, to determine which operation it should perform.
        <br><br>
        </details>
    - <details>
        <summary>Execute</summary>
        <br>
        The last step in the cycle is to execute, or perform, the operation.
        <br><br>
        </details>
- <details>
    <summary>High Level Languages</summary>
    <br>
    High level programming languages are the languages we use most often today to write software programs. The following list is some of the most popular.
    <br><br>
    </details>
    - Python
    - C++
    - Java
    - Ruby
    - JavaScript
- Low Level Languages
    - Assembly Languages: each brand of CPU (ex: IBM, Intel) has its own assembly language which is assembled into machine language
    - A language is considered low-level because it is so close in nature to machine language. Programmers do not write programs in low-level languages.
- <details>
    <summary>Compilers and Interpreters</summary>
    <br>
        Because the CPU understands only machine language instructions, programs that are written in high level languages must be translated into machine language. Depending on the language, a compiler or an interpreter is necessary to make the translation.
        <br><br>
        A <i>compiler</i> translates a high level language into a separate machine language program or file, that file can then be executed.
        <br><br>
        An <i>interpreter</i> translates and executes high-level code and the conversion to machine language occurs "behind the scenes" as the program is being executed.
    <br><br>
    </details>