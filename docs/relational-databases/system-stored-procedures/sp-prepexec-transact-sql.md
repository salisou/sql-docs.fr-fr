---
title: sp_prepexec (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_cursor_prepexec
- sp_cursor_prepexec_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_prepexec
ms.assetid: f9141850-a62b-43bf-8e46-b2f92b75ca56
author: stevestein
ms.author: sstein
ms.openlocfilehash: 670b64cb107610fe8b5506654b9e655b0da5fb16
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "68794718"
---
# <a name="sp_prepexec-transact-sql"></a>sp_prepexec (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  Prépare et exécute une [!INCLUDE[tsql](../../includes/tsql-md.md)] instruction paramétrable. sp_prepexec combine les fonctions de sp_prepare et de sp_execute. Cette action est appelée par ID = 13 dans un paquet tabular data stream (TDS).  
  
 ![Icône du lien de rubrique](../../database-engine/configure-windows/media/topic-link.gif "Icône du lien de rubrique") [Conventions de la syntaxe Transact-SQL](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
sp_prepexec handle OUTPUT, params , stmt  
    [ , bound param ] [ ,...n]]  
```  
  
## <a name="arguments"></a>Arguments  
 *traitée*  
 Identificateur [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de *handle* généré par. *handle* est un paramètre obligatoire avec une valeur de retour **int** .  
  
 *params*  
 Identifie des instructions paramétrables. La définition *params* des variables est substituée aux marqueurs de paramètres dans l’instruction. *params* est un paramètre obligatoire qui requiert une valeur d’entrée **ntext**, **nchar**ou **nvarchar** . Entrez une valeur NULL si l'instruction n'est pas paramétrable.  
  
 *Insert*  
 Définit le jeu de résultats de curseur. Le paramètre *stmt* est requis et appelle une valeur d’entrée **ntext**, **nchar**ou **nvarchar** .  
  
 *bound_param*  
 Indique l'utilisation facultative de paramètres supplémentaires. *bound_param* appelle une valeur d’entrée de n’importe quel type de données pour désigner les paramètres supplémentaires en cours d’utilisation.  
  
## <a name="examples"></a>Exemples  
 L’exemple suivant prépare et exécute une instruction simple :  
  
```  
Declare @Out int;  
EXEC sp_prepexec @Out output,   
    N'@P1 nvarchar(128), @P2 nvarchar(100)',  
    N'SELECT database_id, name  
      FROM sys.databases  
      WHERE name=@P1 AND state_desc = @P2',   
          @P1 = 'tempdb', @P2 = 'ONLINE';   
EXEC sp_unprepare @Out;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [sp_prepare &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-prepare-transact-sql.md)   
 [sp_execute &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-execute-transact-sql.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
