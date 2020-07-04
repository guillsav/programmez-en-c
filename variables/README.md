# **Variables**

Alors une variable, c'est quoi?
Eh bien c'est une petite information temporaire qu'on stocke dans la RAM. Tout simplement.
On dit qu'elle est "variable" car c'est une valeur qui peut changer pendant le déroulement du programme. Par exemple, notre nombre 5 de tout à l'heure (le nombre de vies restant au joueur) risque de diminuer au fil du temps. Si ce nombre atteint 0, on saura que le joueur a perdu.

Nos programmes, vous allez le voir, sont remplis de variables. Vous allez en voir partout, à toutes les sauces.

En langage C, une variable est constituée de deux choses:

- Une **valeur**: C'est le nombre qu'elle stocke, par exemple 5.
- Un **nom**: C'est ce qui permet de la reconnaître. En programmant en C, on n'aura pas à retenir l'adresse mémoire (ouf!): à la place, on va juste indiquer des noms de variables. C'est le compilateur qui fera la conversion entre le nom et l'adresse. Voilà déjà un souci de moins.

### **Donner un nom à ses variables**

En langage C, chaque variable doit donc avoir un nom. Pour notre fameuse variable qui retient le nombre de vies, on aimerait bien l'appeler "Nombre de vies" ou quelque chose du genre.

Hélas, il y a quelques contraintes. Vous ne pouvez pas appeler une variable n'importe comment:

- Il ne peut y avoir que des minuscules, majuscules et des chiffres (`abcABC012`);
- votre nom de variable doit commencer par une lettre
- Les espaces sont interdits. À la place, on peut utiliser le caractère "underscore" \_ (qui ressemble à un trait de soulignement). C'est le seul caractère différent des lettres et chiffres autorisé.
- Vous n'avez pas le droit d'utiliser des accents (`éàê` etc.).

Enfin, et c'est très important à savoir, le langage C fait la différence entre les majuscules et les minuscules. Pour votre culture, sachez qu'on dit que c'est un langage qui "respecte la casse".

Donc, du coup, les variables `largeur`, `LARGEUR` ou encore `LArgEurR` sont trois variables différentes en langage C, même si pour nous ça a l'air de signifier la même chose!

Voici quelques exemples de noms de variables corrects: `nombreDeVies`, `prenom`, `nom`, `numero_de_telephone`, `numeroDeTelephone`.

Chaque programmeur a sa propre façon de nommer des variables. Pendant ce cours, je vais vous montrer ma manière de faire:

- Je commence tous mes noms de variables par une lettre minuscule.
- S'il y a plusieurs mots dans mon nom de variable, je mets une lettre majuscule au début de chaque nouveau mot.

Je vais vous demander de faire de la même manière que moi, ça nous permettra d'être sur la même longueur d'ondes.

> Quoi que vous fassiez, faites en sorte de donner des noms clairs à vos variables. On aurait pu abréger `nombreDeVies`, en l'écrivant par exemple `nvd`. C'est peut-être plus court, mais c'est beaucoup moins clair pour vous quand vous relisez votre code. N'ayez donc pas peur de donner des noms un peu plus longs pour que ça reste compréhensible.

### **Les types de variables**

Notre ordinateur, vous pourrez le constater, n'est en fait rien d'autre qu'une (très grosse) machine à calculer. Il ne sait traiter que des nombres.

Oui mais voilà, j'ai un scoop ! Il existe plusieurs types de nombres ! Par exemple, il y a les nombres entiers positifs:

- 45
- 398
- 7650

Mais il y a aussi des nombres décimaux, c'est-à-dire des nombres à virgule:

- 75.909
- 1.7741
- 9810.7

En plus de ça, il y a aussi des nombres entiers négatifs:

- -87
- -916

… Et des nombres négatifs décimaux!

- -76.9
- -100.11

Votre pauvre ordinateur a besoin d'aide! Lorsque vous lui demandez de stocker un nombre, vous devez dire de quel type il est. Ce n'est pas vraiment qu'il ne soit pas capable de le reconnaître tout seul, mais… ça l'aide beaucoup à s'organiser, et à faire en sorte de ne pas prendre trop de mémoire pour rien.

