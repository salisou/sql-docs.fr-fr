---
title: Filtrer une trace | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- filters [SQL Server], events
- events [SQL Server], filters
- filters [SQL Server]
- filters [SQL Server], traces
- traces [SQL Server], filters
ms.assetid: 019c10ab-68f6-4e40-a5e8-735b2e1270db
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 381007cb26f74cdf945900436d8a9fcea5a4ef39
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62714716"
---
# <a name="filter-a-trace"></a>Filtrer une trace
  Les filtres limitent les événements recueillis dans une trace. Si aucun filtre n'est défini, tous les événements des classes d'événements sélectionnées sont retournés dans le résultat de trace. Par exemple, limiter les noms d'utilisateurs Windows d'une trace à des utilisateurs particuliers réduit le volume des données de sortie à ces seuls utilisateurs.  
  
 Il n'est pas obligatoire de définir un filtre pour une trace. Cependant, un filtre minimise la charge générée au cours d'une trace. Un filtre retourne des données ciblées et permet ainsi de faciliter les analyses de performance et les audits.  
  
 Pour filtrer les données relatives aux événements capturés au sein d'une trace, sélectionnez les critères d'événements de trace qui ne retournent que des données pertinentes à partir de la trace. Ainsi, vous pouvez inclure ou exclure de la trace l'analyse de l'activité d'une application particulière.  
  
> [!NOTE]  
>  Lorsque le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] crée des traces, il exclut sa propre activité par défaut.  
  
 À titre d'exemple supplémentaire, lorsque vous surveillez des requêtes pour déterminer les traitements les plus longs à exécuter, vous pouvez définir les critères d'événements de trace pour surveiller (analyser) uniquement les traitements dont l'exécution prend plus de 30 secondes (valeur minimale de l'UC de 30 000 millisecondes).  
  
## <a name="filter-creation-guidelines"></a>Instructions de création de filtres  
 En général, suivez ces étapes pour filtrer une trace.  
  
1.  Identifiez les événements que vous voulez inclure dans la trace.  
  
2.  Identifiez les données et les colonnes des données qui contiennent les informations dont vous avez besoin.  
  
