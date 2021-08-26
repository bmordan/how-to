# how-to
yep how to do all the things

## Rudy version manager

```
brew install gnupg
curl https://raw.githubusercontent.com/rvm/rvm/master/binscripts/rvm-installer | bash -s stable
source /Users/bernardmordan/.rvm/scripts/rvm
rvm list
```
## Ubuntu watcher limits

https://github.com/guard/listen/wiki/Increasing-the-amount-of-inotify-watchers#the-technical-details

Listen uses inotify by default on Linux to monitor directories for changes. It's not uncommon to encounter a system limit on the number of files you can monitor. For example, Ubuntu Lucid's (64bit) inotify limit is set to 8192.

You can get your current inotify file watch limit by executing:

`$ cat /proc/sys/fs/inotify/max_user_watches`

When this limit is not enough to monitor all files inside a directory, the limit must be increased for Listen to work properly.

You can set a new limit temporary with:

`$ sudo sysctl fs.inotify.max_user_watches=524288`
`$ sudo sysctl -p`

If you like to make your limit permanent, use:

`$ echo fs.inotify.max_user_watches=524288 | sudo tee -a /etc/sysctl.conf`
`$ sudo sysctl -p`

You may also need to pay attention to the values of max_queued_events and max_user_instances if Listen keeps on complaining.

## node-gyp stops working

After a MAC OS update.

```
sudo rm -rf  /Library/Developer/CommandLineTools
xcode-select --install
```
