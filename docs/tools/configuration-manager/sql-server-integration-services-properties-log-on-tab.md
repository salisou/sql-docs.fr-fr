---
title: Propriétés de SQL Server Integration Services (onglet Ouvrir une session)
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
ms.assetid: c0eb1b87-6bb0-475e-8492-0fd3c3f910ea
author: markingmyname
ms.author: maghan
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
ms.openlocfilehash: 59fd7444eecfd0beb6310ecfec3380eaf1b8b3f3
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75306852"
---
# <a name="sql-server-integration-services-properties-log-on-tab"></a>Propriétés de SQL Server Integration Services (onglet Ouvrir une session)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  L'onglet **Ouvrir une session** de la boîte de dialogue [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] **Propriétés de** permet de spécifier le compte utilisé par le service [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ainsi que de démarrer et d'arrêter ce service.  
  
## <a name="options"></a>Options  
 **Compte système local**  
 Spécifie un compte système local, qui ne requiert pas de mot de passe. Cependant, le compte système local peut limiter l'interaction du service avec les autres serveurs, en fonction des privilèges accordés au compte.  
  
 **Ce compte**  
 Spécifiez un compte d'utilisateur local ou de domaine qui utilise l'authentification [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows. [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'utiliser un compte d'utilisateur de domaine doté d'autorisations minimales pour les services. Pour plus d'informations sur la sélection d'un compte, recherchez dans la documentation en ligne la rubrique « Configuration des comptes de services Windows ».  
  
 **Nom du compte**  
 Spécifie le nom de compte d'utilisateur local ou de domaine.  
  
 **Mot de passe**  
 Tapez le mot de passe du compte.  
  
 **Confirmer le mot de passe**  
 Tapez de nouveau le mot de passe du compte.  
  
 **Start**  
 Démarrez le service.  
  
 **Stop**  
 Arrête le service.  
  
 **Suspendre**  
 Suspend le service.  
  
 **Reprendre**  
 Reprend un service suspendu.  
  
  
