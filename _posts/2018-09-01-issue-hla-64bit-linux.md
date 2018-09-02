---
layout: post
title: "Getting HLA compiler on 64bit Linux"
date: 2018-09-01 21:00:00
published: true
comments: true
tags: hla issue closed
---

How to get Randal Hyde's xi386 HLA compiler working on 64bit Linux.

Please note: at this time I haven't quite got markdown ordered lists to work for me, hopefully that will get fixed in the near future. For now, just go through the steps sequentially.

0. Get the code
  - Go to the [author's homepage][hla-homepage].
  - Download the taballs titled `HLA for Linux` and `HLA Stdlib Source Code for Linux`. You can save these wherever, like `~/Desktop`.
  - Now you need to extract the tarballs. you can run the commands:
  
    {% highlight bash %}
    tar -xvf linux.hla.tar.gz
    tar -xvf linux.hlalib.tar.gz
    {% endhighlight %}

  - This will extract both archives' contents into a folder in the current directory: `./usr/hla/*` (ie. `~/Desktop/usr/hla`).
  - Optional: Here, the HLA author recommends you set permissions on the HLA files to 'All users can read and execute'. Unless you have multiple users on your linux install this step isn't really necessary, but for completion's sake you can use this command to accomplish this:
  
    {% highlight bash %}
    chmod -R 555 ./usr/hla
    {% endhighlight %}

  - NOTE: Make sure to type the command correctly!! otherwise you might end up changing permissions on files that don't need to be changed; don't miss the period in the path! It means 'current directory'.
  - The next step is to get the hla binaries into your system path so you can simply type 'hla file' to compile your programs:
  
1. Type the following command to copy the HLA compiler source code and binaries to your Unix System Resources (/usr/) directory:

    {% highlight bash %}
    cp -r ./usr/hla /usr/
    {% endhighlight %}

2. Optional, but recommended: The author recommends this step if you prefer a 'Unix-like' environment; it copies the binaries to `/usr/local/bin`:
  
    {% highlight bash %}
    cd /usr/hla
    {% endhighlight %}

  - Move current destination to where we copied the binaries and source files in last step.
    
    {% highlight bash %}
    cp delete hla hlacmp hlaparse /usr/local/bin
    {% endhighlight %}

  - This copies the executable binaries to a folder that normally stores user-compiled programs. This folder should be in your system path, so your shell (typically bash) should find it with little effort.
  
3. If you didn't perform the optional last step, or if you're on an atypical setup, or if you simply want the HLA compiler in a specific directory, then you can add the location of the executables to your system path. The process for this is out of the scope of this how-to, I'll assume if you go this route then you know what you're doing anyway and can figure out how to append a specific directory to your system path.

4. Now you should set some environment variables:
  - open the run commands file in your home directory. For most people, this is `~/.bashrc`. You can figure out which shell you're using with the command `echo $SHELL` if you have a different shell, you can consult it's documentation to figure out how to add environment variables if the following doesn't work.
  - at the bottom of `.bashrc` (or whatever shell you're configuring) add the lines:
     
    {% highlight bash %}
    hlalib=/usr/hla/hlalib
    export hlalib
    hlainc=/usr/hla/include
    export hlainc
    {% endhighlight %}

  - Optional: add a temp directory, but make sure `/tmp` exists:
  
    {% highlight bash %}
    hlatemp=/tmp
    export hlainc
    {% endhighlight %}

  - Save the file and 'activate' it with:
     
    {% highlight bash %}
    source .bashrc
    {% endhighlight %}

  - tip: if that doesn't work, try restarting your session (log out or restart the machine).
  
5. HLA should be properly installed now, type the following into your terminal to confirm: `hla -?`
  - if a help message gets printed out, congrats! you did it! However, if you're on a 64 bit OS there is still one more important step before you can compile programs.

6. The author doesn't mention this, but it's crucial for most people running on modern PCs. The HLA compiler library source code was compiled for 32bit architecture, if you are on a 32bit machine you shouldn't need this step. If you're on a 64bit machine (most computers nowadays) running a raw `hla file.hla` command will probably print out a bunch of linker errors. They look somehting like `ld: system architecture input source file.o is for i386`.
  - Explanation from th bottom of [this page][64bit-hla] (optional reading):

    >The thing is; on x64 systems ld tries to produce x64 output at its default. Since at its current state hla outputs x86 compatible code and provides x86 libraries, ld simply prints those irritating lines.  
    >The solution resides in a very cleverly figured switch of hla; the "-l". What this switch does is simply to pass its argument to ld. But, if you try to pass it in a "hla -l -melf_i386 -v helloWorld" format hla will prompt an error since it doesn't have a "-m" switch. As it is stated in hla's help; this switch's argument needs to be in the "-lxxxxx" format where "xxxxx" corresponds to the linker parameter. Similarly a command as "hla -lm elf_i386 -v helloWorld" is false, because the "elf_i386" part of it is recognized as an input file by the hla. Again, "hla -l-melf_i386 -v helloWorld" also doesn't function as intended because this time ld will be angry since it doesn't recognize the "option '--melf_i386'". The reason to it is that the argument of this switch is passed to ld with a minus sign prefixed to it.  
    > And about this "-melf_i386". "-m" switch of ld configures the "emulation mode". To be honest I don't know what this means accurately but it does work!  
    > The correct command is;  
    > `<user>@<user>-GA-770TA-UD3:/usr/local/samples/hla$ hla -lmelf_i386 -v helloWorld`  
  
  - In short, you want to run the hla binary with the `-lmelf_i386` flag, you can make life easier on yourself by adding an alias to your shell config file (.bashrc):
  
    {% highlight bash %}
    alias hla='hla -lmelf_i386'
    {% endhighlight %}

  - save and run `source .bashrc`
  - You might need to restart your session after editing this file. `source` can give mixed results (it didn't work for me).
    
7. Verify the environment has been set up by compiling a simple hello world program: 

    {% highlight bash %}
    `cd ~/Desktop`
    `mkdir hw`
    `cd hw`
    `touch hw.hla`
    {% endhighlight %}

  - Place this code in the file:
  
    {% highlight c %}
    program HelloWorld;
    #include( "stdlib.hhf" )

    begin HelloWorld;

        stdout.put( "Hello, World of Assembly Language", nl );

    end HelloWorld;
    {% endhighlight %}

  - run: `hla -v hw`
  - this should print out a success message that looks like this:
    
    ```
    HLA (High Level Assembler)
    Use '-license' to see licensing information.
    Version 2.16 build 4409 (prototype)
    ELF output
    OBJ output using HLA Back Engine
    -test active

    HLA Lib Path:     /usr/hla/hlalib/hlalib.a
    HLA include path: /usr/hla/include
    HLA temp path:    /tmp
    Files:
    1: hw.hla

    Compiling 'hw.hla' to 'hw.o'
    using command line:
    [hlaparse -LINUX -level=high  -v -test "hw.hla"]

    ----------------------
    HLA (High Level Assembler) Parser
    use '-license' to view license information
    Version 2.16 build 4409 (prototype)
    -test active
    File: hw.hla
    Output Path: ""
    hlainc Path: "/usr/hla/include"
    hlaauxinc Path: ""
    Compiler generating code for Linux OS
    Back-end assembler: HLABE
    Language Level: high

    Assembling "hw.hla" to "hw.o"
    HLAPARSE assembly complete, 48347 lines,   0.057 seconds,  846708 lines/second
    ------------
    HLA Back Engine Object code formatter

    HLABE compiling 'hw.hla' to 'hw.o'
    Optimization passes: 3+2
    ----------------------
    Linking via [ld   -melf_i386   -o "hw"   "hw.o" "/usr/hla/hlalib/hlalib.a"]

    ========================================
         HLA Compilation Complete
    ========================================
    ```

8. If this runs with no problems, then congrats!! you've successfully installed the High Level Assembly compiler for use with Linux 64bit systems. Leave questions in the comments and I'll do my best to help out. I'm considering adding a section for windows installs too if needed.
    
    - This guide is subject to edits and fixes! Feel free to suggest any, thanks!

    - For more information you can read the [Author's installation guide here][hla-homepage].
    
[hla-homepage]: http://www.plantation-productions.com/Webster/HighLevelAsm/LInuxDownload.html
[64bit-hla]: http://www.masmforum.com/board/index.php?PHPSESSID=8d46cd4ecb1688be429ab49694ec53e6&topic=17138.0;wap2
