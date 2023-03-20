# Boucle bloquante

Cet exemple met en évidence une erreur conceptuelle et les conséquences de l'appel de fonctions trop longues à s'exécuter.

## Analyse

Après avoir cliqué sur le bouton `Démarrer`, la sortie de l'application (journal) affiche l'incrémentation des valeurs de la variable `i`. Sur certaines plateformes, la barre de progression reste figée, sur d'autres, notamment sous Windows, elle ne l'est pas.

Le clic sur le bouton `Démarrer` a provoqué l'appel à une fonction dont l'exécution dure plusieurs secondes. Cette fonction simule un traitement long et bloquant, du type `for() {}`, elle bloque la run-loop du l'objet graphique. Il est alors impossible d'interrompre le traitement et de cliquer sur un autre bouton puisque le thread de l'application est totalement occupé. 

Il faut attendre la fin du traitement pour que l'interface graphique réponde à nouveau.

Même si, en apparence l'application fonctionne car la barre de progression fonctionne, sous Windows, le fait qu'elle n'ait pas le même comportement sur toutes les plateformes est un échec. De plus, le fait de ne pas pouvoir interrompre un traitement long est également inacceptable pour un utilisateur qui aura tôt fait de croire l'application bloquée et forcer sa fermeture.

Une autre approche est proposée dans l'exemple **Bouble non bloquante**.
