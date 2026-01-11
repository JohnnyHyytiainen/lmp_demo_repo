# Enkel "How to PR for dummies" step by step guide.

## A) Se till att allting är clean och att Du är på main(root dvs)
```
git status
git branch
git pull origin main
``` 

## B) Skapa en NY branch.
```
git checkout -b docs/pr-for-dummies
```

## C) Skapa filen
- Skapar nu denna .md fil.

## D) Stage (VIKTIGT: ny fil är untracked så git add -p visar den inte!!!)
```
git add docs/how_to_pr_for_dummies.md
git status
```

## E) Commit
```
git commit -m "docs(PR): added PR for dummies guide"
```

## F) Pusha branchen
```
git push -u origin docs/pr-for-dummies
```

## G) Öppna PR på Github
```
Base: main
Compare: docs/pr-for-dummies
Squash merge
Delete branch
```

## H) Synka lokalt och städa
```
git checkout main
git pull origin main
git branch -d docs/pr-for-dummies
git fetch --prune
```