Lorsque vous créez une variable, vous allez donc devoir `indiquer son type`.
Voici les principaux types de variables existant en langage C:

| Nom du type   | Minimum        | Maximum       |
| ------------- | -------------- | ------------- |
| `signed char` | -127           | 127           |
| `int`         | -32,767        | 32,767        |
| `long`        | -2,147,487,687 | 2,147,487,687 |
| `float`       | -1 x1037       | 1 x1037       |
| `double`      | -1 x1037       | 1 x1037       |

> Les valeurs présentées ci-dessus sont les minimums garantis par le langage. En réalité, il est fort probable que vous puissiez stocker des valeurs plus élevées que celles-ci. Cependant, veillez à garder ces valeurs en tête lorsque vous choisissez un type, c'est important.

> Notez que tous les types n'ont pas été présentés, seul les principaux ont été conservés.

Les trois premiers types (`signed char`, `int`, `long`) permettent de stocker des nombres entiers : 1, 2, 3, 4…

Les deux derniers (`float`, `double`) permettent de stocker des nombres décimaux (appelés nombres **flottants**) : 13.8, 16.911…

Vous verrez que la plupart du temps on manipule des nombres entiers (tant mieux, parce que c'est plus facile à utiliser).

> Attention avec les nombres décimaux! Votre ordinateur ne connaît pas la virgule, il utilise le point. Vous ne devez donc pas écrire 54,9 mais plutôt 54.9!

Ce n'est pas tout! Pour les types entiers (`signed char`, `int`, `long` …), il existe d'autres types dits `unsigned` (non signés) qui eux ne peuvent stocker que des nombres positifs. Pour les utiliser, il suffit d'écrire le mot `unsigned` devant le type:

| Type            |                   |
| --------------- | ----------------- |
| `unsigned char` | 0 à 255           |
| `unsigned int`  | 0 à 65,535        |
| `unsigned long` | 0 à 4,294,967,295 |

Comme vous le voyez, les `unsigned` sont des types qui ont le défaut de ne pas pouvoir stocker de nombres négatifs, mais l'avantage de pouvoir stocker des nombres deux fois plus grands (`signed char` s'arrête à 127, tandis que `unsigned char` s'arrête à 255 par exemple).

> Vous remarquerez que le typechara été présenté soit avec le mot-clé `signed`, soit avec le mot-clé `unsigned`, mais jamais seul. La raison en est toute simple: le type peut-être signé ou non signé suivant les machines. Veillez donc à spécifier lequel des deux vous souhaitez utiliser suivant le type de valeur que vous désirez stocker.

> Pourquoi avoir créé trois types pour les nombres entiers? Un seul type aurait été suffisant, non?

Oui, mais on a créé à l'origine plusieurs types pour économiser de la mémoire. Ainsi, quand on dit à l'ordinateur qu'on a besoin d'une variable de type `char`, on prend moins d'espace en mémoire que si on avait demandé une variable de type `int`.

Toutefois, c'était utile surtout à l'époque où la mémoire était limitée. Aujourd'hui, nos ordinateurs ont largement assez de mémoire vive pour que ça ne soit plus vraiment un problème. Il ne sera donc pas utile de se prendre la tête pendant des heures sur le choix d'un type. Si vous ne savez pas si votre variable risque de prendre une grosse valeur, mettez `int` (ou `double` pour un flottant).

En résumé, on fera surtout la distinction entre nombres entiers et flottants:

- Pour un nombre entier, on utilisera le plus souvent `int`
- Pour un nombre flottant, on utilisera généralement `double`

## **Déclarer une variable**

On y arrive. Maintenant, créez un nouveau projet console que vous appellerez "variables".

On va voir comment déclarer une variable, c'est-à-dire **demander à l'ordinateur la permission d'utiliser un peu de mémoire**.

Une déclaration de variable, c'est très simple maintenant que vous savez tout ce qu'il faut. Il suffit dans l'ordre:

1. D'indiquer le type de la variable que l'on veut créer
2. D'insérer un espace
3. D'indiquer le nom que vous voulez donner à la variable
4. Et enfin, de ne pas oublier le point-virgule

Par exemple, si je veux créer ma variable `nombreDeVies` de type `int`, je dois taper la ligne suivante:

```c
int nombreDeVies;
```

Et c'est tout! Quelques autres exemples stupides pour la forme:

```c
int noteDeMaths;
double sommeArgentRecue;
unsigned int int noteDeMaths;
double sommeArgentRecue;
unsigned int nombreDeLecteursEnTrainDeLireUnNomDeVariableUnPeuLong;
```

on bref, vous avez compris le principe je pense!

Ce qu'on fait là s'appelle une **déclaration de variable** (un vocabulaire à retenir). Vous devez faire les déclarations de variables au début des fonctions. Comme pour le moment on n'a qu'une seule fonction (la fonction `main`), vous allez déclarer la variable comme ceci:

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[]) // Équivalent de int main()
{
  int nombreDeVies;

  return 0;
}
```

Si vous lancez le programme ci-dessus, vous constaterez avec stupeur… qu'il ne fait rien.

#### **Quelques explications**

Alors, avant que vous ne m'étrangliez en croyant que je vous mène en bateau depuis tout à l'heure, laissez-moi juste dire une chose pour ma défense.

En fait, il se passe des choses, mais vous ne les voyez pas. Lorsque le programme arrive à la ligne de la déclaration de variable, il demande bien gentiment à l'ordinateur s'il peut utiliser un peu d'espace dans la mémoire vive.
Si tout va bien, l'ordinateur répond "Oui bien sûr, fais comme chez toi". Généralement, cela se passe sans problème. Le seul souci qu'il pourrait y avoir, c'est qu'il n'y ait plus de place en mémoire… Mais heureusement cela arrive rarement, car pour remplir toute la mémoire rien qu'avec des `int` il faut vraiment le vouloir!

Soyez donc sans crainte, vos variables devraient normalement être créées sans souci.

> Une petite astuce à connaître: si vous avez plusieurs variables du même type à déclarer, inutile de faire une ligne pour chaque variable. Il vous suffit de séparer les différents noms de variables par des virgules sur la même ligne: `int nombreDeVies, niveau, ageDuJoueur;`. Cela créera trois variables `int` appelées `nombreDeVies`, `niveau` et `ageDuJoueur`.

Et maintenant?
Maintenant qu'on a créé notre variable, on va pouvoir lui donner une valeur.

## **Affecter une valeur à une variable**

C'est tout ce qu'il y a de plus bête. Si vous voulez donner une valeur à la variable `nombreDeVies`, il suffit de procéder comme ceci:

```c
nombreDeVies = 5;
```

Rien de plus à faire. Vous indiquez le nom de la variable, un signe égal, puis la valeur que vous voulez y mettre.
Ici, on vient de donner la valeur 5 à la variable `nombreDeVies`.
Notre programme complet ressemble donc à ceci:

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char *argv[])
{
  int nombreDeVies;
  nombreDeVies = 5;

  return 0;
}
```

Là encore, rien ne s'affiche à l'écran, tout se passe dans la mémoire.
Quelque part dans les tréfonds de votre ordinateur, une petite case de mémoire vient de prendre la valeur 5. N'est-ce pas magnifique?

On peut s'amuser si on veut à changer la valeur par la suite:

```c
int nombreDeVies;
nombreDeVies = 5;
nombreDeVies = 4;
nombreDeVies = 3;
```

Dans cet exemple, la variable va prendre d'abord la valeur 5, puis 4, et enfin 3. Comme votre ordinateur est très rapide, tout cela se passe extrêmement vite. Vous n'avez pas le temps de cligner des yeux que votre variable vient de prendre les valeurs 5, 4 et 3… et ça y est, votre programme est fini.
