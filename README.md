# CobaltStrike C2 - Tools - InlineExecute-Assembly - WriteUp

> Austin Lai | November 10th, 2022

---

## Table of Contents

<!-- TOC -->

- [CobaltStrike C2 - Tools - InlineExecute-Assembly - WriteUp](#cobaltstrike-c2---tools---inlineexecute-assembly---writeup)
    - [Table of Contents](#table-of-contents)
    - [Disclaimer](#disclaimer)
    - [Description or Introduction](#description-or-introduction)
    - [Evaluate InlineExecute-Assembly Usability](#evaluate-inlineexecute-assembly-usability)

<!-- /TOC -->

<br />

## Disclaimer

This or previous tool is for Educational purpose ONLY. Do not use it without permission. The usual disclaimer applies, especially the fact that me (Austin) is not liable for any damages caused by direct or indirect use of the information or functionality provided by these programs. The author or any Internet provider bears NO responsibility for content or misuse of these programs or any derivatives thereof. By using these programs you accept the fact that any damage (data loss, system crash, system compromise, etc.) caused by the use of these programs is not Austin responsibility.

<br />

## Description or Introduction

<!-- Description -->

[InlineExecute-Assembly](https://github.com/anthemtotheego/InlineExecute-Assembly) created by [anthemtotheego](https://github.com/anthemtotheego) is a proof of concept Beacon Object File (BOF) that allows security professionals to perform in process .NET assembly execution as an alternative to Cobalt Strikes traditional fork and run execute-assembly module.

In this write up; we going to test and understand how it can be used with cobaltstrike along with `Seatbelt`.

<!-- /Description -->

## Evaluate InlineExecute-Assembly Usability

First of all, we can clone the repo down.

```
git clone https://github.com/anthemtotheego/InlineExecute-Assembly.git
```

There is ready to use Beacon Object File located at `inlineExecuteAssembly` directory.

Of course in certain case, you can also manually compile and create your own version.

Now, let's load the `cna` (that is located at `inlineExecuteAssembly` directory) into cobaltstrike.

Once beacon up, we can use below beacon command below to execute `Seatbelt`:

```
inlineExecute-Assembly --dotnetassembly C:\Users\user\Desktop\inlineExecuteAssembly\Seatbelt.exe --assemblyargs AntiVirus
```

If you encountered error below:

```
Process refusing to load v2.0.50727 CLR version.  Try running an assembly that requires a differnt CLR version.
```

**It's mean the victim Windows unable to load DotNet lower than 4.0**

**This is because most updated Windows prohibited DotNet 2.0 or 3.5**

Ensure you have the `Seatbelt` executable compiled with DotNet 4.5.
