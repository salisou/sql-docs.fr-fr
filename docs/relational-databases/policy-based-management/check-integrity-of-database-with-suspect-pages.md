---
title: Vérifier l’intégrité d’une base de données contenant des pages suspectes | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: security
ms.topic: conceptual
helpviewer_keywords:
- Best Practices [Database Engine]
ms.assetid: 3b1ec9fe-f6c5-46f7-aa63-6e671be1572d
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f0be2586d83aaf859ba6b5f4b57f08a4d679b9be
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68109883"
---
# <a name="check-integrity-of-database-with-suspect-pages"></a>Vérifier l'intégrité d'une base de données contenant des pages suspectes
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Cette règle recherche les bases de données utilisateur dont l'état de base de données a la valeur suspect. Lorsque le [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] lit une page de la base de données contenant une erreur 824, cette page est jugée suspecte, son ID est enregistré dans la table suspect_pages dans msdb et la base de données contenant cette page prend la valeur suspecte.  
  
 L'erreur 824 indique qu'une erreur de cohérence logique a été détectée au cours d'une opération de lecture. Cette erreur indique généralement que des données ont été endommagées par un composant défectueux du sous-système d'E/S. Il s'agit d'une condition d'erreur grave qui menace l'intégrité de la base de données et qui doit être immédiatement corrigée.  
  
## <a name="best-practices-recommendations"></a>Meilleures pratiques recommandées  
  
-   Examinez les détails de l'erreur 824 pour cette base de données dans le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Effectuez une vérification complète de la cohérence de la base de données ([DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)).  
  
-   Implémentez les actions utilisateur définies dans [MSSQLSERVER_824](https://go.microsoft.com/fwlink/?LinkId=81397).  
  
## <a name="for-more-information"></a>Pour plus d'informations  
 [Gérer la table suspect_pages &#40;SQL Server&#41;](../../relational-databases/backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
