# Reinforcement Learning TP3


# Comparaison des algorithmes Q-Learning et SARSA sur le jeu Taxi-v3

## Introduction

Ce projet implémente et compare deux algorithmes d'apprentissage par renforcement : Q-Learning et SARSA, appliqués au jeu Taxi-v3 de Gym. Les deux méthodes ont été évaluées en fonction de leurs performances, avec des variantes pour Q-Learning intégrant ou non un scheduling de l'epsilon.

## Algorithmes Implémentés

### Q-Learning

Q-Learning est un algorithme off-policy qui met à jour la fonction de valeur en utilisant l'action optimale attendue, indépendamment de l'action réellement prise par l'agent. L'agent suit une politique **epsilon-greedy**, ce qui favorise l'exploration au début de l'entraînement avant de se concentrer sur l'exploitation des actions optimales. Deux versions de Q-Learning ont été implémentées :
- **Sans scheduling de l'epsilon** : l'epsilon reste constant au fil du temps.
- **Avec scheduling de l'epsilon** : l'epsilon diminue progressivement, encourageant ainsi la transition entre exploration et exploitation.

### SARSA

SARSA (State-Action-Reward-State-Action) est un algorithme on-policy. Contrairement à Q-Learning, il met à jour la fonction de valeur en fonction de l'action réellement prise par l'agent. SARSA utilise également une politique **epsilon-greedy**, mais la mise à jour des valeurs des paires état-action repose sur la politique suivie par l'agent.

## Paramètres

Les deux algorithmes ont été exécutés avec les mêmes paramètres :
- **Taux d'apprentissage (alpha)** : 0.5
- **Facteur de discount (gamma)** : 0.99
- **Epsilon initial pour epsilon-greedy** : 0.1

Pour la version avec scheduling de Q-Learning, l'epsilon diminue progressivement avec le temps, favorisant l'exploration au début de l'entraînement puis l'exploitation à mesure que l'agent apprend.

## Résultats

- Q-Learning sans scheduling converge plus lentement et atteint une récompense moyenne plus faible.
- Q-Learning avec scheduling prend plus de temps pour converger mais obtient une récompense moyenne plus élevée grâce à une meilleure gestion de la transition entre exploration et exploitation.
- SARSA converge plus rapidement et atteint la meilleure récompense moyenne.

Les performances sur les 100 derniers épisodes d'entraînement sont les suivantes :
- **Q-Learning sans scheduling** : Récompense moyenne de 3.08
- **Q-Learning avec scheduling** : Récompense moyenne de 5.49
- **SARSA** : Récompense moyenne de 7.72

## Conclusion

L'introduction d'un scheduling pour l'epsilon améliore les performances de Q-Learning en équilibrant mieux l'exploration et l'exploitation. Cependant, SARSA surpasse Q-Learning, ce qui suggère que dans cet environnement, une approche on-policy est plus efficace.

