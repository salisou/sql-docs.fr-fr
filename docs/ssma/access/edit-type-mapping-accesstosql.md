---
title: Modifier le mappage de type (AccessToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 7f9d9530-6c04-41d9-bbe7-d91820a30066
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 7d41fc2f01e2cfbc2b20c58ea9be640f2afd8ea0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68006573"
---
# <a name="edit-type-mapping-accesstosql"></a>Modifier le mappage de type (AccessToSQL)
La boîte de dialogue **modifier le mappage de type** vous permet de spécifier la manière dont les types sont mappés entre les objets de base de données source et de destination.  
  
Vous pouvez accéder à cette boîte de dialogue à plusieurs endroits :  
  
-   Lorsque vous sélectionnez une base de données source ou un objet de base de données, l’onglet **mappage de type** s’affiche à droite de l’Explorateur de métadonnées. Cliquez sur **Ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
-   Dans le menu **Outils** , sélectionnez **paramètres du projet** ou paramètres du **projet par défaut**. Dans la boîte de dialogue qui en résulte, sélectionnez **mappage de type**. Cliquez sur **Ajouter** pour ajouter un nouveau mappage de type, ou cliquez sur **modifier** pour modifier un mappage de type existant.  
  
Les mappages de types spécifiques aux tables remplacent les mappages de type de projet et de base de données. Les mappages spécifiques à la base de données remplacent les mappages de projet.  
  
## <a name="options"></a>Options  
**Type de source**  
Sélectionnez le type de données source à mapper à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un type de données.  
  
Si le type de données est de longueur variable, les champs suivants s’affichent sous le **type de source**:  
  
**From**  
Spécifiez la longueur minimale pour ce mappage. Par exemple, pour le type de données **Text** , vous pouvez entrer 10 pour spécifier que ce mappage s’adresse à une plage commençant par **Text (10)**.  
  
**To**  
Spécifiez la longueur maximale pour ce mappage. Par exemple, pour le type de données **Text** , vous pouvez entrer 20 pour spécifier que ce mappage s’adresse à une plage se terminant au **texte (20)**.  
  
**Type de cible**  
Sélectionnez le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] type de données auquel le type de données source est mappé. Lorsque SSMA crée la table ou la procédure stockée dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le type de données source passe à ce type de données.  
  
Si le type de données est de longueur variable, le champ suivant s’affiche sous **type de cible**:  
  
**Remplacer par**  
Spécifiez la longueur cible pour ce mappage. Par exemple, pour le type de données **nvarchar** , vous pouvez entrer 20 pour spécifier que le type de données source spécifié doit être mappé à **nvarchar (20)**.  
  
