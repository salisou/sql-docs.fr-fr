---
title: catalog.set_execution_property_override_value | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: 37cb3c01-f4c0-4978-8e40-a975456def5a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a8e85c35552a8bcbf4190bd3ce36b4a65be96789
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71295301"
---
# <a name="catalogset_execution_property_override_value"></a>catalog.set_execution_property_override_value 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Définit la valeur d'une propriété pour une instance d'exécution dans le catalogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.set_execution_property_override_value [ @execution_id = execution_id  
    , [ @property_path = ] property_path  
    , [ @property_value = ] property_value  
    , [ @sensitive = ] sensitive  
```  
  
## <a name="arguments"></a>Arguments  
 [ @execution_id = ] *execution_id*  
 Identificateur unique de l'instance d'exécution. *execution_id* est de type **bigint**.  
  
 [ @property_path = ] *property_path*  
 Chemin d'accès à la propriété dans le package. *property_path* est de type **nvarchar(4000)** .  
  
 [ @property_value = ] *property_value*  
 Valeur de remplacement à affecter à la propriété. *property_value* est de type **nvarchar(max)** .  
  
 [ @sensitive = ] *sensitive*  
 Lorsque la valeur est 1, la propriété est sensible et est chiffrée lorsqu'elle est stockée. Lorsque la valeur est 0, la propriété n'est pas sensible et la valeur est stockée dans en texte en clair. L’argument *sensitive* est de type **bit**.  
  
## <a name="remarks"></a>Notes  
 Cette procédure remplit la même fonction que la section **Substitutions de propriété** sous l’onglet **Avancé** de la boîte de dialogue **Exécuter le package**. Le chemin d’accès de la propriété est dérivé de la propriété **Chemin d’accès au package** de la tâche du package.  
  
## <a name="return-code-value"></a>Valeur du code de retour  
 0 (succès)  
  
## <a name="result-sets"></a>Jeux de résultats  
 None  
  
## <a name="errors-and-warnings"></a>Erreurs et avertissements  
 La liste suivante décrit quelques conditions qui peuvent générer une erreur ou un avertissement :  
  
-   L’utilisateur n’a pas les autorisations appropriées  
  
-   L'identificateur d'exécution n'est pas valide.  
  
-   Le chemin de la propriété n'est pas valide.  
  
-   Le type de données de la valeur de propriété ne correspond pas au type de propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [catalog.set_execution_parameter_value &#40;base de données SSISDB&#41;](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)  
  
  
