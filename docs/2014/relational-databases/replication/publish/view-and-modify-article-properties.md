---
title: Afficher et modifier les propriétés d’un article | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
dev_langs:
- TSQL
helpviewer_keywords:
- sp_changearticle
- sp_helparticle
- viewing replication properties
- sp_changemergearticle
- sp_helpmergearticle
- modifying replication properties, articles
- articles [SQL Server replication], modifying
- articles [SQL Server replication], properties
ms.assetid: e71831fa-3d39-4e4a-9706-4d3a497082cc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 325bedac3968cb59c70863d54c7e0ef429cedd75
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68941075"
---
# <a name="view-and-modify-article-properties"></a>Afficher et modifier les propriétés d'un article
  Cette rubrique décrit comment afficher et modifier les propriétés de l'article dans [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../../includes/tsql-md.md)]ou d'objets RMO (Replication Management Objects).  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Recommandations](#Recommendations)  
  
-   **Pour afficher et modifier les propriétés d'un article à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [Objets RMO (Replication Management Objects)](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> Limitations et restrictions  
  
-   Certaines propriétés ne sont pas modifiables après la création d'une publication et d'autres s'il existe des abonnements à la publication. Les propriétés non modifiables sont affichées en lecture seule.  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> Recommandations  
  
-   Après qu'une publication a été créée, certaines modifications de propriétés nécessitent un nouvel instantané. Si une publication dispose d'abonnements, ces abonnements pourraient devoir alors être réinitialisés selon les modifications que vous avez apportées. Pour plus d’informations, consultez [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md) et [Ajouter et supprimer des articles de publications existantes](add-articles-to-and-drop-articles-from-existing-publications.md).  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
 Affichez et modifiez les propriétés de l’article dans la boîte de dialogue **Propriétés de la publication - \<Publication>** , disponible dans [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] et le Moniteur de réplication. Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](../monitor/start-the-replication-monitor.md).  
  
-   La page **Général** contient le nom et la description de la publication, le nom de la base de données, le type de publication et les paramètres d'expiration des abonnements.  
  
-   La page **Articles** correspond à la page **Articles** de l'Assistant Nouvelle publication. Utilisez-la pour ajouter et supprimer des articles, ainsi que pour modifier des propriétés et le filtrage des colonnes pour des articles.  
  
-   La page **Filtrer les lignes** correspond à la page **Filtrer les lignes de la table** de l'Assistant Nouvelle publication. Utilisez-la pour ajouter, modifier et supprimer des filtres de lignes statiques pour tous les types de publications, ainsi que pour ajouter, modifier et supprimer des filtres de lignes paramétrés et des filtres de jointure pour des publications de fusion.  
  
-   La page **Instantané** permet de spécifier le format et l'emplacement de l'instantané, la compression éventuelle de l'instantané, ainsi que des scripts à exécuter avant et après l'application de l'instantané.  
  
