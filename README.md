# WAR_POWERS 

An application for gene deletion / duplication screening (against Human GRCh38)

## Setup

Note that the "$" prefixes are not to be typed into the shell themselves. These are short-hand characters that mean "at your shell's command-line."

### Input

Your .bam file needs to go into the same folder where the genes\_clean.txt and executable script for your operating system lives.

**NOTES:** 

* The software works with either bare ("7") or chr-prefixed ("chr7") BAMs; it will auto-detect. 

* The .bam.bai index is built automatically if missing.

### Windows

WSL and some dependencies have to be installed first. There are several ways to install WSL, but we will use the most straightforward that does not involve going to the Microsoft Store. If you _want_ to go to the microsoft store to grab WSL, that's fine (grab ubuntu or some debian-based distro for matching commands to the readme below).

For a video on how to install from the Microsoft Store, you can check [here](https://www.youtube.com/watch?v=WD7swbRpwKM). Otherwise, the instructions below assume you're using the built-in Windows shell.

1. Open a command shell by using key combo Windows + R and typing "cmd" at the prompt that appears.

2. Now you should have a command shell for windows. Within here, we can install wsl. 

**IMPORTANT!** Once this installation command starts running, allow it to finish without interruption, or you can corrupt the installation (and it can be a pita to recover from).

```bash
$ wsl --install
```

3. You may then be prompted for things like a confirmation, a username for your WSL installation, etc. Go through those prompts and be sure to remember this new username and password pair (it can be the same you use for windows login if you desire). Older installations also required a reboot, but this may no longer be necessary.

4. Once wsl is installed, update it. 

**Note:** If Windows does not automatically provide you a WSL window after the initial installation, you can easily open one by going to your Windows start bar and typing "WSL" int the search. You will see either a Blue Penguin icon or the icon for your distro (e.g. an orange square with a dotted cirlce for ubuntu). Select either and a different kind of shell window should pop up. This is your linux instance's shell.

```bash
$ sudo apt update && sudo apt-get upgrade -y
```

5. Now install samtools

```bash
$ sudo apt install samtools -y
```

### Mac

We just need to open up a terminal and install samtools.

```bash
$ brew install samtools
```

### Linux

We want to make sure everything is updated and that we can install samtools.

```bash
$ sudo apt update && sudo apt upgrade -y && sudo apt install samtools -y
```

Now you're ready to run!

## Running 

### Executable Scripts

The executable to use depends on your operating system. In the case of windows or mac, double-clicking the respective file should work; in the case of linux (or running direclty under WSL) you will have to run within the terminal.

#### **Windows**

Double-click WAR\_POWERS.bat

**Note:** You can technically run the .sh version of WAR\_POWERS from within WSL's default shell as well and follow the linux instructions below. (You know, if you're a cool kid and want to run things from the command-line.)


#### **Mac**

Double-click WAR\_POWERS.command

#### **Linux**

1. Open a shell.

2. Navigate to the location of the WAR\_POWERS.sh script (which should be in the same folder as your input bam file and genes\_clean.txt are located)

3. Run the script

```bash
$ ./WAR\_POWERS.sh
```

## Output

When sucessfully run, the software outputs the following files

* **deletion\_all\_data.tsv** - every gene + depths + call

* **deletion\_hits.tsv** - only flagged deletions / MT review

Files contain results like:

* LIKELY\_FULL\_DELETION\_OR\_MAJOR\_COPY\_LOSS - gene depth near zero
* POSSIBLE\_PARTIAL\_OR\_HET\_DELETION - gene ~half of clean flank OR genome baseline
* POSSIBLE\_DUPLICATION\_OR\_HIGH_COPY - gene above flank AND baseline
* MT_POSSIBLE\_HETEROPLASMIC\_DELETION\_REVIEW - mitochondrial gene low vs whole-MT depth
* NORMAL / NO\_CALL / NOT\_FOUND\_IN\_GENCODE / MT\_DEPTH\_NORMAL / MT\_NOT\_ASSESSED

## Gotchas

## Errors

## Reporting Issues

## Caution

This software should be used for screening / personal research only. It should not be used to diagnose or treat any condition or disease. 

Confirm any hit in IGV / with a depth + loss-of-heterozygosity check before treating it as real. Other utilities should be considered for confirming anything reported by this tool as well. 

## Disclaimer

There is no warranty of this software express or implied. No assertions, claims, or information gained as a result of using this software should be taken as medical advice, and any engagement with the software and its results is AT YOUR OWN RISK.

