# Github Team Track

Scripts to track GitHub activity for teams across GitHub Enterprise and public GitHub.

## Setup

### Create config directory
```shell
mkdir -p ~/.config/team
```

### Configure users (for team-stats and user-stats scripts)
Create file `~/.config/team/users` with the format:
```
DisplayName|username:hostname|username:hostname
```

Each line represents one person and can have multiple GitHub accounts.

```
Inacio Klassman|iklassman:github.internal.com|codegik:github.com
John Doe|johndoe:github.com
```

## Scripts

### user-stats
Shows commit and PR statistics for a specific GitHub user.

```shell
./user-stats <github-username> [github-hostname]
```

```shell
./user-stats inaciok github.internal.com
./user-stats codegik github.com
./user-stats someuser
```

Output:
```
Fetching GitHub stats for user: gpassos from github.internal.com
Current week: 2026-01-15 to 2026-01-21
Previous week: 2026-01-08 to 2026-01-14

Metric         Current Week  Previous Week
Commits        2             7
Pull Requests  4             13
```

### team-stats
Shows commit and PR statistics for all configured team members across their GitHub accounts.

```shell
./team-stats
```

Output:
```
Current week (2026-01-15 to 2026-01-21)
Previous week (2026-01-08 to 2026-01-14)

User             GitHub      CW-Commits  CW-PRs  PW-Commits  PW-PRs
Inacio Klassman  Enterprise  5           0       0           0
Inacio Klassman  Public      58          5       18          3
John Doe         Enterprise  2           4       7           13
```

CW = Current Week, PW = Previous Week

Current week is calculated as last 7 days from today.
Previous week is calculated as 7 to 14 days ago from today.

## Global Installing

Install scripts globally on MacOS to run from anywhere:

```shell
cp user-stats /usr/local/bin/
cp team-stats /usr/local/bin/
chmod +x /usr/local/bin/user-stats
chmod +x /usr/local/bin/team-stats
```

Then run from anywhere:
```shell
user-stats <username> [hostname]
team-stats
```
