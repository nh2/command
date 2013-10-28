command
=======

This is a standalone version of the powerful and intuitive command line functions present in the [Shake](http://hackage.haskell.org/package/shake) build system (so that they work in plain `IO`).

They are intended as an easy-to-remember, easy-to-use alternative to the [System.Process](hackage.haskell.org/package/process/docs/System-Process.html) functions.


Examples
--------

The function with most convenience is `cmd`.

```haskell
cmd "gcc -c myfile.c"     -- compile a file, throwing an exception on failure
```

`cmd` understands what you want to do using type inference.

```haskell
Stdout out <- cmd "gcc -MM myfile.c"                   -- run a command, recording the output
Exit c <- cmd "gcc -c" [myfile]                        -- run a command, recording the exit code
(Exit c, Stderr err) <- cmd "gcc -c myfile.c"          -- run a command, recording the exit code and error output
cmd (Cwd "generated") "gcc -c" [myfile] :: Action ()   -- run a command in a directory
```


Credit
------

All credit goes to the [Shake](http://hackage.haskell.org/package/shake) author!

I hope he'll take it over as a standalone project.
