---
title: Commentaires (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 26a529d6eb15997ccb48ad25d8d4fcb11cd2ddfb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68071054"
---
# <a name="comments-dmx"></a>Commentaires (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Les commentaires dans les extensions DMX (Data Mining Extensions) sont des chaînes de [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] texte dans le code de programme qui ne s’exécute pas. Les commentaires sont également appelés remarques. Vous pouvez utiliser les commentaires pour documenter du code ou pour désactiver temporairement les composants d'une instruction ou d'un script DMX lorsque vous analysez le code.  
  
 L'utilisation des commentaires pour documenter votre code programme facilitera la gestion du code.  En effet, les commentaires permettent d'enregistrer des détails tels que le nom du programme, le nom du développeur qui a écrit le code, et les dates des principales modifications du code. Vous pouvez également aussi les utiliser pour décrire des calculs complexes ou pour commenter une méthode de programmation.  
  
 Voici les règles de bases de l'écriture des commentaires :  
  
-   Vous pouvez utiliser tous les caractères ou symboles alphanumériques dans un commentaire. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ignore tous les caractères figurant au sein d'un commentaire.  
  
-   La longueur d'un commentaire dans une instruction ou un script n'est pas limitée. Un commentaire peut être constitué d’une ou de plusieurs lignes.  
  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] prend en charge les types de caractères de commentaire suivants :  
  
-   **(doubles barres obliques).** Ces caractères de commentaire permettent d'écrire un commentaire sur la même ligne que le code à exécuter, ou d'écrire un commentaire sur une ligne séparée. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère tout ce qui est situé à partir des doubles barres obliques jusqu'à la fin de la ligne comme étant le commentaire. Pour créer un commentaire sur plusieurs lignes, utilisez les doubles barres obliques au début de chaque ligne de commentaire. Pour plus d’informations sur ce caractère de commentaire, consultez [double barre oblique &#40;commentaire&#41; &#40;&#41;DMX ](../dmx/double-slash-comment-dmx.md).  
  
-   **--(double trait d’Union).** Ces caractères de commentaire permettent d'écrire un commentaire sur la même ligne que le code à exécuter, ou d'écrire un commentaire sur une ligne séparée. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] considère tout ce qui est situé à partir du double trait d'union jusqu'à la fin de la ligne comme étant le commentaire. Pour créer un commentaire sur plusieurs lignes, utilisez le double trait d'union au début de chaque ligne de commentaire. Pour plus d’informations sur ce caractère de commentaire, consultez [--&#40;comment&#41; &#40;DMX&#41; Summary](../dmx/comment-dmx-summary.md).  
  
-   **/\*... \*/(paires de caractères barre oblique-astérisque).** Ces caractères de commentaire permettent d'écrire un commentaire sur la même ligne que le code à exécuter, d'écrire un commentaire sur une ligne séparée ou même d'écrire des commentaires dans du code exécutable. [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]évalue tous les éléments de la paire de commentaires ouverts (/*) à la paire\*de commentaires de fermeture (/) dans le cadre du commentaire. Pour créer un commentaire sur plusieurs lignes, commencez le commentaire par la paire de caractères de commentaire ouvert (\*/) et terminez le commentaire par la paire de caractères de fermeture\*de commentaire (/). Aucun autre caractère de commentaire ne doit être inclus dans les lignes de commentaire. Pour plus d’informations sur ce caractère de commentaire, consultez [barre oblique &#40;commentaire&#41; &#40;&#41;DMX ](../dmx/slash-star-comment-dmx.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur la&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-reference.md)   
 [Informations de référence sur les fonctions DMX&#41; Data Mining Extensions &#40;](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [Informations de référence sur l’opérateur de&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [Informations de référence sur les instructions DMX&#41; &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-statements.md)   
 [Conventions de syntaxe du&#41; DMX &#40;Data Mining Extensions](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [Data Mining Extensions &#40;les éléments de la syntaxe DMX&#41;](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [Fonctions de prédiction générales &#40;&#41;DMX](../dmx/general-prediction-functions-dmx.md)   
 [Structure et utilisation des requêtes de prédiction DMX](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [Présentation de l’instruction DMX Select](../dmx/understanding-the-dmx-select-statement.md)  
  
  
