# Pull Request (PR) for Dummies — Team Guide

Syfte: En enkel steg-för-steg guide för hur vi gör en ändring och får in den i `main` via Pull Request.
Vi jobbar ALDRIG direkt på `main`.

---

## Förutsättningar (innan du börjar)
1) Du har klonat repot och står i reporoten
2) Din working tree är clean

Kör:
```
git status
```

## Steg 1 - Uppdatera `main` 
- Gå till `main` och hämta senaste från github:
```
git checkout main
git pull origin main
```
**Varför?** 
- Du vill ALLTID utgå från senaste 'sanningen'

## Steg 2 - Skapa ny branch
- Skapa en branch med ett TYDLIGT namn:
```
git checkout -b <typ>/<kort-beskrivning>
```
**Exempel:**
- docs/update-readme
- feat/clean-ads-keywords
- fix/null-title-bug

## Steg 3 - Gör din ändring.
- Ändra filer, skapa nya filer etc etc.
- **PRO TIP** `git status` och `git diff`

## Steg 4 - Stage (Lägg till det du MENAR!)
- A) Om du har ändrat en befintlig fil (rekommenderat)
```
git add -p
```
**Varför?** Du undviker att råka lägga med skräp.

- B) Om du skapat en NY fil (untracked)
- (`git add -p` visar inte alltid nya filer. Lägg då till filen direkt med:)
```
git add path/to/new_file
```
**Exempel:** `git add docs/my_new_doc.md` kolla sedan med 
`git status`

## Steg 5: Commit
- Commit meddelandet ska vara kort och tydligt som står i vår `team_workflow_and_rules.md`
```
git commit -m "docs(scope): kort beskrivning" 
```
**Exempel:**
- docs(readme): Clarify setup steps
- feat(clean): added keyword tagging
- fix(parser): handle empty description

## Steg 6: Pusha din branch
**Första gången du pushar branchen:**
```
git push -u origin <branch-namn>
```
**Exempel:**
```
git push -u origin docs/update-readme
```

## Steg 7: Skapa Pull Request(PR) på Github.
- 1) Gå till Github -> repo -> Pull requests -> New pull request.

- 2) Base: `main`, compare: din branch

- 3) Fyll i PR mallen/checklistan du har vid namn `pull_requests_checklist.md`

- 4) Request review (Som det står om i `team_workflow.md`)

## Steg 8: Merge (vi använder oss av SQUASH)
- När PRn är OK:
- Välj `Squash and merge`
- Radera branchen `Delete branch`
**Varför?** REN HISTORIK PÅ `main`

## Steg 9: Synka lokalt och städa.
- Efter merge:
```
git checkout main
git pull origin main
```
- Radera din lokala branch:
```
git branch -d <branch-namn>
```
- Städa remote-spår (valfritt men cleant och fint)
```
git fetch --prune
```

### Vanliga problem och snabbfixar:

- "No changes" när jag kör git add -p
Du har troligen bara nya (untracked) filer. Kör:

`git status`
`git add path/to/file`

- "rejected (fetch first)" vid push.
Remote har commits du saknar. Kör:

`git pull --rebase origin main`

och försök pusha igen.

- Jag råkade ändra på main. Skapa en branch direkt och fortsätt där:

`git checkout -b fix/move-work-off-main`

**THE END**