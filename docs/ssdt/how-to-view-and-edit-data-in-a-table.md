---
title: Afficher et modifier des données dans une table
ms.prod: sql
ms.technology: ssdt
ms.topic: conceptual
f1_keywords:
- SQL.DATA.TOOLS.QUERYRESULTS.F1
- sql.data.tools.queryresults.executequerydeletingrow
ms.assetid: bb67ce83-a87a-4e14-84cd-9a5930fe74c8
author: markingmyname
ms.author: maghan
manager: jroth
ms.reviewer: “”
ms.custom: seo-lt-2019
ms.date: 02/09/2017
ms.openlocfilehash: 557b5d5c5986b47eab22bb9d70bd8103c5032eeb
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75226758"
---
# <a name="how-to-view-and-edit-data-in-a-table"></a>Procédure : afficher et modifier des données dans une table

Vous pouvez consulter, modifier et supprimer des données d'une table existante à l'aide de l'Éditeur de données visuel.  
  
> [!WARNING]  
> Les procédures suivantes utilisent les entités créées dans les procédures précédentes de la section [Développement d’une base de données connectée](../ssdt/connected-database-development.md).  
  
### <a name="to-edit-data-in-a-table-visually-using-the-data-editor"></a>Pour modifier des données dans une table visuellement à l'aide de l'Éditeur de données  
  
1.  Dans l’**Explorateur d'objets SQL Server**, cliquez avec le bouton droit sur **Produit** et sélectionnez **Afficher les données**.  
  
2.  L'Éditeur de données démarre. Notez les lignes ajoutées à la table dans les procédures précédentes.  
  
3.  Dans l’Explorateur d'objets SQL Server, cliquez avec le bouton droit sur **Fruits** et sélectionnez **Afficher les données**.  
  
4.  Dans l'Éditeur de données, tapez **1** pour **Id** et **True** pour **Perishable**, puis appuyez sur Entrée ou sur Tabulation pour déplacer le focus de la nouvelle ligne afin de la valider dans la base de données.  
  
5.  Répétez l'étape ci-dessus pour entrer **2**, **False** et **3**, **False** dans la table.  
  
    Notez que lorsque vous modifiez une ligne, vous pouvez toujours annuler les modifications apportées à une cellule en appuyant sur Échap.  
  
6.  Pour afficher vos modifications sous la forme d'un script, cliquez sur le bouton **Script** dans la barre d'outils. Vous pouvez aussi utiliser le bouton **Générer un script dans un fichier** pour les enregistrer dans un fichier de script .sql à exécuter ultérieurement.  
  
7.  Dans l’**Explorateur d'objets SQL Server**, cliquez avec le bouton droit sur **Trade** et sélectionnez **Nouvelle requête**. Dans l'éditeur, tapez `select * from dbo.PerishableFruits` et cliquez sur le bouton **Exécuter la requête** pour revenir aux données représentées par l'affichage `PerishableFruits`.  
  
