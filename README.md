# Notes

## Create SSH Key

   $ ssh-keygen -t rsa -b 4096 -C "${EMAIL} -f ~/.ssh/githubkey"

## Configure Github

Account Settings > SSH Keys > Paste Contents of ~/.ssh/githubkey.pub

## Clone Github repository

    $ ssh-agent bash -c 'ssh-add ~/.ssh/githubkey; git clone git@github.com:${USER}/${REPOSITORY}.git'

## Configure git repository

    $ git config user.name "${USER}"
    $ git config user.email "${EMAIL}
    $ gpg --gen-key # RSA and RSA, 4096, Never Expire
    $ gpg --list-secret-keys | grep -B 1 uid
    sec   4096R/${KEYID} ${DATE}
    uid                  ${USER} <${EMAIL}>
    $ git config user.signingkey ${KEYID}

## Commit and Push

    $ git commit -a -S -m "${MESSAGE}"
    $ ssh-agent bash -c 'ssh-add ~/.ssh/githubkey; git push'

