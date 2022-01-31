# Useful programmer knowledge

## GIT

### ebook
https://www.git-tower.com/learn/git/ebook

### Merge vs rebase
http://www.pzielinski.com/?p=2652

### Workflows
https://www.atlassian.com/git/tutorials/comparing-workflows

### Rename branch

```shell script
git checkout <old_name>
git branch -m <new_name>
git push origin -u <new_name>
git push origin --delete <old_name>
```


### Removing old branches

```shell script
git remote prune origin
git branch -vv | grep 'origin/.*: gone]' | awk '{print $1}' | xargs git branch -d
```

or

```shell script
git fetch --prune && git branch -vv | grep 'origin/.*: gone]' | awk '{print $1}' | xargs git branch -D
```

### Multiple ssh keys on multiple repo

Add to `~/.gitconfig` or `~/.config/git/config`

```shell script
[url "git@github.com:"]
    insteadOf = https://github.com/
[url "git@github-user1:user1"]
    insteadOf = git@github.com:user1
```

and then in `~/.ssh/config`
    
```shell script    
AddKeysToAgent  yes
IdentitiesOnly yes

Host github-user1
    HostName github.com
    IdentityFile ~/.ssh/id_rsa_user1

Host *.example.com
    IdentityFile ~/.ssh/id_rsa_example
```

then replace in origin from `github.com` to `github-user1` for specific repo

## NPM

### Checking outdated dependencies

```shell script
yarn outdated
```

### Stashing changes

Stashing your work
```shell script
git stash
```

Re-applying your stashed changes
```shell script
git stash pop
```

### Yarn workspaces

```
/app
 - package.json
 - /workspace-a
   - package.json
 - /workspace-b
   - package.json
```

package.json
```json
{
  "private": true,
  "workspaces": ["workspace-a", "workspace-b"]
}
```

Adding dependency to workspace
```shell script
yarn workspace workspace-a add dependency
```

Running script in workspace from project root
```shell script
yarn workspace workspace-a command
```

Running commands on each workspace
```shell script
yarn workspaces foreach run command
```

### Run audit

```shell script
yarn audit [--level info|low|moderate|high|critical]
```

## CSS

### Flexbox
https://css-tricks.com/snippets/css/a-guide-to-flexbox/

### Gridbox
https://css-tricks.com/snippets/css/complete-guide-grid/

## JavaScript

### Usefull array functions
`includes|some|every|filter|map|reduce`

### Intl
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl

### Fetch API
https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

### Service worker API
https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API

Learn about -> https://mastery.games/serviceworkies/

### Web Animations API
https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API

### Web Components
https://developer.mozilla.org/en-US/docs/Web/Web_Components

### Web RTC
https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API

### WebSocket API
https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API

### Can I use
https://caniuse.com/

### Can I email
https://www.caniemail.com/

### Managing queues
https://optimalbits.github.io/bull/

### Node.js streams
https://devhints.io/nodejs-stream

## Process management tools

### PM2
https://pm2.keymetrics.io/docs/usage/quick-start/

## Transfering files

### SCP

Single file
```shell script
scp your_username@remotehost.edu:foobar.txt /some/local/directory

scp foobar.txt your_username@remotehost.edu:/some/remote/directory

```

Directory
```shell script
scp -r foo your_username@remotehost.edu:/some/remote/directory/bar

```

betwen servers
```shell script
scp your_username@rh1.edu:/some/remote/directory/foobar.txt \
your_username@rh2.edu:/some/remote/directory/
```


```shell script
ls | sed -n 's/\(.*\)\(20[0-2]\{1\}[0-9]\{1\}\)\([0-9]\{2\}\)\([0-9]\{2\}\)\(.*\)/mv "\1\2\3\4\5" "\/Volumes\/FotoBackup\/\2\/\2\-\3\/\1\2\3\4\5"/p' | sh
```

## Docker

### Handbook
https://www.freecodecamp.org/news/the-docker-handbook/

## Tools

### Server automation tool
https://capistranorb.com/

## Dealing with files

### Finding informations

`grep "some string" file` options

- -i - case insensitive
- -E - regex
- -v - find lines that not match
- -r - recursive in all files in directory
- -o - only print matching part


`find path -name filename`

`find . -name "*.js"`

## Server stats

### Checking disk space

`du` - disk usage

- -h - human format
- -d [level] - level of depth
- -c - total size

`du -h | sort -hr` - sorting by directory size

`du -sm .[!.]* *` - checking hidden files

### Checking free disk space

`df`

- -h - human format
