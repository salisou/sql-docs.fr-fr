---
title: Notes de publication de DacFx et de SqlPackage
description: Notes de publication de Microsoft SqlPackage.
ms.custom: tools|sos
ms.date: 02/02/2019
ms.prod: sql
ms.reviewer: alayu; sstein
ms.prod_service: sql-tools
ms.topic: conceptual
author: pensivebrian
ms.author: broneill
manager: kenvh
ms.openlocfilehash: 0b034a0c0d449bd85afbfd46fa407e34921b8cf2
ms.sourcegitcommit: bfb5e79586fd08d8e48e9df0e9c76d1f6c2004e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82262128"
---
# <a name="release-notes-for-sqlpackageexe"></a>Notes de version de SqlPackage.exe

**[Télécharger la version la plus récente](sqlpackage-download.md)**

Cet article présente les fonctionnalités et les correctifs fournis par les versions commerciales de SqlPackage.exe.

<!--
TODO:
The Introduction text needs to add clarity regarding the relationship between
'SqlPackage.exe' and 'DacFx' (the Microsoft 'Data-Tier Application Framework').
One added sentence would be sufficient.

Or, if there is no relationship, remove 'DacFx' from the metadata 'title:'.

I discussed this with SStein (SteveStein).
Thanks.  GeneMi (MightyPen in GitHub).  2019-03-27
-->
## <a name="185-sqlpackage"></a>18.5 sqlpackage

|Plateforme|Téléchargement|Date de publication|Version|Build
|:---|:---|:---|:---|:---|
| Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2128142)|28 avril 2020|18.5|15.0.4769.1|
|macOS .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2128145)|28 avril 2020| 18.5|15.0.4769.1|
|Linux .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2128144)|28 avril 2020| 18.5|15.0.4769.1|
|Windows .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2128143)|28 avril 2020| 18.5|15.0.4769.1|

### <a name="features"></a>Fonctionnalités
| Fonctionnalité | Détails |
| :------ | :------ |
| Déploiement | La classification de la sensibilité des données est maintenant prise en charge pour SQL Server 2008 et ultérieur, Azure SQL Database et Azure SQL Data Warehouse |
| Déploiement | Ajout de la prise en charge des contraintes de table dans Azure SQL Data Warehouse |
| Déploiement | Ajout de la prise en charge de l’index columnstore en cluster ordonné dans SQL Data Warehouse |
| Déploiement | Ajout de la prise en charge de la source de données externe (pour Oracle, Teradata, MongoDB/CosmosDB, ODBC, cluster Big Data) et de la table externe pour le cluster Big Data SQL Server 2019 |
| Déploiement | Ajout de SQL Database Edge comme édition prise en charge |
| Déploiement | Prise en charge des noms de serveur Managed Instance au format « \<serveur>.\<zonedns>.database.windows.net » |
| Déploiement | Ajout de la prise en charge de la commande copy dans Azure SQL Data Warehouse |
| Déploiement | Ajout de l’option de déploiement « IgnoreTablePartitionOptions » durant la publication pour éviter la recréation de la table en cas de modification de la fonction de partition sur la table pour Azure SQL Data Warehouse |
| .NET Core | Ajout de la prise en charge de Microsoft.Data.SqlClient dans la version .NET Core de sqlpackage |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs
| Fix | Détails |
| :-- | :------ |
| Déploiement | Correction de la publication du package DAC d’une base de données contenant un utilisateur externe qui générait une erreur « La référence d’objet n’a pas la valeur d’une instance d’un objet ». |
| Déploiement | Correction de l’analyse du chemin JSON en tant qu’expression |
| Déploiement | Correction de la génération d’instructions GRANT pour les autorisations AlterAnyDatabaseScopedConfiguration et AlterAnySensitivityClassification |
| Déploiement | Correction d’un problème entraînant la non-reconnaissance d’une autorisation de script externe |
| Déploiement | Correction de la propriété inline : l’ajout implicite de la propriété ne doit pas apparaître dans la différence, mais une mention explicite doit apparaître dans le script |
| Déploiement | Résolution d’un problème où la modification d’une table référencée par une vue matérialisée entraîne la génération d’instructions Alter View qui ne sont pas prises en charge dans les vues matérialisées pour Azure SQL Data Warehouse |
| Déploiement | Correction de l’échec de la publication lors de l’ajout d’une colonne à une table avec des données pour Azure SQL Data Warehouse |
| Déploiement | Correction du script de mise à jour devant déplacer les données vers une nouvelle table lors de la modification du type de colonne de distribution (scénario de perte de données) pour Azure SQL Data Warehouse |
| ScriptDom | Correction d’un bogue dans ScriptDom entraînant la non-reconnaissance des contraintes inline définies après un index inline |
| ScriptDom | Correction dans ScriptDom d’une parenthèse fermante manquante SYSTEM_TIME dans une instruction de traitement par lots |
| Always Encrypted | Correction de l’échec de la suppression de la table #tmpErrors lorsque sqlpackage se reconnecte et que la table temporaire est déjà supprimée (la table temporaire disparaissant quand la connexion est perdue) |
| &nbsp; | &nbsp; |

