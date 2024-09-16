#docker 

Les conteneurs Docker vous apportent aussi les notions de _stateless_ et d'_immutabilité_.

#### Stateless et immutabilité

##### _Stateless_ vs _Stateful_

Dans le monde de Docker, vous allez souvent entendre parler de **stateless et stateful**, deux catégories de conteneurs, et vous devez savoir à quoi correspond chaque catégorie.

Si nous prenons le cas d'une **base de donnée MySQL**, celle-ci est **stateful** car elle stocke un état. Ainsi, si vous éteignez et rallumez votre base de données, vous la retrouverez dans le même état de fonctionnement.

Stateless est donc l'inverse : l'application ne stocke pas d'état. Vous pouvez prendre le cas du **protocole HTTP**, celui-ci est **stateless**. À chaque nouvelle requête HTTP, les mêmes séries d'actions seront réalisées.

##### Un conteneur est immuable

**L'immutabilité** d'un conteneur est aussi importante. Un conteneur ne doit pas stocker de données qui doivent être pérennes, car il les perdra (à moins que vous les ayez pérennisées). Mais si vous souhaitez en local mettre une base de données dans un conteneur Docker, vous devez créer un volume pour que celui-ci puisse stocker les données de façon pérenne.