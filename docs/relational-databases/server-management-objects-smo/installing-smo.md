---
title: Installation de SMO | Microsoft Docs
ms.custom: ''
ms.date: 08/06/2017
ms.prod: sql
ms.reviewer: ''
ms.prod_service: database-engine
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- installing SMO
- SMO [SQL Server], installing
- SQL Server Management Objects, installing
ms.assetid: 140e9971-4940-4866-89b9-5cec938e2a16
author: markingmyname
ms.author: maghan
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: cabd2d1ebbe726971e7837ff3e268ad3c2cee89f
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "72041259"
---
# <a name="installing-smo"></a>Installation de SMO

[!INCLUDE[appliesto-ss-asdb-asdw-xxx-md](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Cette page fournit des informations sur l’installation de SMO pour une utilisation par les applications et la configuration requise pour utiliser SMO.

## <a name="smo-nuget-package"></a>Package NuGet SMO

À partir [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de 2017 Smo est distribué en tant que package NuGet [Microsoft. SqlServer. SqlManagementObjects](https://www.nuget.org/packages/Microsoft.SqlServer.SqlManagementObjects) pour permettre aux utilisateurs de développer des applications avec Smo.

Il s’agit d’un remplacement de SharedManagementObjects. msi, qui a été précédemment publié dans le cadre du Feature Pack SQL pour chaque version de SQL Server. Les applications qui utilisent SMO doivent être mises à jour pour utiliser le package NuGet à la place et doivent s’assurer que les fichiers binaires sont installés avec l’application en cours de développement.

>>[!Important]
>>Comme mentionné dans la page [fichiers et numéros de version](files-and-version-numbers.md) , vous ne devez pas installer les assemblys Smo dans le GAC. Cela peut entraîner des problèmes avec d’autres applications qui utilisent également ces versions de SMO (par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] exemple, Management Studio).

## <a name="installing-the-package"></a>Installation du package

Consultez [NuGet démarrage rapide-utilisation d’un package](https://docs.microsoft.com/nuget/quickstart/use-a-package) pour obtenir des instructions et des exemples d’installation et d’utilisation d’un package NuGet. 
  
## <a name="system-requirements"></a>Configuration requise
  
 SMO requiert [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] l’exécution de 4,0 ou .net Core 2,0, donc toutes les applications qui l’utilisent doivent s’assurer que cette version ou une version ultérieure est installée sur les ordinateurs clients. Certains binaires natifs installés avec les bibliothèques SMO NetFx nécessitent également l’installation du runtime VC 2013. ce Runtime n’est pas inclus dans le package. Vous pouvez télécharger le package Redist approprié à votre architecture cible à partir dehttps://www.microsoft.com/download/details.aspx?id=40784
  
