# auth-keepmykeys
Intégrer une passerelle vers KeepMyKeys sur votre page de connexion

# Manuel d'utilisation du bouton d'identification avec KeepMyKeys
  
* ## Déroulement du processus:
1. L'utilisateur accède à keepmykeys depuis votre site grâce au bouton
2. L'utilisateur se connecte ou s'inscrit puis se connecte sur keepmykeys
3. L'utilisateur est directement renvoyé sur votre site pour lequel il avait besoin de son mot de passe

* ## Le bouton d'authentification :
### 1. HTML
```
<!-- connexion avec keepmykeys -->
<a href="https://www.keepmykeys.fr/generer.php?from=URL DE VOTRE PAGE DE CONNEXION&for=LE NOM DE VOTRE APPLICATION" target=_blank id="btn-kmk-connect" class="both">
    <div class="img-kmk"><img src="https://www.cloud.keepmykeys.fr/images/logo_kmk_sans_text_png.png"></div>
    <div class="text-kmk">Utiliser KeepMyKeys</div>
</a>
```

**Remarque 1** : le href *DOIT* contenir l'adresse du site après "from" et le nom donné à keepmykeys pour identifier votre application après "for" (exemple : `https://www.keepmykeys.fr/generer.php?from=https://cloud.keepmykeys.fr&for=keepmycloud`)

**Remarque 2** : le href *PEUT* contenir un GET supplémentaire "option" qui spécifie les options choisi pour le cryptage. (exemple :` https://www.keepmykeys.fr/generer.php?from=https://cloud.keepmykeys.fr&for=keepmycloud&option=01015`)

#### * Les options pour la conception du mot de passe sont (par défaut 01015) : 
- chiffre seulement : 0 ou 1
- caractère spéciaux : 0 ou 1
- caractère spéciaux simplifiés : 0 ou 1
- longueur du mot de passe : entre 1 et 30

**! ATTENTION !** 
Si les caractères spéciaux sont désactivés aucun caractère spécial ne sera présent dans le mot de passe,
même si les caractères spéciaux simplifiés sont activés, ils ne seront pas pris en compte.

### 2. CSS
Le code à ajouter dans la partie `<header>` de votre code : <br/>
```<link rel="stylesheet" href="https://www.keepmykeys.fr/style/css/authKMK.css"/>```

#### a) Différentes class pour #btn-kmk-connect
- both -> logo et texte
- img-kmk -> logo uniquement 

#### b) Styliser le reste
- Autant que vous voulez mais le but est que l'utilisateur puisse reconnaitre facilement KeepMyKeys

* ## Gérer les informations renvoyées

L'adresse où est redirigé l'utilisateur est de la forme : `https://VOTRE SITE.fr/VOTRE PAGE DE CONNEXION.php?authKey=MOT DE PASSE DE L'UTILISATEUR`   

Exemple: Pour une balise `<a>` avec l'attribut `href=https://www.keepmykeys.fr/generer.php?from=https://cloud.keepmykeys.fr/connexion.php&for=netocentre"`<br/> L'utilisateur sera rédirigé vers : `https://cloud.keepmykeys.fr/connexion.php?authKey=Jsa52!s,e56nKd`

**Remarque 1** : Il est conseillé, pour des raisons de sécurités et d'esthétiques,
de récupèrer la variable GET et de rediriger l'utilisateur vers votre page de connexion sans le GET.

**Remarque 1** : N'hésitez pas à avertir l'utilisateur que tout s'est bien déroulé et que son mot de passe a bien été récupéré.

* ## Exemple
Consulter la page de connexion de [KeepMyCloud](https://www.cloud.keepmykeys.fr).
