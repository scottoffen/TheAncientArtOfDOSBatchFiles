*[The Ancient Art Of Dos Batch Files](./0-0-0-Table-Of-Contents.md) > [Basics](./1-0-0-Basics.md)*

# The Environment And Its Variables #

DOS sets aside a small area of memory (called the environment space) to keep track of information that can vary because it's user definable. Examples of such information are the system prompt and the search path.

The variable information is stored in named environment variables. So, for example, the system prompt configuration is stored in the variable called `PROMPT`. By default, it contains `$p$g` but this can be changed by the user.

The `SET` command allows the user to display the current contents of the environment space and also to create user-defined and named environment variables.

The default capacity of the environment is 160 bytes for earlier versions of DOS, 256 bytes for the most recent versions. This capacity can be expanded throughout the use of the SHELL command in the `config.sys` file. Maximum size is 32kb, but most users work with .05 - 2kb.

The capacity of the environment defines the maximum number of bytes that can be present in the environment, but DOS expands the environment as necessary for holding the values of additional environment variables.

However, this is true only when there are no memory resident programs loaded in memory. Once a memory resident program is loaded, DOS cannot expand the capacity of the environment beyond 128 bytes, since memory resident programs are loaded above the memory area earmarked for the environment. Therefore, using an expanded environment is essential if you are running memory resident programs and also want to set a long directory path or set the value of other custom environment variables.

With an expanded environment, many variables can be given values using the SET command and the value of those variables can be called up for use when needed. Shown below are command lines: one to be placed in the `config.sys` file and the othe to be placed in your `autoexec.bat`:

| File         | Syntax                        |
|--------------|-------------------------------|
| CONFIG.SYS   | `shell=command.com /e:512 /p` |
| AUTOEXEC.BAT | `set comspec=c:\command.com`  |

The `config.sys` expands your environment to 512 bytes and the `autoexec.bat` entry then sets the value of `COMSPEC` (the command processor environment variable) to the `command.com` ensuring that whenever a program needs to access `command.com` it will always be found.

Your `autoexec.bat` file should also set the value of the PATH environment variable. Either of the two command lines shown below will set your PATH to the indicated value:

```
set path=c:\;c:\bat;c:\dos;c:\util
```

or 

```
path=d:\;c:\bat;c:\dos;c:\util
```

Use of the SET command is not necessary for either the PATH or PROMPT environment variables but all the others require it.

---

<div>
	<span style="float:left;">[Previous](./1-0-0-Basics.md)</span>
	<span style="float:right;">[Next](./1-2-0-IO-Redirection.md)</span>
</div>