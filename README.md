# unslop-fr

Skill de relecture pour Claude qui repère et retire, dans un texte français, les traits qui le font reconnaître comme généré par une IA.

`unslop-fr` est un [Agent Skill](https://agentskills.io) : un fichier `SKILL.md` et deux fichiers de référence. Il fonctionne avec Claude Code, Claude Desktop et tout agent qui lit le format SKILL.md, et s'installe aussi comme plugin Claude Code.

C'est une adaptation française de [unslop](https://github.com/jlwin/unslop_ai), écrit par Jean-Luc Winkler pour l'allemand et l'anglais. La méthode est la sienne. Les listes de mots, les exemples et les cas de test ont été refaits pour le français, au lieu d'être traduits : les tics de l'IA en français ne sont pas ceux de l'allemand.

## Pourquoi une liste de mots ne suffit pas

Interdire « plonger dans », « incontournable » ou « véritable » ne règle presque rien. Les listes vieillissent à chaque génération de modèles, et l'empreinte durable se trouve ailleurs : dans l'étude StoryScope (Russell et al., 2026, citée par unslop), la structure du discours seule identifie un texte d'IA avec 93,2 % de précision, alors qu'une réécriture professionnelle phrase par phrase ne déplace la détection que de 1,6 point.

Le skill travaille donc sur trois niveaux, avec plus de poids sur les deux derniers :

| Niveau | Ce qu'il repère | Exemples |
|---|---|---|
| 1. Mots | vocabulaire, formules toutes faites, ponctuation, typographie | « s'inscrire dans », « Force est de constater », calques de l'anglais, « 50% » sans espace |
| 2. Rythme | motifs de phrase | longueurs uniformes, phrases courtes en série, triades, « Ce n'est pas X, c'est Y », « …, permettant ainsi de… » |
| 3. Structure | la forme du texte entier | morale répétée à chaque section, paragraphes identiques, plans tout faits, références vagues, émotion jouée au lieu d'être nommée |

Une règle traverse les trois niveaux : remplacer l'affirmation vague par le fait vérifiable (un chiffre, un nom, une date, un prix, un mécanisme). Quand ce fait manque, le skill signale le manque. Il n'en invente jamais.

## Ce qui est propre au français

- **Les calques de l'anglais** : « adresser un problème », « faire du sens », « supporter un format », « éventuellement » au sens de « finalement ». Ceux qui changent le sens sont classés plus graves que les autres.
- **Les fins de phrase au participe** : « …, permettant ainsi une meilleure réactivité », « …, témoignant de notre engagement ». C'est l'un des tics les plus fréquents du français généré.
- **Le style nominal** : « la mise en place de », « procéder à la vérification de », « au niveau de ». Corrigé en prose courante, protégé dans les textes administratifs et sur les diapositives, où c'est la norme humaine.
- **La typographie française** : espaces insécables avant « : ; ! ? », guillemets « », 1 000 et 3,5, « 50 % », dates, titres sans majuscule à chaque mot. Un document qui mélange conventions anglaises et françaises est signalé.
- **Les formules de politesse** : « Je me permets de revenir vers vous », « Je reste à votre disposition » sont des usages humains. Le skill ne les signale que lorsqu'elles s'empilent sans contenu.
- **Un profil administratif et juridique** : « il convient de », « est tenu de », « le cas échéant » et les interdictions (« ne peut en aucun cas ») sont traités comme du contenu, jamais adoucis.

## Quand il s'applique

Une fois installé, le skill se charge seul quand Claude rédige ou révise en français une prose de plus de quelques phrases destinée à être envoyée ou publiée : courriels, messages Slack ou Teams, publications, tickets, descriptions de PR, notes de version, documentation, spécifications, rapports, présentations. Il ne touche ni au code, ni aux commandes, ni aux tableaux de données, ni aux réponses d'une ligne.

## Modes

| Mode | Déclencheur | Comportement |
|---|---|---|
| **Écriture** | par défaut pour un texte nouveau | applique les règles en rédigeant, puis relit son propre brouillon |
| **Vérification** | « vérifie les tics IA », « qu'est-ce qui fait IA ici » | signale seulement, par gravité (P0, P1, P2), sans rien changer |
| **Réécriture** | « ça fait ChatGPT », « rends ça plus naturel » | audit, version nettoyée, journal des changements, seconde relecture |
| **Édition de fichier** | « corrige directement brouillon.md » | retouches minimales sur place, passages humains laissés intacts |

## Garde-fous

L'échec classique des outils d'« humanisation » est d'échanger une empreinte contre une autre : phrases hachées, anecdotes inventées à la première personne, franchise jouée (« Soyons honnêtes : »). Le skill considère chacun de ces gestes comme une réécriture ratée. Il peut couper et préciser ; il ne peut pas ajouter de fait, de position ou de personnalité que l'auteur n'a pas écrits. Une réécriture qui perd un chiffre, une condition ou une négation, ou qui en change la force, a aussi échoué.

Ce skill sert à mieux écrire. Il ne sert pas à échapper aux détecteurs d'IA ni aux obligations de déclaration : là où l'usage de l'IA doit être déclaré, il n'y change rien.

## Installation

Dans Claude Code :

```
/plugin marketplace add monsieur-akhir/unslop-fr
/plugin install unslop-fr@unslop-fr
```

Sans plugin, copier le dossier `skills/unslop-fr` dans `~/.claude/skills/`.

Pour l'allemand et l'anglais, installer [unslop](https://github.com/jlwin/unslop_ai). Les deux skills se complètent.

## Contenu

```
skills/unslop-fr/
  SKILL.md                      règles, modes, profils de registre, garde-fous
  references/listes-de-mots.md  vocabulaire en trois niveaux, calques, artefacts, typographie
  references/catalogue.md       25 motifs avec exemples avant/après
  evals/cas.md                  10 cas de non-régression avec constats attendus
  CHANGELOG.md
```

## Tests

Les cas de `skills/unslop-fr/evals/cas.md` se passent en mode vérification après chaque modification. Trois d'entre eux doivent rester propres (un courriel ordinaire, un paragraphe aux signaux faibles isolés, une clause de marché public) : signaler trop est aussi une régression. Pour un résultat non biaisé, les faire passer par un agent qui ne voit pas les constats attendus.

## Confidentialité

Le plugin ne contient que du Markdown : il n'envoie et ne conserve aucune donnée. Voir `PRIVACY.md`.

## Licence

MIT. Copyright (c) 2026 Jean-Luc Winkler pour unslop, dont ce skill est dérivé ; adaptation française par Monsieur Akhir. Voir `LICENSE`.
