## Multiple SSH Keys settings for different github account(在单台电脑上使用多个github账号)

```zsh
# jack5209 GitHub account
Host github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/id_rsa_jack5209

# link5209 GitHub account
Host github.com-link5209
 HostName github.com
 User git
 IdentityFile ~/.ssh/id_rsa
```

download github repo use jack5209 GitHub account
`git clone git@github.com:jack5209/project.git`

download github repo use link5209 GitHub account
`git clone git@github.com-link5209:link5209/project.git`

```sh
vi .git/config
...
[remote "origin"]
    url = git@github.com-link5209:link5209/shopee.git
    fetch = +refs/heads/*:refs/remotes/origin/*
...
```

Reference: [Multiple SSH Keys settings for different github account](https://gist.github.com/jexchan/2351996)