3.  Identifiez un sous-ensemble des données dont vous avez besoin et définissez des filtres en fonction de ce sous-ensemble.  
  
 Par exemple, vous pouvez être intéressé uniquement par les événements qui durent plus longtemps qu'une certaine période de temps. Vous pouvez créer une trace qui inclut les événements pour lesquels les données de la colonne **Durée** sont supérieures à 300 millisecondes. Votre trace n'inclura pas les événements qui se terminent en moins de 300 millisecondes.  
  
 Vous pouvez créer des filtres en utilisant le Générateur de profils SQL Server Profiler ou des procédures stockées Transact-SQL.  
  
 **Pour filtrer des événements dans un modèle de trace**  
  
 [Filtrer des événements dans une trace &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/filter-events-in-a-trace-sql-server-profiler.md)  
  
 [Définir un filtre de trace &#40;Transact-SQL&#41;](../../ssms/agent/set-sql-server-alias-for-sql-server-agent-service-ssms.md)  
  
 **Pour modifier des filtres**  
  
 [Modifier un filtre &#40;SQL Server Profiler&#41;](../../tools/sql-server-profiler/modify-a-filter-sql-server-profiler.md)  
  
 La disponibilité du filtre dépend de la colonne de données. Certaines colonnes de données ne peuvent être filtrées. Les colonnes de données qui peuvent être filtrées ne peuvent l'être qu'en fonction de certains opérateurs relationnels, comme spécifié dans le tableau suivant.  
  
|Opérateur relationnel|Symbole d'opérateur|Description|  
|-------------------------|---------------------|-----------------|  
|Correspond à|LIKE|Indique que les données d'événements de trace doivent correspondre au texte entré. Autorise plusieurs valeurs.|  
|Ne correspond pas à|Ne correspond pas à|Indique que les données d'événements de trace ne doivent pas correspondre au texte entré. Autorise plusieurs valeurs.|  
|Égal à|=|Indique que les données d'événements de trace doivent être égales à la valeur entrée. Autorise plusieurs valeurs.|  
|Différent de|<>|Indique que les données d'événements de trace ne doivent pas être égales à la valeur entrée. Autorise plusieurs valeurs.|  
|Supérieur à|>|Indique que les données d'événements de trace doivent être supérieures à la valeur entrée.|  
|Supérieur ou égal à|>=|Indique que les données d'événements de trace doivent être supérieures ou égales à la valeur entrée.|  
|Inférieur à|<|Indique que les données d'événements de trace doivent être inférieures à la valeur entrée.|  
|Inférieur ou égal à|<=|Indique que les données d'événements de trace doivent être inférieures ou égales à la valeur entrée.|  
  
 Le tableau suivant liste les colonnes de données filtrables, ainsi que les opérateurs relationnels disponibles.  
  
|Colonnes de données|Opérateurs relationnels|  
|------------------|--------------------------|  
|**ApplicationName**|LIKE, NOT LIKE|  
|**BigintData1**|=, <>, >=, <=|  
|**BigintData2**|=, <>, >=, <=|  
|**BinaryData**|Utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour filtrer les événements de cette colonne de données. Pour plus d’informations, consultez [Filtrer des traces avec SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**ClientProcessID**|=, <>, >=, <=|  
|**ColumnPermissions**|=, <>, >=, <=|  
|**UC**|=, <>, >=, <=|  
|**DatabaseID**|=, <>, >=, <=|  
|**DatabaseName**|LIKE, NOT LIKE|  
|**DBUserName**|LIKE, NOT LIKE|  
|**Durée**|=, <>, >=, \<=|  
|**EndTime**|>=, <=|  
|**Error**|=, <>, >=, <=|  
|**EventSubClass**|=, <>, >=, <=|  
|**FileName**|LIKE, NOT LIKE|  
|**GUID**|Utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour filtrer les événements de cette colonne de données. Pour plus d’informations, consultez [Filtrer des traces avec SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**Handle**|=, <>, >=, <=|  
|**HostName**|LIKE, NOT LIKE|  
|**IndexID**|=, <>, >=, <=|  
|**IntegerData**|=, <>, >=, <=|  
|**IntegerData2**|=, <>, >=, <=|  
|**IsSystem**|=, <>, >=, <=|  
|**LineNumber**|=, <>, >=, <=|  
|**LinkedServerName**|LIKE, NOT LIKE|  
|**LoginName**|LIKE, NOT LIKE|  
|**LoginSid**|Utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour filtrer les événements de cette colonne de données. Pour plus d’informations, consultez [Filtrer des traces avec SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**MethodName**|LIKE, NOT LIKE|  
|**Mode**|=, <>, >=, <=|  
|**NestLevel**|=, <>, >=, <=|  
|**NTDomainName**|LIKE, NOT LIKE|  
|**NTUserName**|LIKE, NOT LIKE|  
|**ObjectID**|=, <>, >=, <=|  
|**ObjectID2**|=, <>, >=, <=|  
|**ObjectName**|LIKE, NOT LIKE|  
|**ObjectType**|=, <>, >=, <=|  
|**Offset**|=, <>, >=, <=|  
|**OwnerID**|=, <>, >=, <=|  
|**OwnerName**|LIKE, NOT LIKE|  
|**ParentName**|LIKE, NOT LIKE|  
|**Autorisations**|=, <>, >=, <=|  
|**ProviderName**|LIKE, NOT LIKE|  
|**Reads**|=, <>, >=, <=|  
|**RequestID**|=, <>, >=, <=|  
|**RoleName**|LIKE, NOT LIKE|  
|**RowCounts**|=, <>, >=, <=|  
|**SessionLoginName**|LIKE, NOT LIKE|  
|**Niveau de gravité**|=, <>, >=, <=|  
|**SourceDatabaseID**|=, <>, >=, <=|  
|**SPID**|=, <>, >=, \<=|  
|**SqlHandle**|Utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour filtrer les événements de cette colonne de données. Pour plus d’informations, consultez [Filtrer des traces avec SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**StartTime**|>=, <=|  
|**State**|=, <>, >=, <=|  
|**Success**|=, <>, >=, <=|  
|**TargetLoginName**|LIKE, NOT LIKE|  
|**TargetLoginSid**|Utilisez le [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] pour filtrer les événements de cette colonne de données. Pour plus d’informations, consultez [Filtrer des traces avec SQL Server Profiler](../../tools/sql-server-profiler/filter-traces-with-sql-server-profiler.md).|  
|**TargetUserName**|LIKE, NOT LIKE|  
|**TextData** <sup>1</sup>|LIKE, NOT LIKE|  
|**TransactionID**|=, <>, >=, <=|  
|**Type**|=, <>, >=, <=|  
|**Writes**|=, <>, >=, <=|  
|**XactSequence**|=, <>, >=, <=|  
  
 <sup>1</sup> si vous tracez des événements à partir de l’utilitaire **osql** ou de **%** l’utilitaire **sqlcmd** , ajoutez toujours aux filtres sur la colonne de données **TextData** .  
  
 En tant que mécanisme de sécurité, le Générateur de profils SQL omet automatiquement de la trace les procédures stockées de sécurité qui affectent les mots de passe. Ce mécanisme de sécurité n'est pas configurable et est toujours actif. Il empêche les utilisateurs, qui par ailleurs ont l'autorisation de tracer l'ensemble de l'activité de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], d'intercepter les mots de passe.  
  
 Les procédures stockées de sécurité suivantes sont surveillées, mais aucune donnée de sortie n’est écrite dans la colonne de données **TextData** :  
  
 [sp_addapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addapprole-transact-sql)  
  
 [sp_adddistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql)  
  
 [sp_adddistributiondb &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributiondb-transact-sql)  
  
 [sp_adddistributor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-adddistributor-transact-sql)  
  
 [sp_addlinkedserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql)  
  
 [sp_addlinkedsrvlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlinkedsrvlogin-transact-sql)  
  
 [sp_addlogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addlogin-transact-sql)  
  
 [sp_addmergepullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql)  
  
 [sp_addpullsubscription_agent &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql)  
  
 [sp_addremotelogin &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addremotelogin-transact-sql)  
  
 [sp_addsubscriber &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql)  
  
 [sp_approlepassword &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-approlepassword-transact-sql)  
  
 [sp_changedistpublisher &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changedistpublisher-transact-sql)  
  
 [sp_changesubscriber &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql)  
  
 [sp_dsninfo &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dsninfo-transact-sql)  
  
 [sp_helpsubscription_properties &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpsubscription-properties-transact-sql)  
  
 [sp_link_publication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-link-publication-transact-sql)  
  
 [sp_password &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-password-transact-sql)  
  
 [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql)  
  
  