## <a name="1841-sqlpackage"></a>sqlpackage 18.4.1

|Plateforme|Téléchargement|Date de publication|Version|Build
|:---|:---|:---|:---|:---|
| Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2113703)|13 décembre 2019|18.4.1|15.0.4630.1|
|macOS .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2113705)|13 décembre 2019| 18.4.1|15.0.4630.1|
|Linux .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2113331)|13 décembre 2019| 18.4.1|15.0.4630.1|
|Windows .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2113704)|13 décembre 2019| 18.4.1|15.0.4630.1|

### <a name="fixes"></a>Correctifs
| Fix | Détails |
| :-- | :------ |
| ScriptDom |  Une régression de l’analyse ScriptDom a été introduite dans la version 18.3.1, où ’RENAME’ n’est pas traité correctement comme un jeton de niveau supérieur, ce qui entraîne l’échec de l’analyse.
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus 

| Fonctionnalité | Détails |
| :------ | :------ |
| Déploiement |  Une régression introduite dans la version 18.4.1 provoque l’erreur « La référence d’objet n’a pas pour valeur une instance d’un objet. » lors du déploiement d’un dacpac ou de l’importation d’un bacpac avec un utilisateur disposant d’une connexion externe. Contournez ce problème en utilisant sqlpackage 18.4. Ce sera corrigé dans la prochaine version de sqlpackage. | 
| &nbsp; | &nbsp; |

## <a name="184-sqlpackage"></a>sqlpackage 18.4

|Plateforme|Téléchargement|Date de publication|Version|Build
|:---|:---|:---|:---|:---|
| Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2108813)|29 octobre 2019|18.4|15.0.4573.2|
|macOS .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2108815)|29 octobre 2019| 18.4|15.0.4573.2|
|Linux .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2108814)|29 octobre 2019| 18.4|15.0.4573.2|
|Windows .NET Core |[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2109019)|29 octobre 2019| 18.4|15.0.4573.2|

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Déploiement | Ajout de la prise en charge pour le déploiement sur Azure SQL Data Warehouse (GA). | 
| Plateforme | sqlpackage .NET Core GA pour macOS, Linux et Windows. | 
| Sécurité | Suppression de la signature du code SHA1. |
| Déploiement | Ajout de la prise en charge des nouvelles éditions des bases de données Azure : GeneralPurpose, BusinessCritical, Hyperscale |
| Déploiement | Ajout de la prise en charge de Managed Instance pour les groupes et utilisateurs AAD. |
| Déploiement | Prise en charge du paramètre /AccessToken pour sqlpackage sur .NET Core. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus 

