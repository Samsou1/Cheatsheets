# Git

## Create a new repository on the command line
```
git init
git add README.md
git commit -m "first commit"
git branch -M main
git remote add origin git@github.com:Samsou1/POO_day_2.gitgit push -u origin main
```

## Push an existing repository from the command line
```
git remote add origin git@github.com:Samsou1/POO_day_2.git
git branch -M main
git push -u origin main
```

## Pull
```
git remote add origin git@github.com:Samsou1/POO_day_2.git
git pull origin main
```

## To switch branches

```
git checkout master $to be on the right branch
git pull origin master $to get the last version of master
git branch feature_name $to create a new branch from master (which is now up to date)
git checkout feature_name 
git add . 
git commit -m "reason of commit" 
```

## How to merge branches

```
git checkout master 
git pull origin master
git checkout feature_name
git merge master 
git checkout master
git merge feature_name 
git push origin master 
```

Felix's cheatsheet (https://github.com/felhix)
