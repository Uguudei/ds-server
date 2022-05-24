# How to set up SSH connection

Start a  PowerShell as an Administrator

## Generate SSH key on Windows

```powershell
ssh-keygen -t rsa -b 4096 -f $HOME/.ssh/key_name_rsa
generate no passphrase
```

## Start ssh-agent on Windows

```powershell
Set-Service ssh-agent -StartupType Automatic
Start-Service ssh-agent
Get-Service ssh-agent
```

## Add key to ssh-agent

```powershell
ssh-add $HOME/.ssh/key_name_rsa
```

## Add SSH key to linux server

```powershell
scp $HOME/.ssh/key_name_rsa.pub user@ip_address:~
# SSH into linux server
ssh user@ip_address
```

On linux server

```bash
# Create .ssh directory and set permission
mkdir -p ~/.ssh && chmod 700 ~/.ssh
# Write public key to authorized_keys in linux
cat key_name_rsa.pub >> .ssh/authorized_keys
# Remove public key and set file permission
rm key_name_rsa.pub && chmod 600 ~/.ssh/authorized_keys
```

## SSH into server

entering following command should run without asking for password or warning

```powershell
ssh user@ip_address
```

If a warning appears fix OpenSSH on Windows

## Fix OpenSSH on Windows

Start a  PowerShell as an Administrator

### Install [Scoop](https://github.com/lukesampson/scoop)

```powershell
# PowerShell must be enabled for your user account
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
# Install scoop
iwr -useb get.scoop.sh | iex
# Install sudo via scoop
scoop install sudo
```

### Install OpenSSH via scoop

```powershell
sudo scoop install -g win32-openssh
sudo C:\ProgramData\scoop\apps\win32-openssh\current\install-sshd.ps1
sudo Set-Service -Name ssh-agent -StartupType Automatic
sudo Start-Service ssh-agent
```

## Additional useful commands

You may need to use the following command if you ever want to know or remove keys from ssh-agent

```powershell
# List added keys in ssh-agent
ssh-add -l

# Remove added keys from ssh-agent
ssh-add -D
```