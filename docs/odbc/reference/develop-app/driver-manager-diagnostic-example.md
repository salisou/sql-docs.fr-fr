---
title: Exemple de diagnostic du gestionnaire de pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver manager [ODBC], diagnostic messages
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: af8f2d35-d1bf-495c-af25-630654542b7d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 839095e5544cab73cdddd4f4b17a3d8d52136c9c
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305810"
---
# <a name="driver-manager-diagnostic-example"></a>Exemple de diagnostic du gestionnaire de pilotes
Le gestionnaire de pilotes peut également générer des messages de diagnostic. Par exemple, si une application a passé une option direction non valide à **SQLDataSources**, le gestionnaire de pilotes peut formater et retourner les valeurs suivantes à partir de **SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY103"  
Native Error:      0  
Diagnostic Msg:   "[Microsoft][ODBC Driver Manager]Direction option out of range"  
```  
  
 Étant donné que l’erreur s’est produite dans le gestionnaire de pilotes, elle a ajouté des préfixes au message de diagnostic pour son fournisseur ([Microsoft]) et son identificateur ([gestionnaire de pilotes ODBC]).