-   La page **Instantané FTP** (pour les publications d'instantané et transactionnelles, et les publications de fusion pour les serveurs de publication exécutant des versions antérieures à SQL Server 2005) permet de spécifier si des Abonnés peuvent télécharger des fichiers d'instantanés via le protocole FTP.  
  
-   La page **Instantané FTP et Internet** (pour les publications de fusion provenant des serveurs de publication exécutant SQL Server 2005 ou version ultérieure) permet de spécifier si des Abonnés peuvent télécharger des fichiers d'instantanés via FTP et si des Abonnés peuvent synchroniser des abonnements via HTTPS.  
  
-   La page **Options d'abonnement** permet de définir diverses options qui s'appliquent à tous les abonnements. Les options diffèrent en fonction du type de publication.  
  
-   La page **Liste d'accès à la publication** permet de spécifier les connexions et les groupes qui peuvent accéder à une publication.  
  
-   La page **Sécurité de l'agent** permet d'accéder aux paramètres des comptes sous lesquels les agents ci-après s'exécutent et se connectent aux ordinateurs d'une topologie de réplication : l'Agent d'instantané pour toutes les publications, l'Agent de lecture du journal pour toutes les publications transactionnelles et l'Agent de lecture de la file d'attente pour les publications transactionnelles qui autorisent les abonnements mis à jour en attente.  
  
-   La page **Partitions de données** (pour les publications de fusion provenant des serveurs de publication exécutant SQL Server 2005 ou version ultérieure) permet de spécifier si des Abonnés à des publications avec des filtres paramétrés peuvent demander un instantané si aucun n'est disponible. Elle permet de générer des instantanés pour une ou plusieurs partitions, soit au coup par coup, soit à intervalles récurrents.  
  
#### <a name="to-view-and-modify-article-properties"></a>Pour afficher et modifier les propriétés d'un article  
  
1.  Dans la page **Article**s de la boîte de dialogue **Propriétés de la Publication - \<Publication>** , sélectionnez un article, puis cliquez sur **Propriétés de l’article**.  
  
2.  Sélectionnez les articles auxquels les modifications des propriétés doivent s'appliquer :  
  
    -   Cliquez sur **Définir les propriétés de l’article de \<type_objet> en surbrillance** pour ouvrir la boîte de dialogue **Propriétés de l’article - \<nom_objet>** . Les modifications de propriétés apportées dans cette boîte de dialogue sont appliquées uniquement à l’objet en surbrillance dans le volet Objet de la page **Articles**.  
  
    -   Cliquez sur **Définir les propriétés de tous les articles \<type_objet>** pour ouvrir la boîte de dialogue **Propriétés pour tous les articles \<type_objet>** . Les modifications de propriétés apportées dans cette boîte de dialogue sont appliquées à tous les objets de ce type dans le volet Objet de la page **Articles**, notamment ceux qui ne sont pas encore sélectionnés pour la publication.  
  
        > [!NOTE]  
        >  Les modifications de propriétés apportées dans la boîte de dialogue **Propriétés pour tous les articles \<type_objet>** remplacent celles apportées dans la boîte de dialogue **Propriétés de l’article - \<nom_objet>** . Ainsi, si vous voulez définir un certain nombre de valeurs par défaut applicables à tous les articles d'un type d'objet mais souhaitez également définir des propriétés pour des objets spécifiques, vous devez d'abord définir les valeurs par défaut pour tous les articles. Définissez ensuite les propriétés des objets individuels.  
  
3.  Modifiez les propriétés si nécessaire, puis cliquez sur **OK**.  
  
4.  Dans la boîte de dialogue **Propriétés de la publication -** Publication> **, cliquez sur \<OK**.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
 Les articles peuvent être modifiés et leurs propriétés retournées, par programme, à l'aide des procédures stockées de réplication. Les procédures stockées utilisées dépendent du type de publication auquel l'article appartient.  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a>Pour afficher les propriétés d'un article appartenant à une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_helparticle](/sql/relational-databases/system-stored-procedures/sp-helparticle-transact-sql), en spécifiant le nom de la publication ** \@** pour le paramètre de publication et le nom de l' ** \@** article pour le paramètre de l’article. Si vous ne spécifiez ** \@pas l’article**, des informations sont retournées pour tous les Articles de la publication.  
  
2.  Exécutez [sp_helparticlecolumns](/sql/relational-databases/system-stored-procedures/sp-helparticlecolumns-transact-sql) pour les articles de table pour répertorier toutes les colonnes disponibles dans la table de base.  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-snapshot-or-transactional-publication"></a>Pour modifier les propriétés d'un article appartenant à une publication transactionnelle ou d'instantané  
  
1.  Exécutez [sp_changearticle](/sql/relational-databases/system-stored-procedures/sp-changearticle-transact-sql), en spécifiant la propriété d’article en ** \@** cours de modification dans le paramètre Property et la nouvelle valeur ** \@** de cette propriété dans le paramètre value.  
  
    > [!NOTE]  
    >  Si la modification nécessite la génération d’un nouvel instantané, vous devez également spécifier la valeur **1** pour ** \@force_invalidate_snapshot**, et si la modification nécessite la réinitialisation des abonnés, vous devez également spécifier la valeur **1** pour ** \@force_reinit_subscription**. Pour plus d’informations sur les propriétés qui, une fois modifiées, nécessitent un nouvel instantané ou une réinitialisation, consultez [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md).  
  
#### <a name="to-view-the-properties-of-an-article-belonging-to-a-merge-publication"></a>Pour afficher les propriétés d'un article appartenant à une publication de fusion  
  
1.  Exécutez [sp_helpmergearticle](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql), en spécifiant le nom de la publication ** \@** pour le paramètre de publication et le nom de l' ** \@** article pour le paramètre de l’article. Si vous ne spécifiez pas ces paramètres, des informations sont retournées pour tous les articles d'une publication ou sur l'Abonné.  
  
2.  Exécutez [sp_helpmergearticlecolumn](/sql/relational-databases/system-stored-procedures/sp-helpmergearticlecolumn-transact-sql) pour les articles de table pour répertorier toutes les colonnes disponibles dans la table de base.  
  
#### <a name="to-modify-the-properties-of-an-article-belonging-to-a-merge-publication"></a>Pour modifier les propriétés d'un article appartenant à une publication de fusion  
  
1.  Exécutez [sp_changemergearticle](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql), en spécifiant la propriété d’article en ** \@** cours de modification dans le paramètre Property et la nouvelle valeur ** \@** de cette propriété dans le paramètre value.  
  
    > [!NOTE]  
    >  Si la modification nécessite la génération d’un nouvel instantané, vous devez également spécifier la valeur **1** pour ** \@force_invalidate_snapshot**, et si la modification nécessite la réinitialisation des abonnés, vous devez également spécifier la valeur **1** pour ** \@force_reinit_subscription**. Pour plus d’informations sur les propriétés qui, une fois modifiées, nécessitent un nouvel instantané ou une réinitialisation, consultez [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md).  
  
###  <a name="example-transact-sql"></a><a name="TsqlExample"></a> Exemple (Transact-SQL)  
 Cet exemple de réplication transactionnelle retourne les propriétés de l'article publié.  
  
 [!code-sql[HowTo#sp_helptranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_helptranarticle)]  
  
 Cet exemple de réplication transactionnelle modifie les options de schéma pour l'article publié.  
  
 [!code-sql[HowTo#sp_changetranarticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changetranart.sql#sp_changetranarticle)]  
  
 Cet exemple de réplication de fusion retourne les propriétés de l'article publié.  
  
 [!code-sql[HowTo#sp_helpmergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_helpmergearticle)]  
  
 Cet exemple de réplication de fusion modifie les paramètres de détection de conflit pour un article publié.  
  
 [!code-sql[HowTo#sp_changemergearticle](../../../snippets/tsql/SQL15/replication/howto/tsql/changemergeart.sql#sp_changemergearticle)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> Utilisation d'objets RMO (Replication Management Objects)  
 Vous pouvez modifier des articles et accéder à leurs propriétés, par programme, en utilisant les objets RMO (Replication Management Objects). Les classes RMO à utiliser pour afficher ou modifier les propriétés d'un article dépendent du type de publication auquel l'article appartient.  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-snapshot-or-transactional-publication"></a>Pour afficher ou modifier les propriétés d'un article qui appartient à une publication transactionnelle ou d'instantané  
  
1.  Créez une connexion au serveur de publication en utilisant la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.TransArticle>.  
  
3.  Définissez les propriétés <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Définissez la connexion créée à l'étape 1 pour la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> pour obtenir les propriétés de l'objet. Si cette méthode retourne `false`, soit les propriétés de l'article ont été définies de manière incorrecte à l'étape 3, soit l'article n'existe pas.  
  
6.  (Facultatif) Pour modifier des propriétés, modifiez la valeur d'une des propriétés <xref:Microsoft.SqlServer.Replication.TransArticle> qui peuvent être définies.  
  
7.  (Facultatif) Si vous avez spécifié la valeur `true` pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> pour valider les modifications sur le serveur. Si vous avez spécifié la valeur `false` pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (valeur par défaut), les modifications sont envoyées immédiatement au serveur.  
  
#### <a name="to-view-or-modify-properties-of-an-article-that-belongs-to-a-merge-publication"></a>Pour afficher ou modifier les propriétés d'un article qui appartient à une publication de fusion  
  
1.  Créez une connexion au serveur de publication en utilisant la classe <xref:Microsoft.SqlServer.Management.Common.ServerConnection> .  
  
2.  Créez une instance de la classe <xref:Microsoft.SqlServer.Replication.MergeArticle>.  
  
3.  Définissez les propriétés <xref:Microsoft.SqlServer.Replication.Article.Name%2A>, <xref:Microsoft.SqlServer.Replication.Article.PublicationName%2A>et <xref:Microsoft.SqlServer.Replication.Article.DatabaseName%2A> .  
  
4.  Définissez la connexion créée à l'étape 1 pour la propriété <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> .  
  
5.  Appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> pour obtenir les propriétés de l'objet. Si cette méthode retourne `false`, soit les propriétés de l'article ont été définies de manière incorrecte à l'étape 3, soit l'article n'existe pas.  
  
6.  (Facultatif) Pour modifier des propriétés, modifiez la valeur d'une des propriétés <xref:Microsoft.SqlServer.Replication.MergeArticle> qui peuvent être définies.  
  
7.  (Facultatif) Si vous avez spécifié la valeur `true` pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A>, appelez la méthode <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> pour valider les modifications sur le serveur. Si vous avez spécifié la valeur `false` pour <xref:Microsoft.SqlServer.Replication.ReplicationObject.CachePropertyChanges%2A> (valeur par défaut), les modifications sont envoyées immédiatement au serveur.  
  
###  <a name="example-rmo"></a><a name="PShellExample"></a> Exemple (RMO)  
 Cet exemple modifie un article de fusion pour spécifier le gestionnaire de logique métier utilisé par l'article.  
  
 [!code-csharp[HowTo#rmo_ChangeMergeArticle_BLH](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_changemergearticle_blh)]  
  
 [!code-vb[HowTo#rmo_vb_ChangeMergeArticle_BLH](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_changemergearticle_blh)]  
  
## <a name="see-also"></a>Voir aussi  
 [Implémenter un gestionnaire de logique métier pour un article de fusion](../implement-a-business-logic-handler-for-a-merge-article.md)   
 [Publier des données et des objets de base de données](publish-data-and-database-objects.md)   
 [Changer les propriétés des publications et des articles](change-publication-and-article-properties.md)   
 [Concepts liés aux procédures stockées système de réplication](../concepts/replication-system-stored-procedures-concepts.md)   
 [Advanced Merge Replication Conflict Detection and Resolution](../merge/advanced-merge-replication-conflict-detection-and-resolution.md)  
  
  
