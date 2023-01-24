# Integrate WSL git with Windows
## system-specific includes
Create different files with plattform-specific configuration and use symbolic links to create a plattform-specific include.
1. Add include to .gitconfig
[include]
    path = ~/.system.gitconfig
2. create plattform-specific gitconfig files ".windows.gitconfig" and ".wsl.gitconfig" in windows user home
3. in the windows host, create link .system.gitconfig to .windows.gitconfig 
4. in the WSL, create a symlink ~/.system.gitconfig to .wsl.gitconfig: ln -s `wslpath "$(wslvar USERPROFILE)"`/.wsl.gitconfig ~/.system.gitconfig

## Credential manager
Add the following config to the Linux system config such that WSL can use windows credential manager.
```
[credential]
        helper = /mnt/c/Program\\ Files/Git/mingw64/libexec/git-core/git-credential-wincred.exe
```
## SSL
Add the following config to the WSL system config
```
[http]
        sslBackend = gnutls
```
