# TP1 : Manipulation du système de fichiers HDFS

## Objectif 
Ce TP vise à familiariser les apprenants avec le système de fichiers distribué Hadoop (HDFS). Les objectifs spécifiques comprennent le démarrage des processus Hadoop, la création d'une structure d'arborescence dans le HDFS, la manipulation de fichiers en utilisant des commandes Hadoop, la copie de fichiers entre différents répertoires, la visualisation du contenu des fichiers, et la gestion des fichiers locaux et distants.

**1. Démarrage des processus Hadoop**

Pour démarrer les processus Hadoop, nous utilisons les commandes suivantes :

```bash
start-dfs.sh
start-yarn.sh
```

Nous vérifions ensuite que les processus sont en cours d'exécution avec la commande `jps`. Nous accédons à l'interface web de NameNode en utilisant le lien http://localhost:50070.

**2. Création de l'arborescence dans le HDFS**

![Arbre](assets/arbre.png)

Nous créons la structure demandée dans la racine du HDFS avec les commandes Hadoop suivantes :

```bash
hadoop fs -mkdir /BDDC
hadoop fs -mkdir /BDDC/JAVA
hadoop fs -mkdir /BDDC/JAVA/TPs
hadoop fs -mkdir /BDDC/JAVA/Cours
hadoop fs -mkdir /BDDC/CPP
hadoop fs -mkdir /BDDC/CPP/TPs
hadoop fs -mkdir /BDDC/CPP/Cours
```
`Commandes en raccourci pour créer l'arborescence demandée dans le HDFS :`
```bash
hadoop fs -mkdir -p /BDDC/{JAVA/{TPs,Cours},CPP/{TPs,Cours}}
```



**3. Création et ajout de contenu dans les fichiers Cours de CPP**

```bash
hadoop fs -mkdir /BDDC/CPP/Cours
hadoop fs -put CoursCPP1 /BDDC/CPP/Cours
hadoop fs -put CoursCPP2 /BDDC/CPP/Cours
hadoop fs -put CoursCPP3 /BDDC/CPP/Cours
```

**4. Affichage du contenu des fichiers CoursCPP1, CoursCPP2 et CoursCPP3**

```bash
hadoop fs -cat /BDDC/CPP/Cours/CoursCPP1
hadoop fs -cat /BDDC/CPP/Cours/CoursCPP2
hadoop fs -cat /BDDC/CPP/Cours/CoursCPP3
```

**5. Copie des fichiers CPP vers le répertoire JAVA**

```bash
hadoop fs -cp /BDDC/CPP/Cours/CoursCPP1 /BDDC/JAVA/Cours/CoursJAVA1
hadoop fs -cp /BDDC/CPP/Cours/CoursCPP2 /BDDC/JAVA/Cours/CoursJAVA2
hadoop fs -cp /BDDC/CPP/Cours/CoursCPP3 /BDDC/JAVA/Cours/CoursJAVA3
```

**6. Suppression et renommage des fichiers dans le répertoire JAVA**

```bash
hadoop fs -rm /BDDC/JAVA/Cours/CoursJAVA3
hadoop fs -mv /BDDC/JAVA/Cours/CoursJAVA1 /BDDC/JAVA/Cours/CoursJAVA1
hadoop fs -mv /BDDC/JAVA/Cours/CoursJAVA2 /BDDC/JAVA/Cours/CoursJAVA2
```

**7. Création de fichiers locaux**

```bash
touch TP1CPP TP2CPP TP1JAVA TP2JAVA TP3JAVA
```

**8. Copie des fichiers locaux vers le HDFS**

```bash
hadoop fs -copyFromLocal TP1CPP /BDDC/CPP/TPs
hadoop fs -copyFromLocal TP2CPP /BDDC/CPP/TPs
hadoop fs -copyFromLocal TP1JAVA /BDDC/JAVA/TPs
hadoop fs -copyFromLocal TP2JAVA /BDDC/JAVA/TPs
hadoop fs -copyFromLocal TP3JAVA /BDDC/JAVA/TPs
```

**9. Affichage récursif du contenu de BDDC**

```bash
hadoop fs -ls -R /BDDC
```

**10. Suppression du fichier TP1CPP**

```bash
hadoop fs -rm /BDDC/CPP/TPs/TP1CPP
```

**11. Suppression du répertoire JAVA et de son contenu**

```bash
hadoop fs -rm -r /BDDC/JAVA
```

Ce rapport résume les différentes étapes de manipulation du système de fichiers HDFS conformément aux instructions fournies.