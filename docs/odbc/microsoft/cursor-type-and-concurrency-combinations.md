---
title: Type de curseur et combinaisons d’accès concurrentiel | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], concurrency options
- cursors [ODBC], ODBC driver for Oracle
- concurrency options [ODBC]
- ODBC driver for Oracle [ODBC], cursor options
ms.assetid: db63d610-f86f-4029-9d66-fed616c8a818
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b6397b5d675546bf41102f037b68c0022bec74df
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280769"
---
# <a name="cursor-type-and-concurrency-combinations"></a>Combinaisons des types de curseurs et des accès concurrentiels
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Les types de curseur contrôlent les fonctionnalités du curseur fourni à l’utilisateur. Les options de concurrence contrôlent le comportement de mise à jour et de verrouillage d’un jeu de résultats.  
  
|Type de curseur|Concurrence (valeurs autorisées)|  
|-----------------|------------------------------------|  
|SQL_CURSOR_FORWARD_ONLY|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_STATIC|SQL_CONCUR_READ_ONLY|  
|SQL_CURSOR_KEYSET_DRIVEN<sup>[1]</sup>|SQL_CONCUR_READ_ONLY SQL_CONCUR_LOCK<sup>[2]</sup> SQL_CONCUR_VALUES|  
  
 <sup>[1]</sup> consultez [limitations de l’utilisation de curseurs de jeu de clés](../../odbc/microsoft/limitations-of-using-keyset-driven-cursors.md).  
  
 <sup>[2]</sup> SQL_CONCUR_LOCK est pris en charge uniquement lorsque l’option de connexion SQL_AUTOCOMMIT est définie sur SQL_AUTOCOMMIT_OFF.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de connexion](../../odbc/microsoft/connect-options.md)
