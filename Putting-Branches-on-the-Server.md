##### Pulling `develop` or `release-[x]` or `ferrari-[x]` onto the development server.
The `dev1.dinnerlab.com`, `release1.dinnerlab.com` and `ferrari1.dinnerlab.com` domains all reside on the same server.

The server has an IP address of `23.92.31.20`.

In order to log in to this server, you can SSH into it with your username (usually your first name), and your password. If you forget your first name, you're out of luck, but if you forget your password, you can contact Broen in order to reset it.

Once you have logged in, the first thing you need to do is "switch" to the `dinnerlab` user. That way, you can pull the various branches onto the server by using the `dinnerlab` user, which has SSH keypair authentication between the server and the GitHub repository itself. This is done by:
```
broen@development:~$ switch
dinnerlab@development:~$ whoami
dinnerlab
```
Note that running the `switch` command may ask for a password, and if it does, the password is your password that you use to SSH into the system with your username (not a shared password that's used for the `dinnerlab` user). Once you're the `dinnerlab` user (and you can verify that you're the `dinnerlab` user by typing `whoami`), the directory structure looks like this:
```
dinnerlab@development:~$ ll
total 4.0K
drwxr-xr-x 7 dinnerlab dinnerlab 4.0K Sep  1 04:43 domains
lrwxrwxrwx 1 dinnerlab dinnerlab   55 Apr  2 01:37 dev1 -> /home/dinnerlab/domains/dev1.dinnerlab.com/public_html/
lrwxrwxrwx 1 dinnerlab dinnerlab   48 May 15 19:11 dev1logs -> /home/dinnerlab/domains/dev1.dinnerlab.com/logs/
lrwxrwxrwx 1 dinnerlab dinnerlab   59 Sep  1 04:52 ferrari1 -> /home/dinnerlab/domains/ferrari1.dinnerlab.com/public_html/
lrwxrwxrwx 1 dinnerlab dinnerlab   52 Sep  1 04:52 ferrari1logs -> /home/dinnerlab/domains/ferrari1.dinnerlab.com/logs/
lrwxrwxrwx 1 dinnerlab dinnerlab   59 Jul 14 18:07 release1 -> /home/dinnerlab/domains/release1.dinnerlab.com/public_html/
lrwxrwxrwx 1 dinnerlab dinnerlab   52 Sep  1 04:53 release1logs -> /home/dinnerlab/domains/release1.dinnerlab.com/logs/
dinnerlab@development:~$
```
Note that directories like `dev1` and `dev1logs` are symbolic links to `/home/dinnerlab/domains/dev1.dinnerlab.com/public_html/` and `/home/dinnerlab/domains/dev1.dinnerlab.com/logs/` respectively, and can be used as shortcuts to get to the HTML document root and logs directories for a particular domain quickly.

###### Pulling to dev1.dinnerlab.com
Once you've switched to the `dinnerlab` user, you can enter the HTML document root for `dev1.dinnerlab.com` using the symbolic link and then run `git pull` like this:
```
dinnerlab@development:~$ cd dev1
dinnerlab@development:~/dev1$ git pull
remote: Counting objects: 465, done.
remote: Compressing objects: 100% (59/59), done.
remote: Total 465 (delta 213), reused 182 (delta 182), pack-reused 224
Receiving objects: 100% (465/465), 438.72 KiB, done.
Resolving deltas: 100% (335/335), completed with 74 local objects.
From github.com:dinnerlab/dinnerlab
   36add69..fde4fcd  develop    -> origin/develop
   107f275..8057bb3  feature-ferrari -> origin/feature-ferrari
 * [new branch]      feature-magnus-project -> origin/feature-magnus-project
   c7776be..a9a4af8  release-2.2.2 -> origin/release-2.2.2
Merge made by the 'recursive' strategy.
 _/includes/head.php |    5 +----
 1 file changed, 1 insertion(+), 4 deletions(-)
dinnerlab@development:~/dev1$
```

---

##### Tagging a version number onto `master`.

###### Listing Tags
Listing the available tags in Git is straightforward. Just type `git tag`:
```
git checkout master
git tag
```
This command lists the tags in alphabetical order; the order in which they appear has no real importance.

###### Creating Tags
In the following example, the version number is `2.2` and the codename is `New Durham Tadpole`
```
git tag -a v2.2 -m 'New Durham Tadpole'
```

###### Pushing Tags
By default, the git push command doesn't transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them. This process is just like sharing remote branches – you can run git push origin [tagname].
```
git push origin v2.2
```