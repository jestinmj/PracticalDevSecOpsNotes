configure git 
```
git config --global user.email "student@pdevsecops.com"
git config --global user.name "student"
```

Git clone a repo
```
git clone http://root:pdso-training@gitlab-ce-xioqjd4c.lab.practical-devsecops.training/root/django-nv.git
```

`git status`
will show while files are added and those that need adding
`git add myfile FILENAME`
`git commit -m "Commit message"`

push files to a github repo
`git push`

pull changes from a repo
`git pull`
+



Command	Description
git add README.md	
        Records the changes made to the README.md file in preparation for committing them to the repository.
git commit -m “update the new text to README.md”	
        Commits the recorded changes to the repository with a descriptive message indicating the update made to the README.md file.
git push origin new-branch	
        Sends the committed changes to the remote repository and saves them in the new-branch branch.
