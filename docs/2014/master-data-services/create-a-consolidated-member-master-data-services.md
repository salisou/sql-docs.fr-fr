---
title: Créer un membre consolidé (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 588295d0705ec9c556c85eb5bef1d96d8128b580
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78176068"
---
# <a name="create-a-consolidated-member-master-data-services"></a>Créer un membre consolidé (Master Data Services)
  Dans [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], créez un membre consolidé lorsque vous souhaitez un nœud parent pour une hiérarchie explicite. Les membres consolidés peuvent avoir leurs propres attributs. Ils sont utilisés pour le regroupement. Comme indiqué dans l'exemple suivant, les membres consolidés peuvent être utilisés pour les groupes de comptes qui ont des comptes sous eux.

 ![Membres consolidés MDS](../../2014/master-data-services/media/mds-consolidated-members.png "Membres consolidés MDS")

## <a name="prerequisites"></a>Prérequis
 Pour effectuer cette procédure :

-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .

-   Vous devez au minimum disposer de l'autorisation **Mettre à jour** sur l'objet modèle consolidé de l'entité à laquelle vous ajoutez un membre.

### <a name="to-create-a-consolidated-member"></a>Pour créer un membre consolidé

1.  Dans la page d'accueil de [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] , dans la liste **Modèle** , sélectionnez un modèle.

2.  Dans la liste **Version** , sélectionnez une version.

3.  Cliquez sur **Explorateur**.

4.  Dans la barre de menus, pointez sur **Hiérarchies** , puis cliquez sur le nom de la hiérarchie à laquelle vous souhaitez ajouter un membre consolidé.

5.  Au-dessus de la grille, sélectionnez **Membres consolidés** ou l'option **Tous les membres consolidés de la hiérarchie** .

6.  Cliquez sur **Ajouter**.

7.  Dans le volet de droite, remplissez les champs.

8.  Facultatif. Dans la zone **Annotations** , tapez un commentaire pour expliquer l'ajout du membre. Tous les utilisateurs ayant accès au membre peuvent afficher l'annotation.

9. Cliquez sur **OK**.

## <a name="next-steps"></a>Étapes suivantes

-   [Déplacer des membres au sein d’une hiérarchie &#40;Master Data Services&#41;](move-members-within-a-hierarchy-master-data-services.md)

## <a name="see-also"></a>Voir aussi
 [Créez une hiérarchie explicite &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [créer un membre feuille &#40;Master Data Services](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)&#41;[charger ou mettre à jour des membres dans Master Data Services à l’aide des membres du processus de](add-update-and-delete-data-master-data-services.md) site [&#40;](../../2014/master-data-services/members-master-data-services.md) Master Data Services&#41;les [hiérarchies explicites](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) &#40;Master Data Services&#41;


