---
title: Suppression de lignes par signet avec SQLBulkOperations | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], SQLBulkOperations
- SQLBulkOperations function [ODBC], deleting rows
- updating data [ODBC], SQLBulkOperations
ms.assetid: 46139ec9-7095-481a-bf45-20200a2fdc03
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6b6a4c1b24ee276c86175392eb45ac5ce0aa45e5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305960"
---
# <a name="deleting-rows-by-bookmark-with-sqlbulkoperations"></a>Suppression de lignes par signet avec SQLBulkOperations
Lors de la suppression d’une ligne par signet, **SQLBulkOperations** permet à la source de données de supprimer une ou plusieurs lignes sélectionnées de la table. Les lignes sont identifiées par le signet dans une colonne de signets liée.  
  
 Pour supprimer des lignes par signet avec **SQLBulkOperations**, l’application effectue les opérations suivantes :  
  
1.  Récupère et met en cache les signets de toutes les lignes à supprimer. Si plusieurs liaisons de signet et de colonne sont utilisées, les signets sont stockés dans un tableau ; s’il y a plus d’un signet et que la liaison selon les lignes est utilisée, les signets sont stockés dans un tableau de structures de lignes.  
  
2.  Définit l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE sur le nombre de signets et lie la mémoire tampon contenant la valeur de signet, ou le tableau de signets, à la colonne 0.  
  
3.  Appelle **SQLBulkOperations** avec l' *opération* définie sur SQL_DELETE_BY_BOOKMARK.
