---
title: SQL_NO_DATA | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL_NO_DATA [ODBC]
- application upgrades [ODBC], SQL_NO_DATA
- backward compatibility [ODBC], SQL_NO_DATA
- compatibility [ODBC], SQL_NO_DATA
- upgrading applications [ODBC], SQL_NO_DATA
ms.assetid: 07a4144a-a548-4578-b2be-715c3cf73bf8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9a399a270eb1cd2f3daf9449c53b1f577a6b9545
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299789"
---
# <a name="sql_no_data"></a>SQL_NO_DATA
Quand ODBC 3. l’application *x* appelle **SQLExecDirect**, **SQLExecute**ou **SQLParamData** dans ODBC 2. *x* pour exécuter une instruction UPDATE ou DELETE recherchée qui n’affecte aucune ligne de la source de données, le pilote doit retourner SQL_SUCCESS, et non SQL_NO_DATA. Quand ODBC 2. *x* ou ODBC 3. *x* qui fonctionne avec une application ODBC 3. le pilote *x* appelle **SQLExecDirect**, **SQLExecute**ou **SQLParamData** avec le même résultat, ODBC 3. le pilote *x* doit retourner SQL_NO_DATA.