| Fonctionnalité | Détails |
| :------ | :------ |
| ScriptDom |  Une régression de l’analyse ScriptDom a été introduite dans la version 18.3.1, où ’RENAME’ n’est pas traité correctement comme un jeton de niveau supérieur, ce qui entraîne l’échec de l’analyse. Ce problème sera résolu dans la prochaine version de sqlpackage. | 
| &nbsp; | &nbsp; |

### <a name="known-issues-for-net-core"></a>Problèmes connus pour .NET Core

| Fonctionnalité | Détails |
| :------ | :------ |
| Importer |  Pour les fichiers .BacPac avec des fichiers compressés d’une taille supérieure à 4 Go, vous devrez peut-être utiliser la version .NET Core de sqlpackage pour effectuer l’importation.  Ce comportement est dû au fait que .NET Core génère des en-têtes zip qui, bien qu’ils soient valides, ne sont pas lisibles par la version .NET Framework complète de sqlpackage. | 
| Déploiement | Le paramètre /p:Storage=File n’est pas pris en charge. Seul Memory est pris en charge sur .NET Core. | 
| Always Encrypted | sqlpackage .NET Core ne prend pas en charge les colonnes Always Encrypted. | 
| Sécurité | sqlpackage .NET Core ne prend pas en charge le paramètre /ua pour l’authentification multifacteur. | 
| Déploiement | Les anciens fichiers .dacpac et .bacpac V2 qui utilisent la sérialisation de données JSON ne sont pas pris en charge. |
| &nbsp; | &nbsp; |

## <a name="1831-sqlpackage"></a>SqlPackage 18.3.1

|Plateforme|Téléchargement|Date de publication|Version|Build
|:---|:---|:---|:---|:---|
| Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2102893)|13 septembre 2019|18.3.1|15.0.4538.1|
|macOS .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102894)|13 septembre 2019| 18.3.1|15.0.4538.1|
|Linux .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102978)|13 septembre 2019| 18.3.1|15.0.4538.1|
|Windows .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2102979)|13 septembre 2019| 18.13.1|15.0.4538.1|

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Déploiement | Ajout de la prise en charge pour le déploiement sur Azure SQL Data Warehouse (préversion). | 
| Déploiement | Ajout du paramètre /p:DatabaseLockTimeout=(INT32 '60') à sqlpackage. | 
| Déploiement | Ajout du paramètre /p:LongRunningCommandTimeout=(INT32) à sqlpackage. |
| Exportation/Extraction | Ajout du paramètre /p:TempDirectoryForTableData=(STRING) à sqlpackage. |
| Déploiement | Autorisation du chargement de contributeurs de déploiement à partir d’emplacements supplémentaires. Les contributeurs de déploiement sont chargés à partir du même répertoire que la cible .dacpac en cours de déploiement, du répertoire des extensions par rapport au fichier binaire sqlpackage.exe, et du paramètre /p:AdditionalDeploymentContributorPaths=(STRING) ajouté à sqlpackage où des emplacements de répertoire supplémentaires peuvent être spécifiés. |
| Déploiement | Ajoute de la prise en charge de OPTIMIZE_FOR_SEQUENTIAL_KEY. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Déploiement | Correction pour ignorer les index automatiques afin qu’ils ne soient pas supprimés lors du déploiement. | 
| Always Encrypted | Correction de la gestion des colonnes varchar Always Encrypted. | 
| Build/Déploiement | Correctif pour résoudre la méthode nodes() pour les jeux de colonnes XML.| 
| ScriptDom | Correction des cas supplémentaires où la chaîne « URL » était interprétée comme un jeton de niveau supérieur. | 
| Graph | Correction du TSQL généré pour les références de pseudo-colonnes dans les contraintes.  | 
| Exporter | Génération de mots de passe aléatoires conformes aux exigences de complexité. | 
| Déploiement | Correctif pour honorer les délais d’attente des commandes lors de la récupération de contraintes. | 
| .NET Core (préversion) | Correction de la journalisation des diagnostics dans un fichier. | 
| .NET Core (préversion) | Utilisation de la diffusion en continu pour exporter des données de table afin de prendre en charge les tables volumineuses. | 
| &nbsp; | &nbsp; |

