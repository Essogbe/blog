---
socialImage: https://upload.wikimedia.org/wikipedia/en/thumb/8/87/Tea_Dating_Advice_logo.png/250px-Tea_Dating_Advice_logo.png
title: Le Scandale Tea App et le Vibe Coding
---


# Tea App, Vibe Coding et la sécurité : Réflexions d'un développeur



> [!note]
> Ce blog  a été originellement écrit et publié sur les statuts de mon compte Whatsapp d'où le style d'écriture un peu ... relâché.  Ne m'en tenez pas rigueur :)

## Parlons de Vibe Coding

 « *Le concept fait référence à une approche de programmation qui s'appuie sur les LLM, permettant aux programmeurs de générer du code fonctionnel en fournissant des descriptions en langage naturel plutôt que d'écrire le code manuellement. Karpathy a décrit son approche comme conversationnelle, utilisant des commandes vocales tandis que l'IA génère le code fonctionnel. « Ce n'est pas vraiment de la programmation - je visualise juste des choses, je dis des choses, j'exécute des choses et je copie-colle des choses, et la plupart du temps, ça marche. »* » Wikipedia. https://fr.wikipedia.org/wiki/Vibe_coding
 




<html lang="en">



  <div class="tweet-container" class ="center-image"     >
    <blockquote class="twitter-tweet">
      <p lang="en" dir="ltr">
        There's a new kind of coding I call "vibe coding", where you fully give in to the vibes, embrace exponentials, and forget that the code even exists. It's possible because the LLMs (e.g. Cursor Composer w Sonnet) are getting too good. Also I just talk to Composer with SuperWhisper…
      </p>
      — Andrej Karpathy (@karpathy) 
      <a href="https://twitter.com/karpathy/status/1886192184808149383?ref_src=twsrc%5Etfw">February 2, 2025</a>
    </blockquote>
  </div>

  <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>


</html>


	


## Tea App : l'application qui fait polémique

Il y a actuellement une application qui fait polémique sur les réseaux. Cette application c'est Tea App. Une application pour les femmes dont le but est de donner des informations sur les hommes et vérifier s'ils sont impliqués dans des cas d'adultères, de criminalité, abus ou autres "red flag". L'objectif étant de favoriser un environnement "safe" entre femmes pour leur éviter de se mettre en couple avec des hommes zarbi. L'application en Juillet 2025 avait environ 1 million d'utilisateurs principalement aux USA.

Comment ça marche ? Simple. L'application est réservée exclusivement aux femmes , vraiment exclusivement. Et pour s'en assurer, les utilisateurs doivent fournir leurs informations personnelles; essentiellement uploader les photos de leurs pièces d'identité (peu importe pourvu que ça prouve que la personne est de sexe féminin. Je ne vais pas rentrer dans les considérations de sexe  mais vous avez compris).

