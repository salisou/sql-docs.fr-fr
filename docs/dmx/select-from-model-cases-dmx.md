---
title: Sélectionnez à &lt;partir&gt;du modèle. CAS (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 5f0334c37eeedafee7066f01d61745fcb82d1629
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68892844"
---
# <a name="select-from-ltmodelgtcases-dmx"></a>Sélectionnez à &lt;partir&gt;du modèle. CAS (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Prend en charge l'extraction et retourne les cas qui ont été utilisés pour l'apprentissage du modèle. Vous pouvez également retourner des colonnes de structure qui ne sont pas incluses dans le modèle si l'extraction a été activée sur la structure d'exploration de données et sur le modèle d'exploration de données et que vous disposez des autorisations appropriées.  
  
 Si l'extraction n'est pas activée sur le modèle d'exploration de données, cette instruction échoue.  
  
> [!NOTE]  
>  En DMX (Data Mining Extensions), vous ne pouvez activer l'extraction que lors de la création du modèle. Vous pouvez ajouter l'extraction à un modèle existant à l'aide de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], mais le modèle doit être retraité avant que vous ne puissiez afficher ou interroger les cas.  
  
 Pour plus d’informations sur l’activation de l’extraction, consultez [créer un modèle d’exploration de données &#40;dmx&#41;](../dmx/create-mining-model-dmx.md), [SELECT INTO &#40;DMX&#41;](../dmx/select-into-dmx.md)et [ALTER Mining structure &#40;DMX&#41;](../dmx/alter-mining-structure-dmx.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
SELECT [FLATTENED] [TOP <n>] <expression list> FROM <model>.CASES  
[WHERE <condition expression>][ORDER BY <expression> [DESC|ASC]]  
```  
  
## <a name="arguments"></a>Arguments  
 *n*  
 Facultatif. Entier qui spécifie le nombre de lignes à retourner.  
  
 *liste d’expressions*  
 Liste d'expressions séparées par des virgules. Une expression peut comprendre des identificateurs de colonne, des fonctions définies par l'utilisateur, des fonctions VBA, etc.  
  
 Pour inclure une colonne de structure qui n'est pas incluse dans le modèle d'exploration de données, utilisez la fonction `StructureColumn('<structure column name>')`.  
  
 *model*  
 Identificateur du modèle  
  
 *expression de condition*  
 Condition pour restreindre les valeurs retournées de la liste des colonnes.  
  
 *expression*  
 Facultatif. Expression qui retourne une valeur scalaire.  
  
## <a name="remarks"></a>Notes  
 Si l'extraction est activée à la fois sur le modèle d'exploration de données et la structure d'exploration de données, les utilisateurs membres d'un rôle qui a des autorisations d'extraction sur le modèle et la structure peuvent accéder aux colonnes de la structure d'exploration de données qui ne sont pas incluses dans le modèle d'exploration de données. Par conséquent, pour protéger des données sensibles ou des informations personnelles, vous devez construire votre vue de source de données pour masquer les informations personnelles et accorder l’autorisation **AllowDrillThrough** sur une structure d’exploration de données uniquement lorsque cela est nécessaire.  
  
 Le [décalage &#40;fonction DMX&#41;](../dmx/lag-dmx.md) peut être utilisé avec les modèles de série chronologique pour retourner ou filtrer sur le décalage horaire entre chaque cas et l’heure initiale.  
  
 L’utilisation de la fonction [IsInNode &#40;DMX&#41;](../dmx/isinnode-dmx.md) dans la clause **Where** renvoie uniquement les cas associés au nœud spécifié par la colonne NODE_UNIQUE_NAME de l’ensemble de lignes de schéma.  
  
## <a name="examples"></a>Exemples  
 Les exemples suivants sont basés sur le publipostage ciblé de la structure d’exploration de données, [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)]qui est basé sur la base de données et ses modèles d’exploration de données associés. Pour plus d’informations, consultez le didacticiel sur l' [exploration de données de base](https://msdn.microsoft.com/library/6602edb6-d160-43fb-83c8-9df5dddfeb9c).  
  
### <a name="example-1-drillthrough-to-model-cases-and-structure-columns"></a>Exemple 1 : Extraction dans des cas de modèles et des colonnes de structure  
 L'exemple suivant retourne les colonnes de tous les cas qui ont été utilisés pour tester le modèle Targeted Mailing. Si la structure d'exploration de données sur laquelle le modèle est construit ne possède pas de jeu de données du test d'exclusion, cette requête retourne 0 cas. Vous pouvez utiliser la liste d'expressions pour retourner uniquement les colonnes dont vous avez besoin.  
  
```  
SELECT * FROM [TM Decision Tree].Cases  
WHERE IsTestCase();  
```  
  
### <a name="example-2-drillthrough-to-training-cases-in-a-specific-node"></a>Exemple 2 : Extraction dans des cas d'apprentissage dans un nœud spécifique  
 L'exemple suivant retourne uniquement les cas utilisés pour l'apprentissage de Cluster 2. Le nœud pour Cluster 2 a la valeur '002' pour la colonne NODE_UNIQUE_NAME. L'exemple retourne également une colonne de structure, [Customer Key], qui ne faisait pas partie du modèle d'exploration de données, et fournit l'alias `CustomerID` pour la colonne. Notez que le nom de la colonne de structure est passé en tant que valeur de chaîne ; par conséquent, il doit être entre guillemets, et non entre crochets.  
  
```  
SELECT StructureColumn('Customer Key') AS CustomerID, *   
FROM [TM_Clustering].Cases  
WHERE IsTrainingCase()  
AND IsInNode('002')  
```  
  
 Pour retourner une colonne de structure, les autorisations d'extraction doivent être activées à la fois sur le modèle d'exploration de données et sur la structure d'exploration de données.  
  
> [!NOTE]  
>  La prise en charge de l'extraction varie selon le type de modèle d'exploration de données. Pour plus d’informations sur les modèles qui prennent en charge l’extraction, consultez [requêtes d’extraction &#40;&#41;d’exploration de données ](https://docs.microsoft.com/analysis-services/data-mining/drillthrough-queries-data-mining).  
  
## <a name="see-also"></a>Voir aussi  
 [SÉLECTIONNER &#40;&#41;DMX](../dmx/select-dmx.md)   
 [Instructions de définition de données DMX&#41; Data Mining Extensions &#40;](../dmx/dmx-statements-data-definition.md)   
 [Data Mining Extensions &#40;les instructions de manipulation de données DMX&#41;](../dmx/dmx-statements-data-manipulation.md)   
 [Guide de référence des instructions DMX &#40;Data Mining Extensions&#41;](../dmx/data-mining-extensions-dmx-statements.md)  
  
  
