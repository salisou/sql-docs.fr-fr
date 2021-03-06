---
title: sys. resource_stats (Azure SQL Database) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2018
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- resource_stats
- sys.resource_stats
- sys.resource_stats_TSQL
- resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_stats
- resource_stats
ms.assetid: 02379a1b-3622-4578-8c59-a1b8f1a17914
author: julieMSFT
ms.author: jrasnick
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: e88d3916f5122564b443bc3c439200526b1f2d5e
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75246909"
---
# <a name="sysresource_stats-azure-sql-database"></a>sys.resource_stats (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  Renvoie les données de stockage et l’utilisation d’UC pour une base de données Azure SQL Database. Les données sont collectées et agrégées dans des intervalles de cinq minutes. Pour chaque base de données utilisateur, il existe une ligne pour chaque fenêtre de rapports de cinq minutes dans laquelle il y a une modification de la consommation des ressources. Les données retournées incluent l’utilisation du processeur, la modification de la taille du stockage et la modification des références SKU de base de données. Les bases de données inactives sans modification peuvent ne pas avoir de lignes pour chaque intervalle de cinq minutes. Les données historiques sont conservées pendant environ 14 jours.  
  
 La vue **sys. resource_stats** a des définitions différentes selon la version du serveur Azure SQL Database à laquelle la base de données est associée. Tenez compte de ces différences et des modifications requises par votre application lors de la mise à niveau vers une nouvelle version de serveur.  
  
 Le tableau suivant décrit les colonnes disponibles dans un serveur v12 :  
  
|Colonnes|Type de données|Description|  
|----------------------------|---------------|-----------------|  
|start_time|**datetime**|Heure UTC indiquant le début de l’intervalle de création de rapports de cinq minutes.|  
|end_time|**datetime**|Heure UTC indiquant la fin de l’intervalle de création de rapports de cinq minutes.|  
|database_name|**nvarchar(128)**|Nom de la base de données utilisateur.|  
|sku|**nvarchar(128)**|Niveau de service de la base de données. Les valeurs possibles sont les suivantes :<br /><br /> De base<br /><br /> standard<br /><br /> Premium<br /><br />Usage général<br /><br />Critique pour l’entreprise|  
|storage_in_megabytes|**float**|Taille de stockage maximale en mégaoctets pour la période, y compris les données, les index, les procédures stockées et les métadonnées de la base de données.|  
|avg_cpu_percent|**décimal (5, 2)**|Utilisation moyenne du calcul en pourcentage de la limite de la couche de service.|  
|avg_data_io_percent|**décimal (5, 2)**|Utilisation moyenne des E-S en pourcentage en fonction de la limite du niveau de service. Pour les bases de données Hyperscale, consultez [e/s de données dans statistiques d’utilisation des ressources](https://docs.microsoft.com/azure/sql-database/sql-database-hyperscale-performance-diagnostics#data-io-in-resource-utilization-statistics).|  
|avg_log_write_percent|**décimal (5, 2)**|Utilisation moyenne de la ressource d'écriture en pourcentage de la limite de la couche de service.|  
|max_worker_percent|**décimal (5, 2)**|Nombre maximal de threads de travail simultanés (demandes) en pourcentage en fonction de la limite du niveau de service de la base de données.<br /><br /> Le nombre maximal est actuellement calculé pour l’intervalle de cinq minutes en fonction des exemples de 15 secondes de nombres de Worker simultanés.|  
|max_session_percent|**décimal (5, 2)**|Nombre maximal de sessions simultanées en pourcentage en fonction de la limite du niveau de service de la base de données.<br /><br /> Le maximum est actuellement calculé pour l’intervalle de cinq minutes en fonction des exemples de 15 secondes de nombres de sessions simultanées.|  
|dtu_limit|**int**|Paramètre DTU maximal de la base de données actuelle pour cette base de données au cours de cet intervalle. |
|xtp_storage_percent|**décimal (5, 2)**|Utilisation du stockage pour l’OLTP en mémoire en pourcentage de la limite du niveau de service (à la fin de l’intervalle de création de rapports). Cela comprend la mémoire utilisée pour le stockage des objets OLTP en mémoire suivants : les tables optimisées en mémoire, les index et les variables de table. Il comprend également la mémoire utilisée pour le traitement des opérations ALTER TABLE.<br /><br /> Retourne 0 si l’OLTP en mémoire n’est pas utilisé dans la base de données.|
|avg_login_rate_percent|**décimal (5, 2)**|Identifié à titre d'information uniquement. Non pris en charge. La compatibilité future n'est pas garantie.|
|avg_instance_cpu_percent|**décimal (5, 2)**|Utilisation moyenne du processeur de base de données en pourcentage du processus de base de données SQL.|
|avg_instance_memory_percent|**décimal (5, 2)**|Utilisation moyenne de la mémoire de la base de données en pourcentage du processus de base de données SQL.|
|cpu_limit|**décimal (5, 2)**|Nombre de vCores pour cette base de données au cours de cet intervalle. Pour les bases de données utilisant le modèle basé sur DTU, cette colonne a la valeur NULL.|
|allocated_storage_in_megabytes|**float**|Quantité d’espace de fichier mise en forme, en Mo, disponible pour le stockage des données de la base de données. L’espace de fichier formaté est également appelé espace de données alloué.  Pour plus d’informations, consultez [gestion de l’espace de fichiers dans la base de données SQL](https://docs.microsoft.com/azure/sql-database/sql-database-file-space-management) .|
  
> [!TIP]  
>  Pour plus d’informations sur ces limites et les niveaux de service, consultez les rubriques [niveaux de service](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/).  
    
## <a name="permissions"></a>Autorisations  
 Cette vue est disponible pour tous les rôles d’utilisateur disposant d’autorisations pour se connecter à la base de données **Master** virtuelle.  
  
## <a name="remarks"></a>Notes  
 Les données retournées par **sys. resource_stats** sont exprimées sous la forme d’un pourcentage des limites maximales autorisées pour le niveau de service/niveau de performances que vous exécutez.  
  
 Lorsqu’une base de données est membre d’un pool élastique, les statistiques de ressources présentées sous forme de pourcentages sont exprimées en pourcentage de la limite maximale pour les bases de données définies dans la configuration du pool élastique.  
  
 Pour obtenir une vue plus granulaire de ces données, utilisez la vue de gestion dynamique **sys. dm_db_resource_stats** dans une base de données utilisateur. Cette vue capture des données toutes les 15 secondes et conserve 1 heure d'historique des données.  Pour plus d’informations, consultez [sys. dm_db_resource_stats &#40;Azure SQL Database&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-resource-stats-azure-sql-database.md).  

## <a name="examples"></a>Exemples  
 L'exemple suivant retourne toutes les bases de données dont la moyenne s'établit à au moins 80 % de l'utilisation du calcul au cours de la dernière semaine.  
  
```sql  
DECLARE @s datetime;  
DECLARE @e datetime;  
SET @s= DateAdd(d,-7,GetUTCDate());  
SET @e= GETUTCDATE();  
SELECT database_name, AVG(avg_cpu_percent) AS Average_Compute_Utilization   
FROM sys.resource_stats   
WHERE start_time BETWEEN @s AND @e  
GROUP BY database_name  
HAVING AVG(avg_cpu_percent) >= 80  
```  
    
## <a name="see-also"></a>Voir aussi  
 [Niveaux de service](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [Capacités et limites des niveaux de service](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
