---
title: Accéder aux FileTables avec des API d’entrée-sortie de fichier | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: filestream
ms.topic: conceptual
helpviewer_keywords:
- FileTables [SQL Server], accessing files with file APIs
ms.assetid: fa504c5a-f131-4781-9a90-46e6c2de27bb
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: cd43f430f43f31435df6fff71687136f4bd5f9e7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010354"
---
# <a name="access-filetables-with-file-input-output-apis"></a>Accéder aux FileTables avec des API d’entrée-sortie de fichier
  Décrit le fonctionnement des E/S du système de fichiers sur un FileTable.  
  
##  <a name="get-started-using-file-io-apis-with-filetables"></a><a name="accessing"></a> Commencer à utiliser les API d'E/S de fichier avec des FileTables  
 Les FileTables sont principalement utilisés via le système de fichiers Windows et les API d'E/S de fichier. Les FileTables prennent en charge l'accès non transactionnel via le vaste ensemble d'API d'E/S de fichier disponibles.  
  
1.  L'accès aux API d'E/S de fichier commence en général par l'acquisition d'un chemin d'accès UNC logique pour le fichier ou le répertoire. Les applications peuvent utiliser une instruction [!INCLUDE[tsql](../../includes/tsql-md.md)] avec la fonction [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql) pour obtenir le chemin d’accès logique du fichier ou du répertoire. Pour plus d'informations, consultez [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md).  
  
2.  L'application utilise ensuite ce chemin d'accès logique pour obtenir un handle de fichier ou de répertoire et effectuer une action à l'aide de l'objet. Le chemin d'accès peut être passé à toute fonction API du système de fichiers prise en charge, par exemple CreateFile() ou CreateDirectory(), pour créer ou ouvrir un fichier et obtenir un handle. Le handle peut ensuite être utilisé pour créer un flux de données, énumérer ou organiser les répertoires, obtenir ou définir des attributs de fichier, supprimer des fichiers ou des répertoires, etc.  
  
##  <a name="creating-files-and-directories-in-a-filetable"></a><a name="create"></a> Création de fichiers et de répertoires dans un FileTable  
 Il est possible de créer un fichier ou un répertoire dans un FileTable en appelant les API d'E/S de fichier, telles que CreateFile ou CreateDirectory.  
  
-   Tous les indicateurs de création de disposition, les modes de partage et les modes d'accès sont pris en charge. Cela inclut la création, la suppression et la modification sur place de fichiers. Les mises à jour d'espaces de noms de fichier, autrement dit les opérations créer, supprimer, renommer ou déplacer des répertoires, sont également prises en charge.  
  
-   La création d'un fichier ou répertoire correspond à la création d'une ligne dans le FileTable sous-jacent.  
  
-   Pour les fichiers, les données de flux sont stockées dans la colonne **file_stream** , alors que pour les répertoires, cette colonne est Null.  
  
-   Pour les fichiers, la colonne **is_directory** contient la valeur **false**. Pour les répertoires, cette colonne contient la valeur **true**.  
  
-   Le partage et la concurrence d'accès sont appliqués lorsque plusieurs opérations d'E/S de fichier ou opérations [!INCLUDE[tsql](../../includes/tsql-md.md)] simultanées affectent le même fichier ou répertoire dans la hiérarchie.  
  
##  <a name="reading-files-and-directories-in-a-filetable"></a><a name="read"></a> Lecture de fichiers et de répertoires dans un FileTable  
 Une sémantique d'isolation de lecture validée (READ COMMITTED) est appliquée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour toutes les opérations d'accès d'E/S de fichier sur les données de flux et les données d'attribut.  
  
##  <a name="writing-and-updating-files-and-directories-in-a-filetable"></a><a name="write"></a> Écriture et mise à jour de fichiers et de répertoires dans un FileTable  
  
-   Toutes les opérations d'écriture ou de mise à jour d'E/S de fichier sur un FileTable sont non transactionnelles. En d'autres termes, aucune transaction [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est liée à ces opérations et aucune garantie ACID n'est fournie.  
  
