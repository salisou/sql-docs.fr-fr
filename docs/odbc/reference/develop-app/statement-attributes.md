---
title: Attributs d’instruction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], statement attributes
- statement attributes [ODBC]
ms.assetid: 4c59cd8e-a713-4095-9065-20d5bdeafe43
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ec24cc43e8c57e47ddda9f20fac1807f42453e84
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299642"
---
# <a name="statement-attributes"></a>Attributs d'instruction
Les attributs d’instruction sont des caractéristiques de l’instruction. Par exemple, s’il faut utiliser des signets et le type de curseur à utiliser avec le jeu de résultats de l’instruction, il s’agit d’attributs d’instruction.  
  
 Les attributs d’instruction sont définis avec **SQLSetStmtAttr** et leurs paramètres actuels récupérés avec **SQLGetStmtAttr**. Il n’est pas nécessaire qu’une application définisse des attributs d’instruction ; tous les attributs d’instruction ont des valeurs par défaut, dont certains sont spécifiques au pilote.  
  
 Lorsqu’un attribut d’instruction peut être défini, dépend de l’attribut lui-même. Les attributs d’instruction SQL_ATTR_CONCURRENCY, SQL_ATTR_CURSOR_TYPE, SQL_ATTR_SIMULATE_CURSOR et SQL_ATTR_USE_BOOKMARKS doivent être définis avant l’exécution de l’instruction. Les attributs d’instruction SQL_ATTR_ASYNC_ENABLE et SQL_ATTR_NOSCAN peuvent être définis à tout moment, mais ils ne sont pas appliqués tant que l’instruction n’est pas réutilisée. Les attributs d’instruction SQL_ATTR_MAX_LENGTH, SQL_ATTR_MAX_ROWS et SQL_ATTR_QUERY_TIMEOUT peuvent être définis à tout moment, mais ils sont spécifiques au pilote, qu’ils soient appliqués avant que l’instruction soit réutilisée. Les attributs d’instruction restants peuvent être définis à tout moment.  
  
> [!NOTE]  
>  La possibilité de définir des attributs d’instruction au niveau de la connexion en appelant **SQLSetConnectAttr** est dépréciée dans ODBC 3. *x*. ODBC 3. *x* les applications ne doivent jamais définir d’attributs d’instruction au niveau de la connexion. ODBC 3. *x* les pilotes doivent uniquement prendre en charge cette fonctionnalité s’ils devraient fonctionner avec ODBC 2. *x* applications. Pour plus d’informations, consultez le [mappage SQLSetConnectOption](../../../odbc/reference/appendixes/sqlsetconnectoption-mapping.md) dans annexe G : instructions relatives aux pilotes pour la compatibilité descendante.  
>   
>  La SQL_ATTR_METADATA_ID et SQL_ATTR_ASYNC_ENABLE attributs, qui sont des attributs de connexion et des attributs d’instruction, sont une exception et peuvent être définis au niveau de la connexion ou de l’instruction.  
>   
>  Aucun des attributs d’instruction introduits dans ODBC 3. *x* (à l’exception de SQL_ATTR_METADATA_ID) peut être défini au niveau de la connexion.  
  
 Pour plus d’informations, consultez la description de la fonction [SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md) .
