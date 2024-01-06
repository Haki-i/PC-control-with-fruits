# PC-control-with-fruits

# Objectif du projet

Jouer sur son PC ou faire de la musique avec des fruits en combinant Arduino et Python

Vidéo du projet : <https://www.tiktok.com/@__hakii__/video/7315744375072443681>

# Conception électronique et programmation Arduino

Nous souhaitons que, lorsqu'on touche un fruit, l'Arduino puisse recevoir un signal et envoyer des informations à un programme Python via la communication série. Ce processus est répété pour chaque fruit utilisé.

### Montage du circuit

- Un Arduino
- Des câbles crocodiles
- Des fruits
- Des résistances 10k ohms

Schéma du circuit :

- Nous connectons une résistance de 10k ohms à la broche D2 de l’Arduino.
- L'autre extrémité de cette résistance est reliée au fruit par l'intermédiaire d'un câble crocodile.
- Nous relions ensuite ce fruit à la broche D3 de l'Arduino.

### Programmation Arduino

Pour détecter si un fruit est touché, nous utiliserons la bibliothèque `CapacitiveSensor`.

- Nous déclarons un objet de type `CapacitiveSensor` en indiquant la broche d’envoi puis la broche de réception.
- Dans le `loop`, nous lisons les données de notre capteur capacitif.
- Nous stockons ces données dans un tableau que nous envoyons par serial.


### Fonctionnement du projet

Comment l’Arduino détecte-t-il lorsque l’on touche un fruit ?

L'Arduino agit comme un capteur capacitif, mesurant les changements dans la capacité électrique du circuit. La capacité d’un système est sa capacité à stocker une charge électrique. 

La bibliothèque `CapacitiveSensor` envoie une petite charge électrique à travers la broche d'émission. Lorsqu'un Arduino est utilisé pour créer un capteur capacitif, il mesure le temps nécessaire pour que cette charge électrique "remplisse" la capacité entre les broches d'envoi et de réception jusqu'à un certain niveau.

Plus la capacité entre les broches est élevée, plus le temps pour atteindre un certain niveau est long. La bibliothèque `CapacitiveSensor` mesure le temps qu'il faut pour que cette charge atteigne un niveau suffisant pour être détectée par la broche de réception.

Quand l'Arduino envoie un signal électrique à travers la broche d'envoi, cela crée un champ électrique autour de cette broche. Lorsqu'un objet conducteur (comme un doigt) entre en contact avec le fruit, il modifie le champ électrique du circuit et change la capacité mesurée par la broche de réception. En présence d'un conducteur supplémentaire, cette capacité augmente. Le corps humain étant conducteur et ayant sa propre capacité électrique, il s'ajoute à la capacité existante entre les broches.

Cette augmentation de la capacité signifie que le circuit prend plus de temps pour atteindre le niveau de charge nécessaire pour être détecté par la broche de réception. L'Arduino mesure ce temps prolongé, ce qui lui permet de détecter que l'objet a été touché.

Lorsqu’on touche l'objet avec le doigt, on ajoute une extension au circuit et on introduit un nouveau chemin pour le courant électrique. Pour que ce courant circule efficacement et pour que le circuit soit complet, il doit y avoir un retour au ground de l'Arduino.

# Rendu final 

![ezgif com-crop](https://github.com/Haki-i/PC-control-with-fruits/assets/137703849/fe025a52-8b9a-4820-bf86-489db9d0ed29)
