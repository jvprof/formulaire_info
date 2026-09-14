# formulaire_info

Recueil de formulaires/résumés LaTeX pour les cours d'informatique, organisés par niveau. Chaque résumé tient sur quelques pages et sert d'aide-mémoire (types, opérateurs, structures de contrôle, boucles, etc.).

## Structure du projet

```
formulaire_info/
├── 1M/     # Résumés du niveau 1M (ex: python-1M-resume.tex)
├── 2M/     # Résumés du niveau 2M
├── 3OC/    # Résumés du niveau 3OC
└── .gitignore
```

Chaque dossier de niveau contient un ou plusieurs documents `.tex` autonomes (un fichier = un document compilable). Les fichiers générés par la compilation (`.pdf`, `.aux`, `.log`, `.fls`, `.fdb_latexmk`, ...) ne sont **pas** versionnés (voir [.gitignore](.gitignore)).

## Prérequis

- Une distribution LaTeX complète (recommandé : [TeX Live](https://www.tug.org/texlive/) ou [MacTeX](https://www.tug.org/mactex/) sur macOS).
- Packages utilisés par les documents : `fancyhdr`, `listings`, `babel` (option `french`), `lmodern`, `tikz` (avec les librairies `shapes.geometric`, `arrows.meta`, `positioning`). Ils sont inclus dans une installation TeX Live standard/complète.
- (Optionnel) Une extension LaTeX pour votre éditeur, par exemple [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) pour VS Code, pour compiler et prévisualiser directement depuis l'éditeur.

## Compiler un document

Depuis le dossier du niveau concerné :

```bash
cd 1M
pdflatex -interaction=nonstopmode python-1M-resume.tex
```

Le PDF est généré à côté du fichier source. Si votre document utilise une bibliographie ou un index, utilisez `latexmk` pour enchaîner automatiquement les passes nécessaires :

```bash
latexmk -pdf python-1M-resume.tex
```

## Conventions

- **Nommage des fichiers** : `<sujet>-<niveau>-resume.tex` (ex : `python-1M-resume.tex`).
- **Structure d'un document** : chaque grande partie est un `\section*{...}` séparé par un saut de page (`\newpage`). Utilisez `\subsection*{...}` pour les sous-parties.
- **Mise en page** : `article`, format `a4paper`, mode `twoside` pour une impression recto-verso façon livret (numéro de page en coin extérieur via `fancyhdr`).
- **Code source** : les extraits de code utilisent l'environnement `lstlisting` (ex : `\begin{lstlisting}[language=Python]`).
- **Schémas** : les diagrammes de flux sont réalisés avec `tikz` en réutilisant les styles définis dans le préambule (`startstop`, `decision`, `process`, `fleche`).

## Contribuer

1. Clonez le dépôt : `git clone https://github.com/jvprof/formulaire_info.git`
2. Créez une branche pour votre modification.
3. Compilez localement pour vérifier l'absence d'erreurs avant de committer.
4. Ne committez jamais les fichiers générés (PDF et fichiers auxiliaires) : ils sont exclus par le [.gitignore](.gitignore).
5. Ouvrez une pull request avec une description claire du contenu ajouté ou corrigé.
