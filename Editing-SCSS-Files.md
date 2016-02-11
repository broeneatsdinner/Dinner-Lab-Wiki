1. Open iTerm2 (or terminal)
2. Change directory to the `/_` directory
3. Run `sass --watch scss:css --style compressed`
4. Edit files in the `/_/scss` directory

If you want to create a bash alias to automatically associate typing `dinnerlab-sass` with the above command, perform the following:
- Open iTerm2 (or terminal)
- Type `cd` to change to your home directory
- Type `nano .bash_profile`
- Append to the end of the file the following:
```
alias dinnerlab-sass='sass --watch scss:css --style compressed'
```
- Restart your terminal program.

***

**Some further reading, on what the various flags to for SASS**
#### Different Sass Output Styles
https://web-design-weekly.com/2014/06/15/different-sass-output-styles/