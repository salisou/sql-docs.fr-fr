---
title: Connexion à SQL Server pour la suppression | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 030b10c2-6b88-4c2c-bf67-22994be25a60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b28d1c4cb3f17ae5a22e98735730a94ae186885
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "71298895"
---
# <a name="connection-to-sql-server-for-delete"></a>Connexion à SQL Server pour la suppression

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Lorsqu’une connexion sans rôle de base de données qui inclut l’autorisation d’accès en écriture (par exemple le rôle **db_owner** ) à la base de données MSXDBCDC tente de supprimer une instance Oracle CDC, la boîte de dialogue Connexion à SQL Server s’affiche.  
  
 Dans cette boîte de dialogue, vous devez entrer les informations d’identification pour une connexion qui a l’autorisation d’accès en écriture à la base de données MSXDBCDC, notamment le rôle de base de données **db_owner** pour supprimer l’instance Oracle CDC.  
  
 Dans la boîte de dialogue Connexion à SQL Server, entrez les informations suivantes :  
  
 **Nom de serveur**  
 Tapez le nom du serveur où se trouve [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
 **Authentification**  
 Sélectionnez l’un des suivants :  
  
-   **Authentification Windows**  
  
-   **Authentification SQL Server**: Si vous sélectionnez cette option, vous devez taper **l’identifiant** et le **mot de passe** de l’utilisateur dans l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à laquelle vous vous connectez.  
  
 **Options**  
 Cliquez sur la flèche pour afficher les options disponibles à configurer. Vous pouvez choisir de conserver ces options avec leur valeur par défaut. Options disponibles :  
  
-   **Délai de connexion**: Tapez le délai (en secondes) pendant lequel le programme attend une connexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] avant de générer une erreur de délai d’expiration. La valeur par défaut est **15**.  
  
-   **Délai d’exécution**: Tapez le délai (en secondes) pendant lequel le programme attend la fin d’exécution d’une commande SQL avant de générer une erreur de délai d’expiration. La valeur par défaut est **30**.  
  
-   **Chiffrer la connexion**: Sélectionnez **Chiffrer la connexion** pour garantir que la connexion [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] établie est chiffrée afin d’assurer la protection des données.  
  
-   **Avancé**: Cliquez sur **Avancé** et tapez toutes les propriétés de connexion supplémentaires dans la boîte de dialogue Propriétés avancées de connexion, si nécessaire.  
  
## <a name="see-also"></a>Voir aussi  
 [Autorisations de connexion SQL Server nécessaires pour le service CDC](../../integration-services/change-data-capture/sql-server-connection-required-permissions-for-the-cdc-service.md)  
  
  
