---
title: MSSQLSERVER_12329 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 12329 (Database Engine error)
ms.assetid: 43f90287-36d5-46c2-ac91-a37202dcf6d3
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1ab8f54e274f92e3ff9a320c57bd91b527d474ed
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62915880"
---
# <a name="mssqlserver_12329"></a>MSSQLSERVER_12329
    
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID de l’événement|12329|  
|Source de l’événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|HK_UNSUPPORTED_NON_LATIN_CODEPAGE|  
|Texte du message|Les types de données char(n) et varchar(n) qui utilisent un classement avec une page de codes différente de 1252 ne sont pas pris en charge par *construction*.|  
  
## <a name="explanation"></a>Explication  
 N'utilisez pas les types de données char(n) et varchar(n) qui utilisent un classement avec une page de codes différente de 1252.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Une situation inattendue pouvant générer cette erreur est :  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = 'us_english')  
```  
  
 Utilisez ceci à la place :  
  
```  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
```  
  
  
