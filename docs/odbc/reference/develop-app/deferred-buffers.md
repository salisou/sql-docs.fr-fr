---
title: Mémoires tampons différées | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- buffers [ODBC], deferred
- deferred buffers [ODBC]
ms.assetid: 02c9a75c-2103-4f68-a1db-e31f7e0f1f03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f34c6d3d886a0a75c309dc4f5c71f5c7ba3df447
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305980"
---
# <a name="deferred-buffers"></a>Mémoires tampons différées
Une *mémoire tampon différée* est une mémoire dont la valeur est utilisée à un moment donné *après* qu’elle a été spécifiée dans un appel de fonction. Par exemple, **SQLBindParameter** est utilisé pour associer ou *lier* un tampon de données à un paramètre dans une instruction SQL. L’application spécifie le numéro du paramètre et passe l’adresse, la longueur en octets et le type de la mémoire tampon. Le pilote enregistre ces informations, mais n’examine pas le contenu de la mémoire tampon. Plus tard, lorsque l’application exécute l’instruction, le pilote récupère les informations et les utilise pour récupérer les données de paramètre et les envoyer à la source de données. Par conséquent, l’entrée des données dans la mémoire tampon est différée. Étant donné que les tampons différés sont spécifiés dans une fonction et utilisés dans une autre, il s’agit d’une erreur de programmation d’application pour libérer une mémoire tampon différée alors que le pilote s’attend à ce qu’elle existe toujours. Pour plus d’informations, consultez [allocation et libération de mémoires tampons](../../../odbc/reference/develop-app/allocating-and-freeing-buffers.md), plus loin dans cette section.  
  
 Les mémoires tampons d’entrée et de sortie peuvent être différées. Le tableau suivant récapitule les utilisations des mémoires tampons différées. Notez que les tampons différés liés aux colonnes de jeu de résultats sont spécifiés avec **SQLBindCol**et que les mémoires tampons différées liées aux paramètres d’instruction SQL sont spécifiées avec **SQLBindParameter**.  
  
|Utilisation de la mémoire tampon|Type|Spécifié avec|Utilisée par|  
|----------------|----------|--------------------|-------------|  
|Envoi de données pour les paramètres d’entrée|Entrée différée|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Envoi de données pour mettre à jour ou insérer une ligne dans un jeu de résultats|Entrée différée|**SQLBindCol**|**SQLSetPos**|  
|Retour de données pour les paramètres de sortie et d’entrée/sortie|Sortie différée|**SQLBindParameter**|**SQLExecute**<br /> **SQLExecDirect**|  
|Renvoi des données du jeu de résultats|Sortie différée|**SQLBindCol**|**SQLFetch**<br /> **SQLFetchScroll SQLSetPos**|
