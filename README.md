# FTPY Beta

A super-simple, no-frills FTP client for the command line written in Python. No `sudo` privileges needed to install or use. Works on *Nix, Mac OS X, and Windows systems and with Python versions 2 and 3.

## Beta Disclaimer

This is a very early version of FTPY. As such, there are still uncaught exceptions and potential bugs that occur when using FTPY. So far in my usage, I haven't encountered any bugs but I have seen a few uncaught exceptions. Use at your own risk.

## Installation

Drop `ftpy` into a directory on your path. One easy way to do this is by cloning the repository and moving the Python script wherever you want it:

```
$ git clone https://github.com/mshmoustafa/FTPY.git
$ mv FTPY/ftpy dir/in/your/PATH
```

## Uninstallation

Delete `ftpy` to uninstall the script. Note that FTPY does not install or create any other files, so uninstallation really does amount to deleting the `ftpy` script.

```
$ rm ftpy
```

## Usage

Run the script in Python:

```
$ python ftpy
```

Log into your host, username, and password at the prompts:

```
$ Host name (URL): myhost.com
$ Username (blank for anonymous): myusername
$ Password (blank for anonymous): 
```

Once logged in, you can type in any of the usual FTP commands.

Note that you must start this script in the same directory as the files that you want to upload.  This is because FTPY does not have 'lcd' and 'lls' commands to work with the current directory.

## Commands

### Navigation

#### ls - List files in directory

`ls` lists the files in the current directory.

```
Command: ls
```

#### cd - Change working directory

`cd` changes to another directory:

```
Command: cd public_html
```

`cd ..` goes up one directory.

#### pwd - Print the current working directory

```
Command: pwd
```

### Transfering Files

#### get - Download a file from the server

Works with binary and ascii files.

```
Command: get index.html
```

Note on binary vs. ascii: `get` currently uses the binary transfer mode for all downloads.

#### put - Upload a file to the server

Works with binary and ascii files.

```
Command: put myimage.png
```

Note on binary vs. ascii: `put` uses the binary transfer mode for all uploads.

### Server Manipulations

#### mv - Move or rename file or directory on server

```
Command: mv page.html subdirectory/page.html
Command: mv old_name.html new_name.html
```

#### rm - Delete file on server

Does not work on directories. See `rmdir`.

```
Command: rm deleteme.html
```

#### mkdir - Make a directory on the server

```
Command: mkdir new_directory
```

#### rmdir - Delete a directory on the server

The directory must be empty to be deleted.

```
Command: rmdir empty_dir
```

### Miscellaneous

#### quit - Close the connection to the server

Nicely closes the connection to the FTP server.

```
Command: quit
```

## License

FTPY is licensed with the MIT license. Enjoy.

## History

One day I was using my ASUS C200 Chromebook and I needed to access my web server using FTP. So I opened up a terminal, typed in `ftp` and hit enter. To my surprise, I got this message: `bash: ftp: command not found`. I looked around for some FTP clients for use with my Chromebook, but I couldn't find any good ones to use. I could have switched over to my Xubuntu chroot using [crouton](https://github.com/dnschneid/crouton), but I wanted a solution I could use in Chrome OS. So I decided to make my own FTP client using Python's excellent [ftplib](https://docs.python.org/2/library/ftplib.html) module. The goal is to make the client very easy to use in almost any environment.
