# Cas de non-régression

Passer chaque cas en mode vérification après une modification du skill et comparer aux constats attendus. Les cas marqués PROPRE ne doivent produire aucun constat P0 ou P1 ; signaler trop est une régression.

## Cas 1 : publication LinkedIn (profil : réseaux sociaux)

> Dans un monde en constante évolution, l'innovation n'est plus une option. Chez nous, ce n'est pas juste une méthode, c'est un véritable état d'esprit. Simple. Rapide. Efficace. Et vous, êtes-vous prêt à passer au niveau supérieur ? 🚀

Attendu : P1 ouverture en grand angle ; P1 parallélisme négatif (« ce n'est pas juste… ») ; P1 « véritable », « passer au niveau supérieur » ; P1 triade en fragments ; P2 fin générique. Aucun fait : recommander une reconstruction et signaler l'absence de contenu.

## Cas 2 : paragraphe de blog (profil : blog)

> Il est important de noter que la mise en place de ce nouvel outil s'inscrit dans une démarche globale d'optimisation, permettant ainsi de gagner en efficacité et témoignant de notre engagement. Force est de constater que les résultats parlent d'eux-mêmes.

Attendu : P1 transition toute faite ; P2 nominalisation (« la mise en place de ») ; P1 « s'inscrit dans » ; P1 queues participiales ; P1 fausse volonté (« les résultats parlent d'eux-mêmes ») ; manque : quels résultats.

## Cas 3 : titres de diapositives (profil : diapositives)

> 1. Introduction
> 2. Comment Ça Marche ?
> 3. Ce que cela change pour nous
> 4. Le concept tient la route — et ça se voit

Attendu : P1 titre d'échafaudage ; P1 question-titre ; P2 majuscules à chaque mot ; P1 teaser ; P1 métaphore porteuse en verdict et tiret d'incise sur diapositive.

## Cas 4 : courriel humain (profil : courriel) : PROPRE

> Bonjour Awa,
> Je me permets de revenir vers vous au sujet du devis du 12 mars. Le montant de la ligne 3 ne correspond pas à notre bon de commande (1 200 € au lieu de 1 020 €). Pouvez-vous m'envoyer une version corrigée avant vendredi ?
> Bien cordialement,
> Koffi

Attendu : aucun constat. Les formules de politesse sont protégées.

## Cas 5 : calques (profil : doc/tech)

> Cette release adresse le bug de connexion et supporte maintenant l'export CSV. Éventuellement, on initiera la migration vers la v2.

Attendu : P1 « éventuellement » (sens changé, à confirmer avec l'auteur) ; P2 « adresse », « initiera » ; « supporte » à vérifier : correct au sens de prise en charge en jargon, P2. « release » est du jargon d'équipe : noter, ne pas corriger d'office.

## Cas 6 : signaux faibles seuls (profil : blog) : PROPRE

> Par ailleurs, l'équipe a revu le planning : les livraisons du samedi passent au vendredi. Le changement concerne une vingtaine de clients, que nous prévenons cette semaine.

Attendu : aucun constat. Un « par ailleurs » isolé, un deux-points qui relie une conséquence, une approximation : signaux faibles sans regroupement.

## Cas 7 : langage porteur (profil : administratif) : PROPRE

> Le titulaire du marché ne peut en aucun cas sous-traiter tout ou partie des prestations sans l'accord écrit préalable du pouvoir adjudicateur. Il est tenu d'en informer ce dernier, le cas échéant, dans un délai de 15 jours.

Attendu : aucun constat. Négations, modalités et formules réglementaires sont du contenu.

## Cas 8 : réponse qui reconstruit le contexte (profil : messagerie)

> Pour rappel, la semaine dernière nous avons constaté que les paiements de nuit échouaient. Après analyse des journaux, il apparaît que le délai d'attente du fournisseur est trop court. Nous avons donc envisagé plusieurs options. Au final, je pense qu'on peut augmenter le délai à 30 secondes.

Attendu : P2 réponse qui reconstruit le contexte (décision à la fin), qui peut citer « au final » (P2, signalé seulement dans ce constat de structure, profil messagerie) ; proposition : commencer par « On peut passer le délai à 30 secondes : le fournisseur répond trop lentement la nuit. »

## Cas 9 : typographie (profil : doc/tech)

> Le taux d'échec est passé de 4.2% à 1.1% entre le 10/03 et le 24/03: soit 3,1 points de moins.

Attendu : P1 formats mêlés (point décimal et virgule décimale dans le même texte) ; P2 « % » collé, deux-points sans espace, deux-points de révélation faible.

## Cas 10 : récit (profil : réseaux sociaux, récit)

> Thomas, 35 ans, ingénieur passionné et père de deux enfants, est entré dans mon bureau. Il avait l'air inquiet. Une boule s'est formée dans ma gorge. Et c'est là que j'ai compris : le vrai problème n'avait jamais été technique.

Attendu : P2 présentation par bloc de description ; P1 émotion jouée au lieu d'être nommée ; P1 prise de conscience finale et deux-points de révélation (un seul constat, deux motifs). Ne pas inventer de citation de Thomas.

## Vérification du déclenchement

- « Rédige un courriel au fournisseur pour relancer le devis » : le skill doit se charger en écriture silencieuse.
- « Ça fait trop ChatGPT, tu peux reprendre ? » : réécriture.
- « Vérifie les tics IA de ce paragraphe » : vérification.
- « Écris une fonction de tri en JavaScript » : ne doit pas se charger.
