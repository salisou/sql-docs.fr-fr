---
title: MSSQLSERVER_2508 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2508 (Database Engine error)
ms.assetid: c37d40e5-c665-4d66-a727-5cb845634fcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d59fd7ce3c6de67ed0072d908c4427cc9e2d8957
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "68220235"
---
# <a name="mssqlserver_2508"></a>MSSQLSERVER_2508
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|2508|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBCC_OUT_OF_DATE_PAGE_OR_ROW_COUNT|  
|Texte du message|Le nombre %.*ls pour l’objet « %.\*ls », ID d’index %d, ID de partition %I64d, ID d’unité d’allocation %I64d (type %.\*ls) est incorrect. Exécutez DBCC UPDATEUSAGE.|  
  
## <a name="explanation"></a>Explication  
Dans les versions de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], les valeurs du nombre de lignes de table et d'index et du nombre de pages peuvent être incorrectes. Les bases de données créées avec des versions antérieures à [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] peuvent contenir des nombres incorrects. DBCC CHECKDB a été amélioré pour détecter ces erreurs et retourne ce message d'avertissement lorsque l'erreur se produit.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Exécutez DBCC UPDATEUSAGE sur l'objet ou l'index spécifié ou sur la base de données qui contient l'objet pour corriger les nombres non valides.  
  
