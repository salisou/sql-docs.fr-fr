---
title: Ajouter un attribut à une dimension | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- adding attributes
- automatic attribute creation
- attributes [Analysis Services], creating
- attributes [Analysis Services], adding
- manual attribute creation [Analysis Services]
ms.assetid: 25826ba1-2b38-4b34-bd3a-7eba116093ae
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 70817c567b77af2bfdb7d715683ae6081fda442b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66077429"
---
# <a name="add-an--attribute-to-a-dimension"></a>Ajouter un attribut à une dimension
  Vous pouvez ajouter un attribut à une dimension soit automatiquement, soit manuellement [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]dans.  
  
 Pour créer un attribut automatiquement, dans le volet **Structure de dimension** du Concepteur de dimensions de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], sélectionnez la colonne que vous voulez mapper avec un attribut, puis faites glisser cette colonne du volet **Vue de source de données** jusqu’au volet **Attributs** . Vous créez ainsi un attribut qui est mappé avec la colonne et en reçoit le nom. S’il existe déjà un attribut de ce nom, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] lui ajoute à la fin un numéro en commençant par « 1 » pour le premier nom en double.  
  
 Pour créer un attribut manuellement, affichez la grille dans le volet **Attributs** . Dans la colonne nom de la dernière ligne de la grille, cliquez sur le ** \<nouvel attribut>** élément. Tapez le nom du nouvel attribut. Vous créez ainsi un attribut qui n'est pas mappé avec une colonne et dont toutes les propriétés ont leurs valeurs par défaut. Vous pouvez définir le mappage dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] en configurant la propriété **KeyColumns** du nouvel attribut.  
  
 Pour plus d’informations, consultez [Définir un nouvel attribut automatiquement](attribute-properties-define-a-new-attribute-automatically.md), [Définir un nouvel attribut manuellement](../define-a-new-attribute-manually.md), [Lier un attribut à une colonne de nom](attribute-properties-bind-an-attribute-to-a-name-column.md)et [Modifier la propriété KeyColumn d’un attribut](attribute-properties-modify-the-keycolumn-property.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des propriétés d’attribut de dimension](dimension-attribute-properties-reference.md)  
  
  