Ensuite les utilisatrices (à partir d'ici permettez-moi d'utiliser les termes de façon interchangeable utilisateurs et utilisatrices) uploadent une photo d'un homme  et l'application utilise des méthodes de  [recherche d'images inversée](https://en.wikipedia.org/wiki/Reverse_image_search) (Je compte faire un petit blog dessus ) pour donner des informations sur un homme, son précédent et éventuellement déduire s'il est digne de confiance ou non. Au sein de l'application, il y a aussi apparemment des groupes d'échanges entre femmes le tout pour créer une communauté et rassurer les femmes.

(Quelques images de l'app) https://teaforwomen.com

<img src ="https://cdn.prod.website-files.com/64cc13c1c99b0aed767d93fc/67bdd9ba5074e2afe36a8a15_Group%203680%201%20(1).png">

## La faille catastrophique : +50 Go de données exposées

La polémique en question c'est que la base de données dans laquelle les concepteurs de l'appli stockent les photos des pièces d'identité des utilisateurs est publique. Non pas qu'elle a été pensée pour être publique puisque l'un des arguments de l'app est la garantie de la confidentialité des données. En gros, les pièces d'identité, photos etc des utilisatrices sont disponibles sur Internet. Ça pèse environ plus de 59GB et avant qu'ils ne pensent à protéger la base de données,certains l'ont  déjà téléchargé et leaké sur un lien Torrent.

<html>
<div class="tweet-container" >
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">The Tea app has been hacked, and you can go download 59.3 gigabytes of user selfies right now.<br><br>The hack is real. A picture from someone I know who signed up just to see what was on there was in it.<br><br>This was an obviously vibe-coded app and was bound to be insecure. <a href="https://t.co/yrUxW1cFZc">pic.twitter.com/yrUxW1cFZc</a></p>&mdash; Crémieux (@cremieuxrecueil) <a href="https://twitter.com/cremieuxrecueil/status/1948787086493901097?ref_src=twsrc%5Etfw">July 25, 2025</a></blockquote></div>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>
</html>



C'est assez dramatique et grave vu le type de données qu'on traite et qui ont été exposées. Et rendez-vous compte que les images renferment une mine d'or. D'une part, le contenu des images mais aussi ce qu'on ne voit pas à l'œil nu. Ce sont les métadonnées de l'image. Pour une image classique prise par un appareil, il y a la localisation (vous comprenez pourquoi Google Photos peut créer des albums en fonction du lieu si vous avez voyagé et ceci sans que vous n'activiez votre localisation), le type de l'appareil photo, le jour l'heure où la photo a été prise etc.

Ce qui fait que juste avec une image que vous avez mise sur les réseaux sociaux par exemple, on peut savoir où vous êtes et autres. Je ne pense pas que ça soit très très précis (certains imaginent déjà un scénario à la Pop Smoke lol) et je ne sais pas comment chaque réseau social gère cet aspect. Il faudra faire un petit test pour ça (rien de sorcier). Pour cette affaire, certains se sont déjà amusés à faire une carte du monde avec les points représentant les endroits où sont photos ont été prises (et on peut supposer avec une forte probabilité que ce sont les domiciles des utilisateurs).

On s'est un peu attardé sur les métadonnées pas parce que c'est plus important que l'aspect visuel de l'image mais à cause du fait que c'est un volet que beaucoup ignorent.

**Instant pub 😂 :** L'une de mes collègues et amie d'IFRI a d'ailleurs travaillé sur cette question (métadonnées des images) dans le cadre de son mémoire (qu'elle a soutenu dans la semaine) à travers une application qui vous permet de voir ces métadonnées et de les supprimer si vous voulez. Elle travaille  encore sur une version finale. Je vous reviendrai si c'est publié. Déjà quand elle a abordé ce sujet, je l'ai jugé super utile. Elle s'appelle  [Sophie AHOLOU ](https://www.linkedin.com/in/sophie-f%C3%A8mi-aholou-96265723b/) .

>[!faq] Comment les supprimer ?
>La première fois que j'ai entendu parlé de ces metadonnées , c'était il y a 2 ans à l'aide d'une vidéo de David Bombal qui proposait un moyen de les supprimer dans une photo avec un script Python : https://youtu.be/A_itRNhbgZk?si=J8XGR3cDBjUpFR_h

## Le lien avec le Vibe Coding

J'ai parlé au tout début de Vibe Coding (avec une citation et tout - pour faire genre). Vous vous demandez le lien qu'il y a entre ce concept (bien connu des développeurs) et cette affaire ?

En vrai de vrai, il n'y en a aucun. En tout cas pas directement. C'est vrai que sur les réseaux actuellement, on associe souvent ces deux choses, non pas à tort puisque le principe même du Vibe Coding c'est de ne pas coder (programmer un logiciel) manuellement mais d'écrire juste ce qu'on veut et de laisser l'IA le faire à notre place en suivant nos instructions. L'idéal serait de ne pas toucher au code mais de se préoccuper uniquement du résultat (ça marche oui ou non?).

Et lorsqu'on responsabilise autant l'IA sur ce genre de choses, l'un des aspects qu'on occulte c'est la sécurité comme nous l'a montré cette affaire et d'autres.

Exemple : On a découvert fortuitement qu'un site web vraisemblablement *vibe codé* exposerait les emails que les utilisateurs entrent dans le code côté client 

<html lang="en">
<div class="tweet-container" >
<blockquote class="twitter-tweet"><p lang="en" dir="ltr">vibe code so hard, your entire waitlist is visible in frontend. <a href="https://t.co/AA342eg8Aj">https://t.co/AA342eg8Aj</a> <a href="https://t.co/LR33OkAxHk">pic.twitter.com/LR33OkAxHk</a></p>&mdash; Sahil Gulihar (@Sahil_Gulihar_) <a href="https://twitter.com/Sahil_Gulihar_/status/1946787529367179551?ref_src=twsrc%5Etfw">July 20, 2025</a>
</blockquote> 
</div>
<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script></html>



