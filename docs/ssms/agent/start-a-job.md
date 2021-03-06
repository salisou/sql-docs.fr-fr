---
title: Démarrer un travail
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], starting
- SQL Server Agent jobs, starting
- starting jobs
ms.assetid: cec9f7f7-d0a7-4239-9dc5-a69c011ebaa0
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 85cc3a1b4e83e8b64f0e6277211b18e93c1c5232
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "75257940"
---
# <a name="start-a-job"></a>Démarrer un travail
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> Dans [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance), la plupart des fonctionnalités SQL Server Agent sont prises en charge. Pour plus d’informations, consultez [Différences T-SQL entre Azure SQL Database Managed Instance et SQL Server](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent).

Cette rubrique indique comment démarrer l’exécution d’un travail de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)] ou SQL Server Management Objects.  
  
Un travail est une série d'actions exécutées par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent peuvent être exécutés sur un serveur local ou sur plusieurs serveurs distants.  
  
-   **Avant de commencer :**  
  
    [Sécurité](#Security)  
  
-   **Pour démarrer un travail, utilisez :**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server Management Objects](#SMO)  
  
## <a name="before-you-begin"></a><a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="security"></a><a name="Security"></a>Sécurité  
Pour plus d'informations, consultez [Implémenter la sécurité de SQL Server Agent](../../ssms/agent/implement-sql-server-agent-security.md).  
  
## <a name="using-sql-server-management-studio"></a><a name="SSMS"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-start-a-job"></a>Pour démarrer un travail  
  
1.  Dans **l’Explorateur d'objets** , connectez-vous à une instance du [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]et développez-la.  
  
2.  Développez **Agent SQL Server** et développez **Travaux**. Selon la façon dont vous voulez démarrer le travail, procédez de l'une des manières suivantes :  
  
    -   Si vous travaillez sur un seul serveur, si vous travaillez sur un serveur cible ou si vous exécutez un travail de serveur local sur un serveur maître, cliquez avec le bouton droit sur le travail à démarrer et cliquez sur **Démarrer le travail**.  
  
    -   Pour démarrer plusieurs travaux, cliquez avec le bouton droit sur **Moniteur d'activité des travaux**, puis cliquez sur **Afficher l'activité du travail**. Dans le Moniteur d'activité des travaux, vous pouvez sélectionner plusieurs travaux. Pour cela, cliquez avec le bouton droit sur votre sélection et cliquez sur **Démarrer les travaux**.  
  
    -   Si vous travaillez sur un serveur maître et souhaitez que tous les serveurs cibles exécutent le travail simultanément, cliquez avec le bouton droit sur le travail à démarrer, cliquez sur **Démarrer le travail**, puis sur **Démarrer sur tous les serveurs cibles**.  
  
    -   Si vous travaillez sur un serveur maître et souhaitez spécifier les serveurs cibles pour le travail, cliquez avec le bouton droit sur le travail à démarrer, cliquez sur **Démarrer le travail**, puis sur **Démarrer sur les serveurs cibles spécifiques**. Dans la boîte de dialogue **Publier les instructions à télécharger** , activez la case à cocher **Serveurs cibles sélectionnés** , puis sélectionnez chacun des serveurs cibles sur lesquels ce travail doit s'exécuter.  
  
## <a name="using-transact-sql"></a><a name="TSQL"></a>Utilisation de Transact-SQL  
  
#### <a name="to-start-a-job"></a>Pour démarrer un travail  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance du [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- starts a job named Weekly Sales Data Backup.    
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_start_job N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_start_job (Transact-SQL)](https://msdn.microsoft.com/8a91df6a-eb84-4512-9a17-4a6e32a9538a).  
  
## <a name="using-sql-server-management-objects"></a><a name="SMO"></a>Utilisation de SQL Server Management Objects  
**Pour démarrer un travail**  
  
Appelez la méthode **Start** de la classe **Job** à l’aide du langage de programmation de votre choix, tel que Visual Basic, Visual C# ou PowerShell. Pour plus d’informations, consultez [SQL Server Management Objects (SMO)](https://msdn.microsoft.com/library/ms162169.aspx).  
  
