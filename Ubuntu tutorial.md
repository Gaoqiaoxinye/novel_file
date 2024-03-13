** This is a tutorial for Linux beginners.**

** Paremeters**

* After we opened a Linux, specifically Ubuntu, shell, we could set parameters as the following codes:*
```
racey@racey-virtual-machine:~/bin$ FOO=EzeeLinux
racey@racey-virtual-machine:~/bin$ echo $FOO
```
EzeeLinux
* The parameter could conserve the value of the parameter as long as the shell exists.*
```
racey@racey-virtual-machine:~/bin$ TIME="$(date)"
racey@racey-virtual-machine:~/bin$ echo $TIME
```
2024年 03月 13日 星期三 16:23:34 CST
```
racey@racey-virtual-machine:~/bin$ echo $TIME
```
2024年 03月 13日 星期三 16:23:34 CST

* One thing that has to be mentioned is that once the parameter once created, the value will be preserved, so you can find that the output of two codes shares the same value.*

** Functions**

* The following is an easy function model:*
```
!/bin/bash


# These are codes available for specific functions.

# Set BASH to quit script and exit on errors:

set -e

# Functions:

update() {
# This is a typical type of function format.
echo "Starting full system update..."
sudo apt-get update
sudo apt-get dist-upgrade -yy

}
# The above is the body of the function

clean(){
echo "Cleaning up..."
sudo apt-get autoremove -yy
sudo apt-get autoclean

}

leave() {
echo "-------------------"
echo "-Updaate Complete!-"
echo "-------------------"
exit

}

up-help() {

cat << _EOF_

I'm sorry, I don't think there is any help for you!

_EOF_
}

# The "cat <<"means that it would print the following contents up to the token right of it, with here it
# being _EOF_ on your screen.


# Execution

# Tell 'em who we are...

echo "Up -- Debian/Ubuntu Update Tool (Version 1.0)"

# Update and clean:

if ["$1" == "--clean"]; then
    update
    clean
    leave
fi

if ["$1" == "--help"]; then
    up-help
    exit
fi

# Check for invalid argument

if [ -n "$1" ]; then
    echo "Up error: Invalid argument. Try 'up --help for more info." >&2
    exit 1
fi

update
leave

```
