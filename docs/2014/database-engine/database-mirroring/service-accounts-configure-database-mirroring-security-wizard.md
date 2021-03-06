---
title: Comptes de service (Assistant Configuration de la sécurité de la mise en miroir de bases de données) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.configdbmsecurwiz.serviceaccounts.f1
ms.assetid: d58d8f93-7888-4d66-af4d-969ef6a2dbee
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 69877c6a20e37e012925185d0b807e9579066e35
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62754397"
---
# <a name="service-accounts-configure-database-mirroring-security-wizard"></a>Comptes de service (Assistant Configuration de la sécurité de la mise en miroir de bases de données)
  Lors de l'utilisation de l'authentification Windows, si les instances de serveur utilisent des comptes différents, spécifiez les comptes de service pour [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces comptes de service doivent tous être des comptes de domaine (dans les mêmes domaines ou des domaines approuvés).  
  
 Si toutes les instances de serveur utilisent le même compte de domaine ou une authentification basée sur les certificats, laissez les champs vides. Cliquez simplement sur **Terminer**; l'Assistant configure alors automatiquement les comptes en fonction du compte de l'Assistant actuel.  
  
> [!IMPORTANT]  
>  Si les points de terminaison de mise en miroir de base de données des instances de serveur sont configurés pour utiliser des certificats, vous devez laisser les champs de compte de service vides.  
  
 **Pour configurer la mise en miroir de bases de données à l'aide de SQL Server Management Studio**  
  
-   [Établir une session de mise en miroir de bases de données au moyen de l’authentification Windows &#40;SQL Server Management Studio&#41;](establish-database-mirroring-session-windows-authentication.md)  
  
-   [Démarrer l’Assistant Configuration de la sécurité de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](start-the-configuring-database-mirroring-security-wizard.md)  
  
## <a name="options"></a>Options  
 **Directeur**  
 Permet de spécifier le compte de service de l'instance de serveur principal. Entrez le nom du domaine en majuscules :  
  
 *DOMAINNAME*\\*Nom* de domaine  
  
 **Miroir**  
 Permet de spécifier le compte de service de l'instance de serveur miroir. Entrez le nom du domaine en majuscules :  
  
 *DOMAINNAME*\\*Nom* de domaine  
  
 **Témoin**  
 Permet de spécifier le compte de service de l'instance de serveur témoin. Entrez le nom du domaine en majuscules :  
  
 *DOMAINNAME*\\*Nom* de domaine  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés de la base de données &#40;page mise en miroir&#41;](../../relational-databases/databases/database-properties-mirroring-page.md)   
 [Démarrer Moniteur de mise en miroir de bases de données &#40;SQL Server Management Studio&#41;](../database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md)   
 [Mise en miroir de bases de données &#40;SQL Server&#41;](database-mirroring-sql-server.md)   
 [Configurer des comptes de connexion pour la mise en miroir de bases de données ou groupes de disponibilité AlwaysOn &#40;SQL Server&#41;](set-up-login-accounts-database-mirroring-always-on-availability.md)  
  
  
