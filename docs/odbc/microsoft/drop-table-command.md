---
title: DROP TABLE, commande | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drop table command [ODBC]
ms.assetid: bc50459b-8861-4889-84a9-129ae9065aa8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 779c519f720027aea3a6f6cf2587d3c6e0b59b52
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81303420"
---
# <a name="drop-table-command"></a>DROP TABLE, commande
Supprime une table de la base de données spécifiée avec la source de données et la supprime du disque.  
  
 Le pilote ODBC Visual FoxPro prend en charge la syntaxe du langage Visual FoxPro natif pour cette commande. Pour obtenir des informations spécifiques au pilote, consultez les notes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
DROP TABLE TableName | FileName | ?  
```  
  
## <a name="settings"></a>Paramètres  
 *TableName*  
 Spécifie la table à supprimer de la base de données spécifiée avec la source de données et à supprimer du disque.  
  
 *FileName*  
 Spécifie une table libre à supprimer du disque.  
  
 ?  
 Affiche la boîte de dialogue Supprimer dans laquelle vous pouvez choisir une table à supprimer de la base de données spécifiée avec la source de données et à supprimer du disque.  
  
## <a name="remarks"></a>Notes  
 Lorsque l’instruction DROP TABLE est émise, tous les index principaux, les valeurs par défaut et les règles de validation associées à la table sont également supprimés. DROP TABLE affecte également les autres tables de la base de données spécifiée avec la source de données si ces tables ont des règles ou des relations associées à la table en cours de suppression. Les règles et les relations ne sont plus valides lorsque la table est supprimée de la base de données.  
  
## <a name="driver-remarks"></a>Remarques sur le pilote  
 Lorsque votre application envoie la TABLE de suppression d’instruction SQL ODBC à la source de données, le pilote ODBC Visual FoxPro convertit la commande en commande Visual FoxProDROP TABLE à l’aide de la syntaxe indiquée dans le tableau suivant.  
  
|Syntaxe ODBC|Source de données|Syntaxe Visual FoxPro|  
|-----------------|-----------------|--------------------------|  
|DROP TABLE *base-table-Name*|Base de données (fichier. DBC)|SUPPRIMER la TABLE *TableName* Delete|  
||Répertoire de tables libres (fichiers. dbf)|EFFACER *dbfName*<br /><br /> EFFACER *cdxName*<br /><br /> EFFACER *fptName*|