> [!info]
> Pour ce type d'applications notamment web, il y a le côté client c'est-à-dire le code et tout ce que l'utilisateur peut voir ou de façon plus précise le code qui sera exécuté ou rendu par le navigateur puis le côté serveur où la logique de l'application et les aspects comme les bases de données, les fonctionnalités etc sont implémentés et exécutés



Ce qui ne devrait pas être le cas puisque à aucun moment un utilisateur s'attend à ce que son adresse mail soit exposée sur la place publique étant donné que ça relève de ses informations privées.

Mais en soi, le site web fonctionne et fonctionne bien. Le développeur (si c'est bien un développeur) qui l'a conçu a atteint son objectif : son site marche mais lorsque l'IA a généré le code, il n'a pas tout vérifié, manqué de vigilance et a mis en péril la vie privée des utilisateurs qui lui ont fait confiance.

L'une des promesses ou plutôt finalité du vibe coding c'est le fait de confier absolument tout à l'IA du début à la fin (même la sécurité) et d'exclure le plus possible le développeur du processus. L'idéal serait que n'importe qui, qui a un appareil quelconque disposant d'une connexion internet puisse concevoir des logiciels sous toutes les formes sans maîtrise de la programmation.

## L'impact sur notre génération de développeurs

Même avant le vibe coding ou la forme qu'on lui connaît aujourd'hui, l'arrivée des IA comme GPT a bousculé un peu les choses. Surtout du côté des débutants comme moi. Heureusement ou malheureusement, pour mon cas, j'ai commencé la programmation (à l'université) l'année où c'est sorti et j'ai vu les conséquences que ce soit de mon côté comme dans mon entourage.

À vrai dire, ça permet d'aller vite. Les devoirs, les petits projets etc, tant que ça marche. Aujourd'hui les choses ont évolué et c'est devenu beaucoup plus sophistiqué, ça fait moins d'erreurs, ça prend moins de temps... Étant donné que ça fait partie des choses avec lesquelles nous (moi notamment) on a grandi et appris, ça devient quand même un peu inquiétant sur la qualité des logiciels ou de la valeur que nous allons produire. Ce n'est pas mauvais en soi. C'est tout de même un moyen comme un autre d'aller vite.

Mais des questions se posent. Jusqu'à quel point faut-il confier ce boulot à l'IA ? En cas de problème, qui accuser ? l'IA, le développeur ou celui qui a conçu l'IA ? Ce qui est sûr, les idées selon lesquelles les développeurs seront remplacés définitivement par l'IA sont de moins en moins probables. Déjà parce que le travail est bien plus large que l'écriture du code. Il y a comme nous l'avons abordé la sécurité, la nature et l'envergure du projet etc.

Certains sont allés jusqu'à dire qu'il ne faut plus orienter les enfants vers la programmation ou les métiers associés au risque qu'ils deviennent obsolètes. On ne va pas en vouloir à ceux-là. Mais l'effet contraire est en train d'être créé. En réalité, ce n'est plus qu'on a besoin de moins de développeurs mais on a besoin de plus de développeurs compétents, qui savent ce qu'ils font, qui ont un peu d'expérience, qui sont vigilants et qui apprennent vite (puisque bah l'IA va te suggérer ou générer des choses et par prudence tu iras chercher toi-même et comprendre un peu pour déterminer si tu vas l'intégrer ou plutôt si à long terme tu serais en mesure de maintenir l'application).


> [!info]
> Maintenir l'application  c'est assurer sa durabilité : corriger les bugs futurs, ajouter de nouvelles fonctionnalités... Et pour y arriver généralement, on s'assure qu'on ne complique pas trop les choses et que même dans 10 ans, soi-même ou quelqu'un qui prend le même projet pour la première fois puisse être en mesure de comprendre et de corriger si possible.



Tous ces éléments, qualités que j'ai cités pour un développeur à l'ère du vibe coding sont à l'opposé du développeur junior. C'est lui qui est le plus menacé : il doit prouver que ce qu'il sait faire n'est pas faisable par une IA (sinon où est l'intérêt de l'embaucher ?), il doit apprendre vite et maîtriser beaucoup de choses au cas où les choses tournent mal etc etc. Ce qui est difficile pour un "junior". Le senior lui en tout cas vu son expérience sera moins vulnérable et remplaçable par l'IA et encore mieux s'il associe son expérience et sa vigilance à la rapidité de l'IA.

On peut facilement faire le parallèle avec d'autres métiers qui sont d'une manière ou d'une autre touchés par l'IA. Quand je dis l'IA, c'est l'IA Générative puisqu'il y a plusieurs formes d'IA de la même manière qu'il y a plusieurs spécialités en médecine certaines moins connues ou plus délicates que d'autres. Aujourd'hui on ne fait plus trop la différence surtout pour ceux qui ne sont pas du domaine bien que la distinction reste importante.

C'est aussi pourquoi il faut faire de la vulgarisation, parler du sujet 


## Faire de la vulgarisation

<img src="Pasted image 20250727141936.png" class="center-image">


  *[Ceci](https://www.linkedin.com/company/the-lab-benin/posts?lipi=urn%3Ali%3Apage%3Ad_flagship3_feed%3BhE6owKNWQHKZDSXhos%2F3cw%3D%3D) par exemple est un cas de vulgarisation. Certains de mes camarades de promo ont fait une séance d'information et de vulgarisation sur l'intelligence artificielle à des élèves du secondaire à Ouidah le Samedi 26 Juillet 2025, histoire de faire découvrir ce monde qui n'est pas nouveau mais qui fait parler de lui, les métiers pour faire carrière dans le domaine, l'intérêt pour un africain, les défis etc.*

On a aussi https://friare.org qui s'intéresse particulièrement au côté éthique et moral de l'intelligence artificielle devenu de plus en plus crucial. Ou aussi www.isheero.com, un creuset des experts de l'IA du Bénin réunis autour d'un idéal de vulgarisation de l'IA, de formation et d'accompagnement dans le domaine. Et plein d'autres organismes ou institutions du genre.

D'ailleurs récemment des élèves du secondaire( Second Cycle notamment) au Bénin ont été  [sélectionnés](https://semecity.bj/ioai-2025-les-jeunes-talents-beninois-prets-a-representer-le-pays-en-chine/) pour participer à l'Olympiade Internationale de l'IA. 

<img class="center-image" src="https://media.licdn.com/dms/image/v2/D4E22AQG6SLZ1SeuYdA/feedshare-shrink_800/B4EZVCkpkTGYAk-/0/1740578661880?e=1756339200&v=beta&t=LrCrRr6Zq52nrE9Wod4TzfKudIqI2aaTGA4fJP44WPc">

Ils ont été formés à l'IA et on leur a aussi montré comment utiliser l'IA Générative  pour accélérer leur apprentissage .

Je ne saurai finir sans parler de l'[EEIA](https://eeia.bj/) qui est un camp d'été au Bénin de la Fondation Vallet  et la Bibliothèque Bénin Excellence où l'on forme  chaque année des milliers de jeunes ( même les enfants) provenant de 13 pays différents sur l'Intelligence Artificielle avec des projets et ceci avec le coaching d'experts .  ( C'est d'ailleurs grâce à cette Bibliothèque et à son club d'IA que j'ai été introduit au langage Python et que j'ai conçu mon premier programme d'IA 🙂‍↔️ )


## Conclusion

Bref en tant que développeur junior et au vu des affaires récentes, je partageais juste mon point de vue sur la question qui touche aussi beaucoup d'autres secteurs pour le meilleur ou pour le pire. Soyons un peu plus vigilants et faisons-nous accompagner par des experts ou des connaisseurs pour ne pas commettre l'irréparable. Il serait stupide aujourd'hui de dire d'exclure complètement l'IA du processus vu la place qu'elle occupe aujourd'hui. Mais les responsabilités sont beaucoup plus importantes pour l'humain que nous sommes surtout si la portée de nos actes touche beaucoup de personnes ou a un impact non négligeable.

On peut bien dire que l'IA ou le *vibe coding* crée des problèmes comme ceux de la sécurité mais si le développeur lui-même n'avait pas des réflexes ou des habitudes pour sécuriser ses conceptions, l'IA ne pourrait pas forcément anticiper tout à sa place. Même avant l'IA, les erreurs légères ou graves étaient faites mais aujourd'hui *<< le football a changé>>* ( pour ceux qui ont la ref) et les compétences qu'on demandait aux développeurs sont beaucoup plus strictes.  Des compétences différentes du fait d'écrire juste du code ...