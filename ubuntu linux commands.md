# Useful Linux commands

## Timezone

```bash
# Check timezone
timedatectl

# Change timezone to Ulaanbaatar
sudo timedatectl set-timezone Asia/Ulaanbaatar
```

## Clear Buff Cache

```shell
free && sync && echo 3 > /proc/sys/vm/drop_caches && free
```

## Clean /tmp directory in linux

```bash
# List big files in linux directory
du -sc * .[^.]* | sort -n
# Clean files one day prior
find /tmp -ctime 1 -exec rm -rf {} +
```

## List open ports

```bash
sudo firewall-cmd --list-all
```

## List permissions

```bash
# List file permissions
stat -c "%a %n" ~/file.html
# List folder permissions
stat -c "%a %n" ~/directory/
```

## Previously used commands

Fix error `permission denied, mkdir '/tmp/vsch'` in vscode remote-release
```bash
# Change owner group of directory into public-data /public-data has all our members/
sudo chown -R uguudei:public-data /tmp/vsch

# Make new directory and files inheret parent directory group permission
sudo chmod 02775 /tmp/vsch
```

### If the problem still exist, enter following command

```bash
sudo chmod 02775 /tmp/vsch/container-features
```
