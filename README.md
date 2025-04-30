Repo containing GT:NH binaries to allow autoupdating modpack for my players.

Installing:
1. Install git
2. Import [GTNH.zip](https://github.com/user-attachments/files/19978842/GTNH.zip) in Prism Launcher
3. Choose modern java (21-22)
4. First launch will download everything and crash. Second launch will succeed

Update script: 
```cmd
powershell.exe -NoProfile -Command "& {$ErrorActionPreference='Stop'; $fetchStatus = git fetch origin --depth=1; if ($fetchStatus -eq $null) { $newCommit = git rev-list HEAD...origin/master --abbrev-commit --max-parents=0; if ($newCommit) { git reset --hard origin/master } else { Write-Output 'No new commits in origin/master' } } else { Write-Error "git fetch failed with exit code $fetchStatus" }}"
```

