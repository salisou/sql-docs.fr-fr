---
title: Fonctions ODBC non exécutées par la bibliothèque de curseurs | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- cursor library [ODBC], functions
- functions [ODBC], cursor library
- ODBC functions [ODBC], cursor library
- ODBC cursor library [ODBC], functions
ms.assetid: f2941522-75eb-4db9-9468-4800b884dac2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ff9d685cf4a509b84142d91f76d41eb7ca3508ee
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81308040"
---
# <a name="odbc-functions-not-executed-by-the-cursor-library"></a>Fonctions ODBC non exécutées par la bibliothèque de curseurs
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d’utiliser cette fonctionnalité dans de nouveaux travaux de développement et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Microsoft recommande l’utilisation de la fonctionnalité de curseur du pilote.  
  
 La bibliothèque de curseurs n’exécute pas les fonctions suivantes. Quand une application appelle l’une de ces fonctions, le gestionnaire de pilotes appelle le pilote, pas la bibliothèque de curseurs.  
  
|||  
|-|-|  
|**SQLFetch**|**SQLGetEnvAttr**|  
|**SQLGetConnectAttr**|**SQLSetDescRec**|  
|**SQLGetDiagField**|**SQLSetEnvAttr**|  
|**SQLGetDiagRec**||
