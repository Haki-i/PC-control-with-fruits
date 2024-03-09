# PC-control-with-fruits

# Objectif du projet

L'objectif est de réaliser deux programmes Python, l'un générant du son et l'autre contrôlant le clavier d’un ordinateur, lorsque l'on touche des fruits reliés à un circuit Arduino.

Vidéo du projet : <https://www.tiktok.com/@__hakii__/video/7315744375072443681>

# I- Conception électronique 

Nous souhaitons faire en sorte que, lorsqu'on touche un fruit, l'Arduino puisse recevoir un signal et envoyer des informations à un programme Python via Serial. Pour chaque fruit utilisé, nous répétons le même procédé.

## 1. Mise en place du circuit

### Matériels : 

- Un Arduino
- Des câbles crocodiles
- Des fruits
- Des résistances 10k ohms

### Schéma du circuit :

- Nous connectons à une broche numérique de l’Arduino une résistance de 10k ohms.
- L'autre extrémité de cette résistance est reliée au fruit par l'intermédiaire d'un câble crocodile.
- Nous relions de nouveau ce fruit, cette fois à une autre broche numérique de l'Arduino.

## 2. Fonctionnement du projet

**Comment l'Arduino détecte-t-il lorsqu'on touche un fruit ?**

L'Arduino joue le rôle d'un capteur capacitif qui mesure les changements dans la capacité électrique de notre circuit. Pour rappel, la capacité d'un système est sa capacité à stocker une charge électrique.

La bibliothèque **`CapacitiveSensor`** envoie une petite charge électrique à travers la broche d'émission. Lorsqu'on utilise un Arduino pour créer un capteur capacitif, ce qu'il mesure est le temps nécessaire pour que cette charge électrique "remplisse" la capacité entre les broches d'envoi et de réception jusqu'à un certain niveau.

Plus la capacité entre les broches est élevée, plus le temps pour atteindre un certain niveau est long. La bibliothèque **`CapacitiveSensor`** mesure le temps nécessaire pour que cette charge atteigne un niveau suffisant pour être détectée par la broche de réception.

Lorsqu'un objet conducteur (comme un doigt) entre en contact avec le fruit, il modifie la capacité mesurée par la broche de réception. En présence d'un conducteur supplémentaire, cette capacité augmente. Le corps humain, étant conducteur et ayant sa propre capacité électrique, s'ajoute à la capacité existante entre les broches.

Cette augmentation de capacité signifie que le circuit prend plus de temps pour atteindre le niveau de charge nécessaire pour être détecté par la broche de réception. L'Arduino mesure ce temps prolongé, ce qui lui permet de détecter que l'objet a été touché.

Lorsqu'on touche l'objet avec le doigt, on ajoute une extension au circuit et on introduit un nouveau chemin pour le courant électrique. Pour que ce courant circule efficacement et pour que le circuit soit complet, il doit y avoir un retour au ground de l'Arduino.

En conclusion, si l'on touche le fruit avec notre doigt, l'Arduino le détecte et envoie l'information à nos programmes Python via Serial.

En disposant de plusieurs fruits reliés à différentes broches, nous pouvons envoyer une valeur différente pour différencier les actions à réaliser sur Python.

# II- Conception informatique

## 1. Jeu du dinosaure

Pour simuler le clavier de notre ordinateur et jouer au jeu du dinosaure sur Google, nous utiliserons la bibliothèque **`keyboard`**.

Lorsque nous voudrons faire sauter le dinosaure, nous toucherons un fruit. Grâce à la bibliothèque Serial, nous écoutons si le port reçoit une information. Si c'est le cas, nous simulons l'appui sur la barre espace.

Ainsi, à chaque fois que nous toucherons le fruit, cela équivaudra à presser la touche espace.

## 2. Jouer de la musique

Pour jouer de la musique, nous utiliserons la bibliothèque **`fluidsynth`**. Celle-ci nous permettra de simuler le son d'instruments de musique, notamment en téléchargeant différents fichiers .SF2.

Le format SF2 permet de stocker une large gamme de données sur des instruments, ce qui permet de reproduire de manière réaliste leurs sons. Pour notre projet, nous utiliserons les fichiers d'un violon, d'une batterie, et d'une chorale.

Pour contrôler ces 3 instruments, nous aurons besoin de trois fruits différents qui renvoient chacun une valeur différente par Serial. En fonction de la valeur reçue, notre programme Python active le son d'un instrument.

# Rendu final 

![ezgif com-crop](https://github.com/Haki-i/PC-control-with-fruits/assets/137703849/fe025a52-8b9a-4820-bf86-489db9d0ed29)
