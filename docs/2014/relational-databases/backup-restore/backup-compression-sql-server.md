---
title: Compression des sauvegardes (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], backup compression
- backup compression [SQL Server], about backup compression
- compression [SQL Server], backup compression
- backups [SQL Server], compression
- backing up [SQL Server], backup compression
- backup compression [SQL Server]
ms.assetid: 05bc9c4f-3947-4dd4-b823-db77519bd4d2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: af3e8d9184b12a726361643c563402242c6b04cd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62876783"
---
# <a name="backup-compression-sql-server"></a>Compression de sauvegardes (SQL Server)
  Cette rubrique décrit la compression des sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , notamment les restrictions, les compromis en termes de performances pour la compression des sauvegardes, la configuration pour la compression des sauvegardes et le taux de compression.  
  
> [!NOTE]  
>  Pour plus d’informations sur [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] les éditions de qui prennent en charge la compression de sauvegarde, consultez [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md). Chaque édition de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] et ultérieure peut restaurer une sauvegarde compressée.  
  
  
##  <a name="benefits"></a><a name="Benefits"></a> Avantages  
  
-   Une sauvegarde compressée étant plus petite qu'une sauvegarde non compressée des mêmes données, la compression d'une sauvegarde requiert en général moins d'E/S de périphérique et, par conséquent, augmente souvent considérablement la vitesse de la sauvegarde.  
  
     Pour plus d'informations, consultez [Impact sur les performances de la compression des sauvegardes](#PerfImpact), plus loin dans cette rubrique.  
  
  
##  <a name="restrictions"></a><a name="Restrictions"></a> Restrictions  
 Les restrictions suivantes s'appliquent aux sauvegardes compressées :  
  
-   Les sauvegardes compressées et non compressées ne peuvent pas co-exister dans un support de sauvegardes.  
  
-   Toutefois, les versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peuvent pas lire les sauvegardes compressées.  
  
-   NTbackups ne peut pas partager de bande avec les sauvegardes [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] compressées.  
  
  
##  <a name="performance-impact-of-compressing-backups"></a><a name="PerfImpact"></a> Impact sur les performances de la compression des sauvegardes  
 Par défaut, la compression augmente considérablement l'utilisation de l'UC et l'UC supplémentaire consommée par le processus de compression peut avoir un impact néfaste sur les opérations simultanées. Ainsi, dans une session où l’utilisation de l’UC est limitée, il peut être préférable de créer une sauvegarde compressée de priorité basse à l’aide de[Resource Governor](../resource-governor/resource-governor.md). Pour plus d'informations, consultez [Utiliser Resource Governor pour limiter l’utilisation de l’UC par compression de la sauvegarde &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).  
  
 Pour obtenir une bonne image de vos performances d'E/S de sauvegarde, vous pouvez isoler l'E/S de sauvegarde en direction ou depuis des unités en évaluant les types suivants de compteurs de performance :  
  
-   Compteurs de performance d'E/S Windows, tels que les compteurs de disque physique  
  
-   Compteur **Débit d’unité en octets/s** de l’objet [SQLServer:Backup Device](../performance-monitor/sql-server-backup-device-object.md)  
  
-   Compteur **Débit de sauvegarde/restauration/s** de l’objet [SQLServer:Databases](../performance-monitor/sql-server-databases-object.md)  
  
 Pour des informations sur les compteurs Windows, consultez l'aide de Windows. Pour obtenir des informations sur l’utilisation des compteurs SQL Server, consultez [Utiliser des objets SQL Server](../performance-monitor/use-sql-server-objects.md).  
  
  
