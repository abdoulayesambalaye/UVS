# projet de abdoulaye syll master1 Big Data Sambalaye Diop master1 Big Data
Dans ce Readme, nous allons créer une application écrite en Scala à l'aide d'Apache Maven avec IntelliJ IDEA. on utilise Apache Maven comme système de construction. Et commence par un archétype Maven existant pour Scala fourni par IntelliJ IDEA. La création d'une application Scala dans IntelliJ IDEA implique les étapes suivantes:
Utilisez Maven comme système de construction.
    Mettez à jour le fichier de modèle d'objet de projet (POM) pour résoudre les dépendances du module Spark.
    Écrivez votre application dans Scala.
    Générez un fichier JAR qui peut être soumis aux clusters HDInsight Spark.
    Exécutez l'application sur le cluster Spark à l'aide de Livy.
    Dans ce didacticiel, nous allons:

    Installer le plugin Scala pour IntelliJ IDEA
    Utiliser IntelliJ pour développer une application Scala Maven
    Créer un projet Scala autonome
    nstaller le plugin Scala pour IntelliJ IDEA

les étapes suivantes pour installer le plugin Scala:

    Ouvrez IntelliJ IDEA.

    Sur l'écran d'accueil, accédez à Configurer> Plugins pour ouvrir la fenêtre Plugins.

    IntelliJ IDEA active le plugin scala
Sélectionnez Installer pour le plugin Scala présenté dans la nouvelle fenêtre.

utiliser IntelliJ pour créer une application

    Démarrez IntelliJ IDEA et sélectionnez Créer un nouveau projet pour ouvrir la fenêtre Nouveau projet.

    Sélectionnez Apache Spark / HDInsight dans le volet gauche.

    Sélectionnez Spark Project (Scala) dans la fenêtre principale.

    Dans la liste déroulante Outil de création, sélectionnez l'une des valeurs suivantes:
        Prise en charge de l'assistant de création de projet Maven pour Scala.
        SBT pour gérer les dépendances et construire pour le projet Scala.
        
        
Dans la fenêtre Nouveau projet, fournissez les informations suivantes:
Tableau 1
Description de la propriété
Nom du projet Saisissez un nom.
Emplacement du projet Saisissez l'emplacement pour enregistrer votre projet.
Projet SDK Ce champ sera vide lors de votre première utilisation d'IDEA. Sélectionnez Nouveau ... et accédez à votre JDK.
Version Spark L'assistant de création intègre la version appropriée pour Spark SDK et Scala SDK. Si la version du cluster Spark est antérieure à 2.0, sélectionnez Spark 1.x. Sinon, sélectionnez Spark2.x. Cet exemple utilise Spark 2.3.0 (Scala 2.11.8).
 
 Créer un projet Scala autonome

    Démarrez IntelliJ IDEA et sélectionnez Créer un nouveau projet pour ouvrir la fenêtre Nouveau projet.
    Sélectionnez Maven dans le volet gauche.
     Spécifiez un SDK de projet. S'il est vide, sélectionnez Nouveau ... et accédez au répertoire d'installation Java.

    Cochez la case Créer à partir de l'archétype.

    Dans la liste des archétypes, sélectionnez org.scala-tools.archetypes: scala-archetype-simple. Cet archétype crée la bonne structure de répertoires et télécharge les dépendances par défaut requises pour écrire le programme Scala.

    La capture d'écran montre l'archétype sélectionné dans la fenêtre Nouveau projet.
Sélectionnez Suivant.

Développez les coordonnées d'artefact. Fournissez les valeurs pertinentes pour GroupId et ArtifactId. Le nom et l'emplacement se rempliront automatiquement.

Dans les étapes ultérieures, vous mettez à jour le pom.xml pour définir les dépendances pour l'application Spark Scala. Pour que ces dépendances soient téléchargées et résolues automatiquement, vous devez configurer Maven.

Dans le menu Fichier, sélectionnez Paramètres pour ouvrir la fenêtre Paramètres.