-   L'ensemble des mises à jour sur place/accès en continu d'E/S de fichier est pris en charge pour le FileTable.  
  
-   Les mises à jour d’attributs ou de données FILESTREAM via des API d’E/S de fichier se traduisent par des mises à jour des colonnes d’attributs **file_stream** et de fichiers correspondantes dans le FileTable.  
  
##  <a name="deleting-files-and-directories-in-a-filetable"></a><a name="delete"></a> Suppression de fichiers et de répertoires dans un FileTable  
 Toute la sémantique des API d'E/S de fichier Windows est appliquée lorsque vous supprimez un fichier ou un répertoire.  
  
-   La suppression d'un répertoire échoue si le répertoire contient des fichiers ou des sous-répertoires.  
  
-   La suppression d'un fichier ou d'un répertoire entraîne la suppression de la ligne correspondante dans le FileTable. Cela équivaut à supprimer la ligne via une opération [!INCLUDE[tsql](../../includes/tsql-md.md)] .  
  
##  <a name="supported-file-system-operations"></a><a name="supported"></a> Opérations du système de fichiers prises en charge  
 Les FileTables prennent en charge les API de système de fichiers associées aux opérations de système de fichiers suivantes :  
  
-   Gestion de répertoires  
  
-   Gestion des fichiers  
  
 Les FileTables ne prennent pas en charge les opérations suivantes :  
  
-   Gestion des disques  
  
-   Gestion des volumes  
  
-   NTFS transactionnel  
  
##  <a name="additional-considerations-for-file-io-access-to-filetables"></a><a name="considerations"></a> Éléments supplémentaires à prendre en considération pour l'accès d'E/S de fichier aux FileTables  
  
###  <a name="using-virtual-network-names-vnns-with-alwayson-availability-groups"></a><a name="vnn"></a> Utilisation de noms de réseau virtuel (VNN) avec des groupes de disponibilité AlwaysOn  
 Lorsque la base de données qui contient FILESTREAM ou des données FileTable appartient à un groupe de disponibilité AlwaysOn, tous les accès à FILESTREAM ou aux données FileTable via les API du système de fichiers doivent utiliser des VNN à la place des noms d'ordinateur. Pour plus d’informations, consultez [FILESTREAM et FileTable avec groupes de disponibilité Always On & &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/filestream-and-filetable-with-always-on-availability-groups-sql-server.md).  
  
###  <a name="partial-updates"></a><a name="partial"></a> Mises à jour partielles  
 Un descripteur accessible en écriture obtenu pour des données FILESTREAM dans un FileTable à l’aide de la fonction [GetFileNamespacePath &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/getfilenamespacepath-transact-sql) peut être utilisé pour effectuer des mises à jour sur place et partielles du contenu FILESTREAM. Ce comportement contraste avec l’accès FILESTREAM transactionnel effectué via un descripteur obtenu en appelant **OpenSQLFILESTREAM()** et en passant un contexte de transaction explicite.  
  
###  <a name="transactional-semantics"></a><a name="trans"></a> Sémantique transactionnelle  
 Lorsque vous accédez aux fichiers d'un FileTable à l'aide des API d'E/S de fichier, ces opérations ne sont pas associées à des transactions utilisateur. Elles présentent les caractéristiques supplémentaires suivantes :  
  