##  <a name="calculate-the-compression-ratio-of-a-compressed-backup"></a><a name="CompressionRatio"></a> Calculer le taux de compression d'une sauvegarde compressée  
 Pour calculer le taux de compression d’une sauvegarde, utilisez les valeurs pour la sauvegarde dans les colonnes **backup_size** et **compressed_backup_size** de la table de l’historique [backupset](/sql/relational-databases/system-tables/backupset-transact-sql) , comme suit :  
  
 **backup_size**:**compressed_backup_size**  
  
 Par exemple, un taux de compression 3:1 indique que vous économisez environ 66 % de l'espace disque. Pour effectuer une requête sur ces colonnes, vous pouvez utiliser l'instruction Transact-SQL suivante :  
  
```  
SELECT backup_size/compressed_backup_size FROM msdb..backupset;  
```  
  
 Le taux de compression d'une sauvegarde compressée dépend des données compressées. Divers facteurs peuvent avoir une incidence sur le taux de compression obtenu. Les facteurs majeurs sont :  
  
-   Le type des données.  
  
     Les données caractères se compressent plus que d'autres types de données.  
  
-   La cohérence des données dans les lignes sur une page.  
  
     En général, si une page contient plusieurs lignes dans lesquelles un champ contient la même valeur, une compression importante peut se produire pour cette valeur. En revanche, pour une base de données qui contient des données aléatoires ou qui contient une seule grande ligne par page, une sauvegarde compressée serait presque aussi importante qu'une sauvegarde non compressée.  
  
-   Si les données sont chiffrées.  
  
     Le taux de compression des données chiffrées est beaucoup moins élevé que celui des données non chiffrées correspondantes. Si le chiffrement transparent des données est utilisé pour chiffrer une base de données entière, la compression des sauvegardes ne réduit pas leur taille de manière significative, voire pas du tout.  
  
-   Si la base de données est compressée.  
  
     Si la base de données est compressée, compresser des sauvegardes peut réduire faiblement leur taille, voire pas du tout.  
  
  
##  <a name="allocation-of-space-for-the-backup-file"></a><a name="Allocation"></a> Allocation d'espace pour le fichier de sauvegarde  
 Pour les sauvegardes compressées, la taille du fichier de sauvegarde final dépend de la capacité de compression des données. Or, celle-ci n'est pas connue avant la fin de l'opération de sauvegarde.  Par conséquent, par défaut, lors de la sauvegarde d'une base de données faisant appel à la compression, le moteur de base de données utilise un algorithme de préallocation pour le fichier de sauvegarde. Cette algorithme préalloue un pourcentage prédéfini de la taille de la base de données pour le fichier de sauvegarde. Si davantage d'espace est requis au cours de l'opération de sauvegarde, le moteur de base de données augmente la taille du fichier. Si la taille finale est inférieure à l'espace alloué, à la fin de l'opération de sauvegarde, le moteur de base de données réduit le fichier à la taille finale réelle de la sauvegarde.  
  
 Pour permettre au fichier de sauvegarde de croître autant que nécessaire uniquement afin d'atteindre sa taille définitive, utilisez l'indicateur de trace 3042. L'indicateur de trace 3042 permet à l'opération de sauvegarde de contourner l'algorithme de préallocation de la compression de sauvegarde par défaut. Cet indicateur de trace est utile si vous devez économiser de l'espace en allouant uniquement la taille réelle requise pour la sauvegarde compressée. Toutefois, le recours à cet indicateur de trace peut entraîner une légère baisse des performances (augmentation possible de la durée de l'opération de sauvegarde).  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> Tâches associées  
  
-   [Configurer la compression de sauvegarde &#40;SQL Server&#41;](backup-compression-sql-server.md)  
  
-   [Afficher ou configurer la compression par défaut des sauvegardes (option de configuration de serveur)](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)  
  
-   [Utiliser Resource Governor pour limiter l’utilisation de l’UC par compression de la sauvegarde &#40;Transact-SQL&#41;](use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)  
  
-   [DBCC TRACEON &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-transact-sql)  
  
-   [DBCC TRACEOFF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceoff-transact-sql)  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de la sauvegarde &#40;SQL Server&#41;](backup-overview-sql-server.md)   
 [Indicateurs de trace &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)  
  
  
