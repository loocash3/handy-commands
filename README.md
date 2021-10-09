# Useful programmer knowledge

## GIT

### Removing old branches

```shell script
git remote prune origin
git branch -vv | grep 'origin/.*: gone]' | awk '{print $1}' | xargs git branch -d
```

or

```shell script
git fetch --prune && git branch -vv | grep 'origin/.*: gone]' | awk '{print $1}' | xargs git branch -D
```

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

### Creating private dependencies

package.json
```json
{
  "private": true,
  "workspaces": ["workspace-a", "workspace-b"]
}
```

then 

```shell script
yarn install
```

### Run audit

```shell script
yarn audit [--level info|low|moderate|high|critical]
```

## JavaScript

### Intl

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl

### Fetch API

https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

### Service worker API

https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API

### Web Animations API

https://developer.mozilla.org/en-US/docs/Web/API/Web_Animations_API

### Web Components

https://developer.mozilla.org/en-US/docs/Web/Web_Components

### Web RTC

https://developer.mozilla.org/en-US/docs/Web/API/WebRTC_API

### WebSocket API

https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API


## Shell commands

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