---
title: catalog.check_schema_version | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: language-reference
ms.assetid: e0d5e9f5-59c6-4118-87b5-4aa5c37a7df6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7d7ec8899e880220dc2011014501a883fafa4470
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71295613"
---
# <a name="catalogcheck_schema_version"></a>catalog.check_schema_version 

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  Détermine si le schéma de catalogue SSISDB et les binaires [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] (assembly ISServerExec et SQLCLR) sont compatibles.  
  
 ISServerExec.exc enregistre un message d'erreur lorsque le schéma et les fichiers binaires sont incompatibles.  
  
 La version du schéma SSISDB est incrémentée quand le schéma change lors de l'application des correctifs logiciels et lors des mises à niveau. Il est recommandé d'exécuter cette procédure stockée après qu'une sauvegarde SSISDB a été restaurée afin de garantir que le schéma et les fichiers binaires sont compatibles.  
  
## <a name="syntax"></a>Syntaxe  
  
```sql  
catalog.check_schema_version [@use32bitruntime = ] use32bitruntime  
```  
  
## <a name="arguments"></a>Arguments  
 [ @use32bitruntime= ] *use32bitruntime*  
 Lorsque le paramètre est défini sur **1**, c’est la version 32 bits de dtexec qui est appelée. *use32bitruntime* est de type **int**.  
  
## <a name="result-set"></a>Jeu de résultats  
 None  
  
## <a name="permissions"></a>Autorisations  
 Cette procédure stockée requiert l'autorisation suivante :  
  
-   Appartenance au rôle de base de données **ssis_admin**.  
  
  
