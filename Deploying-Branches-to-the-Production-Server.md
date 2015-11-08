#### Deploying `master` onto the production server.

##### First things first.
The `dinnerlab.com` domain resides on its own server.

The server has an IP address of `45.56.122.231`.

In order to log in to this server, you can SSH into it with your username (usually your first name), and your password. If you forget your first name (which your mother gave to you), you're out of luck. But, if you forget your password, you can contact <a href="mailto:bwestberg@dinnerlab.com" target="_self">Broen</a> in order to reset it.

Once you have logged in, the first thing you need to do is "switch" to the `dinnerlab` user. That way, you can pull the various branches onto the server by using the `dinnerlab` user, which has SSH keypair authentication between the server and the GitHub repository itself. This is done by:
```
broen@web1:~$ switch
dinnerlab@web1:~$ whoami
dinnerlab
```
Note that running the `switch` command may ask for a password, and if it does, the password is your password that you use to SSH into the system with your username (not a shared password that's used for the `dinnerlab` user). Once you're the `dinnerlab` user (and you can verify that you're the `dinnerlab` user by typing `whoami`), the directory structure looks like this:
```
dinnerlab@web1:~$ ll
total 4.0K
drwxr-xr-x 5 dinnerlab dinnerlab 4.0K Jun 29 16:42 domains
lrwxrwxrwx 1 dinnerlab dinnerlab   49 Mar 25 19:51 public_html -> /home/dinnerlab/domains/dinnerlab.com/public_html
dinnerlab@web1:~$
```
Note that directories like `public_html` are symbolic links to `/home/dinnerlab/domains/dinnerlab.com/public_html/`, and can be used as shortcuts to get to the HTML document root quickly.

---

##### Deploying to dinnerlab.com
Once you've logged in, and switched to the `dinnerlab` user, you can enter the HTML document root for `dinnerlab.com` using the symbolic link and then run `git pull` like this:
```
dinnerlab@web1:~$ cd
dinnerlab@web1:~$ pwd
/home/dinnerlab
dinnerlab@web1:~$ cd public_html
dinnerlab@web1:~/public_html$ git pull
remote: Counting objects: 457, done.
remote: Compressing objects: 100% (59/59), done.
remote: Total 457 (delta 209), reused 178 (delta 178), pack-reused 220
Receiving objects: 100% (457/457), 435.23 KiB, done.
Resolving deltas: 100% (332/332), completed with 67 local objects.
From github.com:dinnerlab/dinnerlab
   4ee6f0b..fde4fcd  develop    -> origin/develop
   ad1f7fb..8057bb3  feature-ferrari -> origin/feature-ferrari
 * [new branch]      feature-magnus-project -> origin/feature-magnus-project
   19ea817..a9a4af8  release-2.2.2 -> origin/release-2.2.2
Already up-to-date.
dinnerlab@web1:~/public_html$
```

Any changes that have been made to the `master` branch will now be live at `dinnerlab.com`