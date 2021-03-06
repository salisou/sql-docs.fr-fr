---
title: Handles d’environnement | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- environment handles [ODBC]
- handles [ODBC], environment
ms.assetid: 917f1b0c-272b-4e37-a1f5-87cd24b9fa21
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b504995e99dfad032598485e370b4d5a6681ae81
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81300439"
---
# <a name="environment-handles"></a>Handles d’environnement
Un *environnement* est un contexte global dans lequel accéder aux données ; les informations de nature globale sont associées à un environnement, par exemple :  
  
-   État de l’environnement  
  
-   Diagnostics au niveau de l’environnement actuel  
  
-   Handles des connexions actuellement allouées sur l’environnement  
  
-   Paramètres actuels de chaque attribut d’environnement  
  
 Dans un morceau de code qui implémente ODBC (gestionnaire de pilotes ou pilote), un descripteur d’environnement identifie une structure qui contient ces informations.  
  
 Les handles d’environnement ne sont pas souvent utilisés dans les applications ODBC. Elles sont toujours utilisées dans les appels à **SQLDataSources** et **SQLDrivers** et parfois utilisées dans les appels à **SQLAllocHandle**, **SQLEndTran**, **SQLFreeHandle**, **SQLGetDiagField**et **SQLGetDiagRec**.  
  
 Chaque morceau de code qui implémente ODBC (le gestionnaire de pilotes ou un pilote) contient un ou plusieurs descripteurs d’environnement. Par exemple, le gestionnaire de pilotes gère un handle d’environnement distinct pour chaque application qui y est connectée. Les handles d’environnement sont alloués avec **SQLAllocHandle** et libérés avec **SQLFreeHandle**.
