---
title: Connexion à des sources de données | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- connections [ADO]
ms.assetid: 82770486-37bd-4c90-885f-6817a7c77ad7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 000302715e7ce7d3a8ae53f06d61f54e98cbd883
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67925796"
---
# <a name="connecting-to-data-sources"></a>Connexion à des sources de données
Un objet de **connexion** ADO représente une session unique avec une source de données, y compris un SGBD, un magasin de fichiers ou un fichier texte délimité par des virgules. Dans le cas d’un système de base de données client/serveur, la connexion ADO peut être une véritable connexion réseau au serveur.  
  
 L’objet de **connexion** prend en charge différentes [Propriétés et méthodes](../../../ado/reference/ado-api/connection-object-properties-methods-and-events.md) pour spécifier des configurations de connexion, ouvrir et fermer des connexions, créer et exécuter des commandes sur la source de données et fournir des informations sur la conception de la source de données sous-jacente sous la forme d’ensembles de lignes de schéma, etc. Selon les fonctionnalités prises en charge par le fournisseur, certaines collections, méthodes ou propriétés d’un objet de **connexion** peuvent ne pas être disponibles.  
  
 Vous pouvez vous connecter à une source de données soit à l’aide d’un objet de **connexion** , soit à l’aide d’un objet **Recordset** .  
  
 Cette section contient les rubriques suivantes :  
  
-   [Utilisation d’un objet Connection](../../../ado/guide/data/using-a-connection-object.md)  
  
-   [Utilisation d’un objet Recordset](../../../ado/guide/data/using-a-recordset-object.md)  
  
-   [Création d’une chaîne de connexion](../../../ado/guide/data/creating-a-connection-string.md)  
  
-   [Spécification des propriétés d’une connexion](../../../ado/guide/data/specifying-connection-properties.md)  
  
-   [Contrôle des transactions](../../../ado/guide/data/controlling-transactions-ado.md)
