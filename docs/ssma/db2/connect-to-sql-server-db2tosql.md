---
title: Se connecter à SQL Server (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: bc14a072-8949-4ee0-a4b4-ada55fe8df5c
author: Shamikg
ms.author: Shamikg
ms.openlocfilehash: 3d96be29aa74d3903e47f20ec6841b4a20135727
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68141075"
---
# <a name="connect-to-sql-server-db2tosql"></a>Se connecter à SQL Server (DB2ToSQL)
Utilisez la boîte de dialogue **se connecter au SQL Server** pour vous connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’instance de sur laquelle vous souhaitez effectuer la migration. Pour accéder à la boîte de dialogue **se connecter à SQL Server** , dans le menu **fichier** , cliquez sur **se connecter à SQL Server**.  
  
## <a name="options"></a>Options  
**Nom du serveur**  
Entrez ou sélectionnez l’instance de SQL Server à laquelle se connecter. Par défaut, l’instance que vous avez connectée au plus récemment s’affiche.  
  
-   Si vous vous connectez à l’instance par défaut sur l’ordinateur local, vous pouvez entrer **localhost** ou un point (**.**).  
  
-   Si vous vous connectez à l’instance par défaut sur un autre ordinateur, entrez le nom de l’ordinateur.  
  
-   Si vous vous connectez à une instance nommée sur un autre ordinateur, entrez le nom de l’ordinateur, une barre oblique inverse et le nom de l’instance, par exemple *monserveur*\\*MyInstance*.  
  
**Port du serveur**  
Si votre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’est pas configurée pour accepter les connexions sur le port par défaut (1433), entrez le numéro de port. Dans le cas contraire, laissez cette valeur vide.  
  
**Sauvegarde de la base de données**  
Spécifiez la base de données vers laquelle migrer les objets et les données. Cette option n’est pas disponible lors de la reconnexion à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
**Authentification**  
Sélectionnez la méthode d’authentification utilisée pour se connecter à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour utiliser votre compte Windows actuel, sélectionnez authentification Windows. Pour spécifier une [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connexion et un mot de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] passe, sélectionnez authentification.  
  
**Nom d'utilisateur**  
Si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, entrez la connexion de cette instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous utilisez l’authentification Windows, cette option n’est pas disponible.  
  
**Mot de passe**  
Si vous utilisez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, entrez le mot de passe de la connexion sur cette [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]instance de. Si vous utilisez l’authentification Windows, cette option n’est pas disponible.  
  
**Chiffrer la connexion**  
Si vous souhaitez vous connecter en toute sécurité à SQL Server, utilisez l’option chiffrer la connexion en activant la case à cocher **chiffrer la connexion** .  
  
**Faire confiance au certificat de serveur**  
Si vous souhaitez utiliser cette option, activez la case à cocher **approuver le certificat du serveur** .  
  
> [!NOTE]  
> Pour activer le **certificat de serveur de confiance**, « Encrypt » doit avoir la valeur **true**.  
  
