---
title: 'Tâche 4 : création d’un projet SSIS à l’aide de SQL Server Data Tools | Microsoft Docs'
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 8603ea91-2ec4-40b6-8070-4f824332f5d3
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: bcf16dc7d63e6a4acca6c30871666d1ffe996192
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78171718"
---
# <a name="task-4-creating-an-ssis-project-using-sql-server-data-tools"></a>Tâche 4 : Création d’un projet SSIS à l’aide de SQL Server Data Tools
  Au cours de cette tâche, vous allez créer un projet SSIS à l’aide de **SQL Server Data Tools** pour automatiser le nettoyage et la correspondance des données des fournisseurs.

1.  Lancez **SQL Server Data Tools**. Cliquez sur Démarrer, pointez sur **tous les programmes**, développez **Microsoft SQL Server 2012**, puis cliquez sur **SQL Server Data Tools**.

2.  Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

3.  Développez **Business Intelligence** dans le volet **modèles installés** , puis sélectionnez **Integration Services**.

     ![Visual Studio - Boîte de dialogue Nouveau projet](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-01.jpg "Visual Studio - Boîte de dialogue Nouveau projet")

4.  Sélectionnez **Integration Services projet** dans la **liste des types de projets**.

5.  Tapez **CleanseAndCurateSuppliers** pour **nom** , puis cliquez sur **OK**.

6.  Dans **Explorateur de solutions** fenêtre, cliquez avec le bouton droit sur **Package. dtsx** , puis sélectionnez **Renommer**. Si **Explorateur de solutions** fenêtre ne s’affiche pas, cliquez sur **affichage** dans la barre de menus et cliquez sur **Explorateur de solutions**.

     ![Package.dtsx - Menu Renommer](../../2014/tutorials/media/et-creatinganssisprojectusingsqlsdt-02.jpg "Package.dtsx - Menu Renommer")

7.  Tapez **CleanseAndCurate. dtsx** et appuyez sur **entrée**. Assurez-vous que l' **extension** reste **. dtsx**.

## <a name="next-step"></a>étape suivante
 [Tâche 5 : Ajout d’une tâche de flux de données](task-5-adding-data-flow-task.md)


