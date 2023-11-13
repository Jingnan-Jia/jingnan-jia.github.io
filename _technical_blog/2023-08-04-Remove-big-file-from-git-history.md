---
title: How to absolutely remove big or sensitive files from git history?
tags:
  - Knowledge
  - Technique
---

`git-filter-repo`

## Install it

`python3 -m pip install --user git-filter-repo`

Source: https://superuser.com/questions/1563034/how-do-you-install-git-filter-repo


## How to use it?
1. cd YOUR_REPOSITORY
2. git filter-repo --analyze  # analyze big files, you will see the report in .git/filter-repo/analyze/
3. git filter-repo --invert-paths --path FILE_NAME1 --path FILE_NAME2


Reference:
- https://stackoverflow.com/questions/2100907/how-to-remove-delete-a-large-file-from-commit-history-in-the-git-repository
- https://htmlpreview.github.io/?https://github.com/newren/git-filter-repo/blob/docs/html/git-filter-repo.html



