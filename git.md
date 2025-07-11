Undo last commit

    git reset --soft HEAD~

Master to main 

    git branch -m master main
    git fetch origin
    git branch -u origin/main main
    git remote set-head origin -a

Merge main to feature branch (Catchup)

    git checkout my-feature
    git pull origin main # or git fetch origin && git merge origin/main
    # Resolve conflicts if any
    git push origin my-feature
