## 在单台电脑上使用多个github账号

### Multiple SSH Keys settings for different github account
create different ssh key

`ssh-keygen -t rsa -C "jack5209@youremail.com"`

for example, new key created at:

`~/.ssh/id_rsa_jack5209`

then, add the new key as following

`ssh-add ~/.ssh/id_rsa_jack5209`

you can delete all cached keys before

`$ ssh-add -D`

finally, you can check your saved key

`$ ssh-add -l`

### Modify the ssh config

Then added

```zsh
vi .ssh/config

# jack5209 GitHub account
Host github-jack5209.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/id_rsa_jack5209

# default GitHub account
Host github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/id_rsa
```

### Clone you repo use different account and modify your Git config

```zsh
git clone git@github.com-jack5209:jack5209/project.git
git config user.name "jack5209"
git config user.email "jack5209@gmail.com"
```

see the difference in url:

```zsh
vi .git/config

[remote "origin"]
    url = git@github.com-jack5209:jack5209/project.git
    fetch = +refs/heads/*:refs/remotes/origin/*
```

Reference: [Multiple SSH Keys settings for different github account](https://gist.github.com/jexchan/2351996)