Dans la fenêtre Paramètres, accédez à Génération, Exécution, Déploiement> Outils de création> Maven> Importation.

Cochez la case Importer automatiquement les projets Maven.

Sélectionnez Appliquer, puis sélectionnez OK. Vous serez ensuite renvoyé dans la fenêtre du projet.

Enregistrez les modifications dans pom.xml.

Créez le fichier .jar. IntelliJ IDEA permet la création de JAR en tant qu'artefact d'un projet. Suivez les étapes suivantes.

    Dans le menu Fichier, sélectionnez Structure du projet ....

    Dans la fenêtre Structure du projet, accédez à Artefacts> le symbole plus +> JAR> À partir de modules avec dépendances .…
Dans la fenêtre Créer un JAR à partir de modules, sélectionnez l'icône de dossier dans la zone de texte Classe principale.

Dans la fenêtre Sélectionner la classe principale, sélectionnez la classe qui apparaît par défaut, puis sélectionnez OK.
Dans la fenêtre Créer un JAR à partir de modules, sélectionnez l'icône de dossier dans la zone de texte Classe principale.

Dans la fenêtre Sélectionner la classe principale, sélectionnez la classe qui apparaît par défaut, puis sélectionnez OK.
Dans la fenêtre Créer un JAR à partir de modules, assurez-vous que l'option Extraire vers le JAR cible est sélectionnée, puis sélectionnez OK. Ce paramètre crée un seul JAR avec toutes les dépendances.
L'onglet Disposition de sortie répertorie tous les fichiers JAR inclus dans le cadre du projet Maven. Vous pouvez sélectionner et supprimer ceux sur lesquels l'application Scala n'a pas de dépendance directe. Pour l'application que vous créez ici, vous pouvez supprimer tout sauf le dernier (sortie de compilation SparkSimpleApp). Sélectionnez les pots à supprimer, puis sélectionnez le symbole négatif -.
Assurez-vous que la case à cocher Inclure dans la génération du projet est activée. Cette option garantit que le fichier JAR est créé à chaque fois que le projet est généré ou mis à jour. Sélectionnez Appliquer puis OK.

Pour créer le pot, accédez à Construire> Créer des artefacts> Construire. Le projet se compilera dans environ 30 secondes. Le fichier jar de sortie est créé sous \ out \ artifacts.

Sortie d'artefact de projet IntelliJ IDEA
ortie d'artefact de projet IntelliJ IDEA
Exécutez l'application sur le cluster Apache Spark

Pour exécuter l'application sur le cluster, vous pouvez utiliser les approches suivantes:

    Copiez le fichier jar d'application dans l'objet blob Stockage Azure associé au cluster. Vous pouvez utiliser AzCopy, un utilitaire de ligne de commande, pour ce faire. Il existe également de nombreux autres clients que vous pouvez utiliser pour télécharger des données. Pour en savoir plus, consultez la page Télécharger des données pour les tâches Apache Hadoop dans HDInsight.

    Utilisez Apache Livy pour soumettre une tâche d'application à distance au cluster Spark. Les clusters Spark sur HDInsight incluent Livy qui expose les points de terminaison REST pour soumettre à distance des travaux Spark. Pour plus d'informations, consultez Soumettre des tâches Apache Spark à distance à l'aide d'Apache Livy avec des clusters Spark sur HDInsight.
    
    Nettoyer les ressources

Si vous n'allez pas continuer à utiliser cette application, supprimez le cluster que vous avez créé en procédant comme suit:

    Connectez-vous au portail Azure.

    Dans la zone de recherche en haut, tapez HDInsight.

    Sélectionnez les clusters HDInsight sous Services.

    Dans la liste des clusters HDInsight qui apparaît, sélectionnez le ... en regard du cluster que vous avez créé pour ce didacticiel.

    Sélectionnez Supprimer. Sélectionnez Oui.
    
    Dans ce Readme, nous avons appris à créer une application Scala Apache Spark. 
