1. Open iTerm2 (or terminal)
2. Change directory to the `/_` directory
3. Run `sass --watch scss:css --style compressed`
4. Edit files in the `/_/scss` directory

If you want to create a bash alias to automatically associate typing `dinnerlab-sass` with the above command, perform the following:
1. Open iTerm2 (or terminal)
2. Type `cd` to change to your home directory
3. Type `nano .bash_profile`
4. Append to the end of the file the following:
```
sass --watch scss:css --style compressed
```
5. Restart your terminal program.

Some further reading, on what the various flags to for SASS:
https://web-design-weekly.com/2014/06/15/different-sass-output-styles/