-   Dans la mesure où l'accès non transactionnel aux données FILESTREAM dans un FileTable n'est pas associé à une transaction, il n'a pas de sémantique d'isolation spécifique. Toutefois [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peut utiliser des transactions internes pour appliquer une sémantique de verrouillage ou de concurrence aux données de FileTable. Toutes les transactions internes de ce type sont effectuées avec une isolation de lecture validée (READ COMMITTED).  
  
-   Il n'existe aucune garantie ACID pour ces opérations non transactionnelles sur des données FILESTREAM. Les garanties de cohérence sont semblables à celles des mises à jour de fichiers effectuées par les applications dans le système de fichiers.  
  
-   Ces modifications ne peuvent pas être restaurées.  
  
 Toutefois, il est également possible d’accéder à la colonne FILESTREAM d’un FileTable à l’aide de l’accès transactionnel FILESTREAM en appelant **OpenSqlFileStream()** . Ce type d'accès peut être entièrement transactionnel et respecte tous les niveaux de cohérences transactionnelles actuellement pris en charge.  
  
###  <a name="concurrency-control"></a><a name="concurrency"></a> Contrôle d'accès concurrentiel  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] applique le contrôle d'accès concurrentiel pour l'accès de FileTable parmi les applications de système de fichiers, ainsi qu'entre applications de système de fichiers et applications [!INCLUDE[tsql](../../includes/tsql-md.md)] . Ce contrôle d'accès concurrentiel s'effectue en prenant des verrous appropriés sur les lignes FileTable.  
  
###  <a name="triggers"></a><a name="triggers"></a> Déclencheurs  
 La création, la modification ou la suppression de fichiers, de répertoires ou de leurs attributs via le système de fichiers se traduit par les opérations d'insertion, de mise à jour ou de suppression correspondantes dans le FileTable. Tous les déclencheurs DML [!INCLUDE[tsql](../../includes/tsql-md.md)] associés sont déclenchés dans le cadre de ces opérations.  
  
##  <a name="file-system-functionality-supported-in-filetables"></a><a name="funclist"></a> Fonctionnalités de système de fichiers prises en charge dans les FileTables  
  
|Fonctionnalité|Prise en charge|Commentaires|  
|----------------|---------------|--------------|  
|**Oplocks**|Oui|La prise en charge du niveau 2, du niveau 1, des oplocks Lot et Filtre est assurée.|  
|**Attributs étendus**|Non||  
|**Points d'analyse**|Non||  
|**ACL persistants**|Non||  
|**Flux nommés**|Non||  
|**Fichiers partiellement alloués**|Oui|Le caractère éparse ne peut être défini que sur les fichiers et affecte le stockage du flux de données. Dans la mesure où les données FILESTREAM sont stockées sur des volumes NTFS, la fonctionnalité FileTable prend en charge les fichiers partiellement alloués en envoyant les demandes au système de fichiers NTFS.|  
|**Compression**|Oui||  
|**Chiffrement**|Oui||  
|**TxF**|Non||  
|**ID de fichier**|Non||  
|**ID d'objet**|Non||  
|**Liens symboliques**|Non||  
|**Liens physiques**|Non||  
|**Noms courts**|Non||  
|**Notifications de modification de répertoire**|Non||  
|**Verrouillage de plage d'octets**|Oui|Les demandes de verrouillage de plage d'octets sont passées au système de fichiers NTFS.|  
|**Fichiers mappés en mémoire**|Non||  
|**Annulation d'entrées/sorties**|Oui||  
|**Sécurité**|Non|La sécurité au niveau du partage Windows et la sécurité au niveau table/colonne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont appliquées.|  
|**Journal USN**|Non|Les modifications de métadonnées apportées aux fichiers et répertoires d'un FileTable sont des opérations DML sur une base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Par conséquent, elles sont journalisées dans le fichier journal de base de données correspondant. En revanche, elles ne sont pas consignées dans le journal USN NTFS (à l'exception des modifications de taille).<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] permettent d'obtenir des informations similaires.|  
  
## <a name="see-also"></a>Voir aussi  
 [Charger des fichiers dans FileTables](load-files-into-filetables.md)   
 [Work with Directories and Paths in FileTables](work-with-directories-and-paths-in-filetables.md)   
 [Accéder aux FileTables avec Transact-SQL](access-filetables-with-transact-sql.md)   
 [DDL, fonctions, procédures stockées et vues FileTable](../views/views.md)  
  
  
