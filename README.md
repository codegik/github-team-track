# Github Team Track

Show commits from team. 

## Setup

### Create file `repos` in config directory.
- `mkdir -p ~/.config/team`
- `touch ~/.config/team/repos`

### Add repositories in `repos` file

Put each repository in new line. Example of file content `~/.config/team/repos`.
```
https://github.com/teammate/java-pocs
https://github.com/codegik/pocs
```

## Running

This command will show last commit from yesterday.
```shell
./team-commits
```

Output sample
```log
User repo                Status  Commit url
teammate/java-pocs       OK      https://github.com/teammate/java-pocs/commit/d2a782f2983d91ed99ed91db24194117b22169fe
codegik/pocs             NOT-OK  https://github.com/codegik/pocs/commit/
```

## Global Installing

Follow this steps to install the script in MacOS. Then you'll be able to call from anywhere by typing `team-commits`.

```shell
cp team-commits /usr/local/bin/
chmod +x /usr/local/bin/team-commits
```
