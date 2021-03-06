---
title: Adresse du tampon de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- address of data buffers [ODBC]
- buffers [ODBC], data
- data buffers [ODBC], address
ms.assetid: f2426d68-71bc-4ef7-a5cb-ee9d6c1c9671
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 578e4e37a78818cb640d9f32e2480cec5951df63
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305270"
---
# <a name="data-buffer-address"></a>Adresse du tampon de données
L’application transmet l’adresse de la mémoire tampon de données au pilote dans un argument, souvent nommé *ValuePtr* ou un nom similaire. Par exemple, dans l’appel suivant à **SQLBindCol**, l’application spécifie l’adresse de la variable de *Date* :  
  
```  
SQL_DATE_STRUCT Date;  
SQLINTEGER DateInd;  
SQLBindCol(hstmt, 1, SQL_C_TYPE_DATE, &dsDate, 0, &DateInd);  
```  
  
 Comme mentionné dans la section [allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md) , l’adresse d’une mémoire tampon différée doit rester valide jusqu’à ce que la mémoire tampon soit détachée.  
  
 À moins qu’il ne soit spécifiquement interdit, l’adresse d’un tampon de données peut être un pointeur null. Pour les mémoires tampons utilisées pour envoyer des données au pilote, le pilote ignore les informations normalement contenues dans la mémoire tampon. Pour les mémoires tampons utilisées pour récupérer des données du pilote, le pilote ne retourne pas de valeur. Dans les deux cas, le pilote ignore l’argument de longueur de tampon de données correspondant.