## <a name="182-sqlpackage"></a>SqlPackage 18.2

|Plateforme|Téléchargement|Date de publication|Version|Build
|:---|:---|:---|:---|:---|
| Windows|[Programme d’installation MSI](https://go.microsoft.com/fwlink/?linkid=2087429)|15 avril 2019|18.2|15.0.4384.2|
|macOS .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2087247)|15 avril 2019 | 18.2 |15.0.4384.2|
|Linux .NET Core (préversion)|[Fichier zip](https://go.microsoft.com/fwlink/?linkid=2087431)|15 avril 2019 | 18.2 |15.0.4384.2|

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Graph | Ajout de la prise en charge des tables de graphe pour les contraintes de bord et les clauses de contrainte de bord. |
| Déploiement | Activation de la règle de validation de modèle afin de prendre en charge 32 colonnes pour les clés d’index avec SQL Server 2016 et les versions ultérieures. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Déploiement | Correction par rétroconception d’une base de données SQL Server 2016 RTM en raison d’un indicateur de requête non pris en charge. |
| Déploiement | Correction de l’ordre de déploiement des instructions AUTO CLOSE ALTER pour qu’elles se produisent avant les instructions CREATE FILEGROUP. |
| ScriptDom | Correction de la régression de l’analyse ScriptDom selon laquelle la chaîne « URL » était interprétée comme un jeton de niveau supérieur. |
| Déploiement | Correction d’une exception de référence Null lors de l’analyse d’une instruction ALTER TABLE ADD INDEX. | 
| Comparaison de schémas | Correction de la comparaison de schéma des colonnes calculées persistantes Nullable qui s’affichent toujours comme différentes.|
| &nbsp; | &nbsp; |

## <a name="181-sqlpackage"></a>SqlPackage 18.1

Date de publication : &nbsp; 1er février 2019  
Build : &nbsp; 15.0.4316.1  
Préversion.

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Déploiement | Ajout de la prise en charge des classements UTF-8. |
| Déploiement | Activation des index columnstore non cluster sur une vue indexée. |
| Plateforme | Déplacement vers .NET Core 2.2. | 
| Comparaison de schémas | Utilisation du stockage sur mémoire pour la comparaison de schémas sur .NET Core. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Performances | Correction des performances afin d’utiliser l’ancien estimateur de cardinalité pour les requêtes de rétroconception. | 
| Performances | Correction d’un problème important de performances de la comparaison de schéma lors de la génération d’un script. | 
| Comparaison de schémas | Correction de la logique de détection de dérive du schéma afin d’ignorer certaines sessions d’événements étendus (XEvent). |
| Graph | Correction de l’ordre d’importation des tables de graphe. | 
| Exporter | Correction de l’exportation de tables externes comportant des autorisations d’objet. |
| &nbsp; | &nbsp; |

### <a name="known-issues"></a>Problèmes connus

Cette version inclut les versions d’évaluation multiplateformes de SqlPackage qui ciblent .NET Core 2.2. SqlPackage peut s’exécuter sur macOS et Linux.

| Problème connu | Détails |
| :---------- | :------ |
| Déploiement | Pour .NET Core, les collaborateurs de build et de déploiement ne sont pas pris en charge. | 
| Déploiement | Pour .NET Core, les anciens fichiers .dacpac et .bacpac qui utilisent la sérialisation de données JSON ne sont pas pris en charge. | 
| Déploiement | Pour .NET Core, il peut arriver que les fichiers .dacpac référencés (par exemple, master.dacpac) ne se résolvent pas en raison de problèmes avec les systèmes de fichiers sensibles à la casse. | Pour contourner le problème, il suffit de mettre en majuscules le nom du fichier de référence (par exemple, MASTER.BACPAC). |
| &nbsp; | &nbsp; |

## <a name="180-sqlpackage"></a>SqlPackage 18.0

Date de publication : &nbsp; 24 octobre 2018  
Build : &nbsp; 15.0.4200.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Déploiement | Ajout de la prise en charge du niveau 150 de compatibilité de base de données. | 
| Déploiement | Ajout de la prise en charge de Managed Instance. | 
| Performances | Ajout du paramètre de ligne de commande MaxParallelism pour spécifier le degré de parallélisme des opérations de base de données. | 
| Sécurité | Ajout du paramètre de ligne de commande AccessToken pour spécifier un jeton d’authentification lors de la connexion à SQL Server. | 
| Importer | Ajout de la prise en charge des flux de types de données BLOB/CLOB pour les importations. | 
| Déploiement | Ajout de la prise en charge de l’option « INLINE » des fonctions UDF scalaires. | 
| Graph | Ajout de la prise en charge de la syntaxe « MERGE » des tables de graphe. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Graph | Correction des pseudo-colonnes non résolues pour les tables de graphe. |
| Déploiement | Correction de la création d’une base de données avec des groupes de fichiers à mémoire optimisée lorsque des tables à mémoire optimisée sont utilisées. |
| Déploiement | Correction de l’intégration de propriétés étendues sur les tables externes. |
| &nbsp; | &nbsp; |

## <a name="178-sqlpackage"></a>SqlPackage 17.8

Date de publication : &nbsp; 22 juin 2018  
Build : &nbsp; 14.0.4079.2

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Diagnostics | Amélioration des messages d’erreur en cas d’échec de connexion, y compris le message d’exception SqlClient. |
| Déploiement | Prise en charge de la compression des index à partition unique pour l’importation/exportation. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Déploiement | Correction d’un problème de rétroconception pour les jeux de colonnes XML avec SQL 2017 et les versions ultérieures. | 
| Déploiement | Correction du problème selon lequel les scripts du niveau de compatibilité de la base de données 140 étaient ignorés pour Azure SQL Database. |
| &nbsp; | &nbsp; |

## <a name="1741-sqlpackage"></a>SqlPackage 17.4.1

Date de publication : &nbsp; 25 janvier 2018  
Build : &nbsp; 14.0.3917.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Importer/Exporter | Ajout du paramètre de ligne de commande ThreadMaxStackSize pour analyser du code Transact-SQL comportant de nombreuses instructions imbriquées. |
| Déploiement | Prise en charge du classement de catalogue de base de données. | 
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Importer | Lors de l’importation d’un .bacpac Azure SQL Database dans une instance locale, correction des erreurs liées au fait que _Les clés principales de base de données sans mot de passe ne sont pas prises en charge dans cette version de SQL Server_. |
| Graph | Correction d’une erreur de pseudo-colonnes non résolue pour les tables de graphe. |
| Comparaison de schémas | Correction de l’authentification SQL pour comparer les schémas. | 
| &nbsp; | &nbsp; |

## <a name="1740-sqlpackage"></a>SqlPackage 17.4.0

Date de publication : &nbsp; 12 décembre 2017  
Build : &nbsp; 14.0.3881.1

### <a name="features"></a>Fonctionnalités

| Fonctionnalité | Détails |
| :------ | :------ |
| Déploiement |  Ajout de la prise en charge de la _stratégie de rétention temporelle_ sur SQL 2017 et versions ultérieures et sur Azure SQL Database. | 
| Diagnostics | Ajout du paramètre de ligne de commande /DiagnosticsFile:"C:\Temp\sqlpackage.log" pour spécifier un chemin de fichier permettant d’enregistrer les informations de diagnostic. | 
| Diagnostics | Ajout du paramètre de ligne de commande /Diagnostics pour consigner les informations de diagnostic dans la console. |
| &nbsp; | &nbsp; |

### <a name="fixes"></a>Correctifs

| Fix | Détails |
| :-- | :------ |
| Déploiement | Suppression du blocage en cas de niveau de compatibilité de base de données non compris. La dernière version de Azure SQL Database ou la dernière plateforme sur site sera présumée. |
| &nbsp; | &nbsp; |
