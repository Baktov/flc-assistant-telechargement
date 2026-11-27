# FLC Assistant

**Foundry VTT avec un assistant Claude pour les joueurs.**

FLC Assistant est une copie **non officielle** de [FLC](https://github.com/phenomen/flc)
(Foundry Lightweight Client, de phenomen). On s'en sert exactement comme de FLC pour rejoindre une
partie Foundry VTT. La différence : un bouton **✦ Assistant** ouvre une discussion avec Claude, qui
connaît ta fiche de personnage, les règles du jeu et les notes de la campagne.

> L'auteur de FLC n'y est pour rien : en cas de souci, ne lui demande pas d'aide, ouvre plutôt un
> ticket ici (onglet *Issues*).

## ⬇️ Télécharger

**[Dernière version : page des téléchargements](../../releases/latest)**, fichier
`FLC_Assistant_<version>_Windows.msi`.

Les numéros de version se lisent ainsi : `8.0.0.5-a` = FLC 8.0.0, version n° 5 de l'assistant,
« -a » pour assistant.

## Ce qu'il sait faire

| | |
| --- | --- |
| **Relire ta fiche** | Erreurs, incohérences, oublis (bonus, CA, sorts préparés…). |
| **T'aider à choisir** | Répartition des points, montée de niveau, dons, sorts. |
| **Te conseiller avec ce que tu as** | « Je cherche un sort offensif », « comment ralentir cet adversaire » : il part de tes sorts préparés, emplacements, objets et aptitudes. |
| **Expliquer les règles** | Du système choisi en haut du panneau (par défaut, celui de la partie). |
| **Répondre sur l'histoire** | À partir des journaux que tu coches dans **Notes**, du tchat si tu coches **Tchat**. |
| **Consulter les compendiums** | Il cherche, parcourt et lit les compendiums que ton compte voit ; il peut te proposer un bouton 📖 pour ouvrir une entrée. |
| **Voir la table et le combat** | Tel que ton compte le voit : les autres joueurs, l'ordre du combat et le tour actuel, les adversaires visibles et leur distance, tes cibles. Rien de caché. |
| **Lancer un sort, attaquer, utiliser une aptitude** | « Je lance une boule de feu sur l'ogre » : il vérifie (sort préparé, emplacement, ton tour, distance), te demande des précisions si besoin, puis propose un bouton 🪄 qui fait comme un clic sur ta fiche. |
| **Lancer des dés, changer tes réglages** | Boutons 🎲 et ⚙, avec la visibilité du jet (public, MJ, aveugle…). **Rien ne se fait sans ton clic**, sauf les dés si tu coches « Dés sans clic ». |
| **Suivre la partie** (au choix) | 🔔 alertes (ton tour, PV, concentration…), 🎯 conseil à ton tour, 📜 journal de séance et compte rendu. |

La lecture détaillée de la fiche est faite pour **D&D 5e**. Pour un autre système, Claude reçoit les
données brutes du personnage : ça marche, mais moins bien. Le bouton **?** du panneau ouvre l'aide
complète.

## Ce qu'il te faut

- **Windows 10 ou 11** (64 bits).
- **Un accès à Claude**, au choix :
  - **un abonnement qui inclut Claude Code** (Pro ou Max), avec
    [Claude Code](https://claude.com/claude-code) installé et connecté sur ce PC. Pour le vérifier :
    ouvre un terminal, tape `claude`, Entrée ; s'il démarre et te connaît, c'est bon (`/exit` pour
    quitter) ;
  - **ou un compte API**, payé à l'usage, sans abonnement (voir plus bas).

  Un simple compte gratuit ne suffit pas : l'offre gratuite de Claude ne comprend pas Claude Code.
  Dans tous les cas, c'est **ton** compte qui sert : l'application ne contient aucun compte ni
  aucune clé.
- Une partie Foundry VTT à rejoindre. Rien n'est à installer côté MJ.

## Installer

1. Télécharge le fichier `.msi` de la [dernière version](../../releases/latest) et double-clique
   dessus.
2. Windows affiche sans doute **« Windows a protégé votre ordinateur »** : c'est normal, le fichier
   n'est pas signé par un éditeur reconnu (une signature est payante). Clique sur **Informations
   complémentaires**, puis **Exécuter quand même**.
3. Accepte la demande d'autorisation de Windows. L'installation se fait seule.
4. Lance **FLC Assistant** depuis le menu Démarrer.

FLC Assistant s'installe **à côté** du FLC officiel, si tu l'as : chacun garde ses réglages. Ajoute
ton serveur dans FLC Assistant, ou utilise l'export de la liste dans FLC puis l'import dans FLC
Assistant.

## Premier lancement

1. Rejoins la partie comme d'habitude.
2. Clique sur **✦ Assistant** (en bas à gauche ; il se déplace à la souris).
3. Clique sur **Voir ce qui sera envoyé** : ta fiche doit y être. Si une valeur manque ou est
   fausse, signale-le.
4. Pose une question, par exemple « Relis ma fiche ».

## Abonnement ou clé d'API

Le menu en haut du panneau choisit le mode.

- **Abonnement** (par défaut) : utilise Claude Code et ton quota d'abonnement. Une relecture
  complète de fiche prend environ 40 secondes, mais le texte s'affiche au fur et à mesure.
- **Clé d'API** : plus rapide (environ 10 secondes), payé à l'usage, de l'ordre de quelques
  centimes par question.

### Sans abonnement : compte API

1. Crée un compte sur la **Claude Console** : [platform.claude.com](https://platform.claude.com).
2. Dans *Billing*, achète quelques dollars de crédits (le minimum est indiqué au moment de
   l'achat). Tu peux y fixer une **limite de dépense** mensuelle.
3. Dans *API keys*, crée une clé et **copie-la** (elle commence par `sk-ant-`). Elle ne s'affiche
   qu'une fois : garde-la pour toi, c'est l'équivalent d'un mot de passe lié à ta carte.
4. Enregistre-la dans Windows : touche Windows, tape **variables d'environnement**, ouvre
   « Modifier les variables d'environnement pour votre compte », **Nouvelle…**, nom
   `ANTHROPIC_API_KEY`, valeur : ta clé.
5. Relance FLC Assistant, puis choisis **Clé d'API** dans le panneau (choix retenu).

Si tu as aussi Claude Code connecté à un abonnement, cette variable le fait passer, lui aussi, sur
ta clé d'API (donc payant à l'usage). Dans ce cas, préfère l'outil `ant` (`ant auth login`), que
FLC Assistant sait utiliser à la place.

## Confidentialité et correction

- Claude ne voit que ce que ton compte Foundry voit : ni les journaux ou compendiums cachés, ni les
  messages privés entre d'autres personnes, ni les secrets du MJ.
- Pour répondre, tes questions et les données du jeu partent chez Anthropic (Claude), avec ton
  compte. Le journal de séance, si tu l'actives, reste sur ton PC.
- **Préviens ton MJ** que tu utilises un assistant, surtout qu'il peut lancer des dés et des sorts
  à ta demande.

## En cas de souci

| Message ou problème | Que faire |
| --- | --- |
| « Impossible de lancer Claude Code » | Tu es en mode Abonnement mais Claude Code n'est pas installé ou pas trouvé : vérifie que `claude` marche dans un terminal, puis relance FLC Assistant. Sans abonnement, choisis **Clé d'API**. |
| Claude Code renvoie une erreur | Souvent une connexion expirée ou un quota atteint : lance `claude` dans un terminal pour voir le message. |
| « Pas d'accès à l'API » | Mode Clé d'API sans clé trouvée : suis « Sans abonnement : compte API », puis relance. |
| « L'API a refusé… crédit » | Crédits épuisés ou limite atteinte : recharge-les dans la Claude Console. |
| Pas de bouton ✦ Assistant | Il n'apparaît qu'une fois connecté à la partie. Recharge la page avec F5. |
| Réponses très lentes | Décoche des journaux dans **Notes**, ou choisis Haiku pour les questions simples. |

## Mises à jour et désinstallation

- FLC Assistant ne se met **pas** à jour tout seul. Pour une nouvelle version, ferme-le et installe
  le nouveau fichier par-dessus : tes serveurs et réglages sont gardés.
- Pour le désinstaller : Paramètres de Windows → Applications → FLC Assistant → Désinstaller.

## Licence et crédits

FLC Assistant est basé sur [FLC](https://github.com/phenomen/flc) de **phenomen**, sous licence MIT
(voir [LICENSE](LICENSE)). Ce dépôt ne contient que les fichiers à télécharger et cette page.
FLC Assistant n'est lié ni à l'auteur de FLC, ni à Foundry Gaming LLC, ni à Anthropic.
