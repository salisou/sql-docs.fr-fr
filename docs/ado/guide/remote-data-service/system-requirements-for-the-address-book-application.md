---
title: Configuration système requise pour l’application Carnet d’adresses | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- address book application scenario [ADO]
- RDS scenarios [ADO]
ms.assetid: da385405-1c9a-478b-9bf6-fba70015324c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2450cc97229a6629d4c2895f3960e3033d129789
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67922035"
---
# <a name="system-requirements-for-the-address-book-application"></a>Configuration système exigée pour l’application Carnet d’adresses
Pour configurer l’exemple d’application de carnet d’adresses, vous devez respecter les conditions suivantes relatives aux logiciels et aux bases de données :  
  
> [!IMPORTANT]
>  À compter de Windows 8 et de Windows Server 2012, les composants serveur RDS ne sont plus inclus dans le système d’exploitation Windows (pour plus d’informations, consultez le livre de recettes sur la compatibilité avec Windows 8 et [Windows server 2012](https://www.microsoft.com/download/details.aspx?id=27416) ). Les composants clients RDS seront supprimés dans une prochaine version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Les applications qui utilisent RDS doivent migrer vers le [service de données WCF](https://go.microsoft.com/fwlink/?LinkId=199565).  
  
## <a name="software-requirements"></a>Configuration logicielle  
 La configuration logicielle requise pour l’exécution de cette application Web est la suivante :  
  
-   Microsoft Windows NT® Server 4,0, avec Service Pack 3 ou version ultérieure, ou Microsoft Windows® 2000 Server.  
  
-   Microsoft Internet Information Services (IIS) version 3,0 ou ultérieure, avec Active Server pages.  
  
 La configuration logicielle requise de l’ordinateur client pour l’exécution de cette application Web est la suivante :  
  
-   Microsoft Internet Explorer 4,0 ou version ultérieure.  
  
-   Station de travail ou serveur Microsoft Windows NT 4,0, Windows 2000 ou Microsoft Windows 98.  
  
## <a name="database-requirements"></a>Configuration requise pour la base de données  
 Pour utiliser cet exemple, vous devez disposer des éléments suivants :  
  
-   Un serveur de base de données opérationnel Microsoft® SQL Server version 6,5 ou ultérieure.  
  
-   Privilèges permettant de créer la base de données et de la remplir avec les exemples de données.  
  
-   Vérification des données remplies par le biais d’Enterprise Manager ou des utilitaires ISQL (appelé analyseur de requêtes dans SQL Server 7,0).  
  
 Si vous n’avez pas de privilèges, il se peut que votre administrateur de base de données doive configurer le système et vous accorder l’autorisation d’accès à la base de données ou configurer la base de données pour vous.  
  
## <a name="see-also"></a>Voir aussi  
 [Exécution du script SQL du carnet d’adresses](../../../ado/guide/remote-data-service/running-the-address-book-sql-script.md)   
 [DataControl, objet (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)   
 [Exécution de l’exemple d’application Carnet d’adresses](../../../ado/guide/remote-data-service/running-the-address-book-sample-application.md)


