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
