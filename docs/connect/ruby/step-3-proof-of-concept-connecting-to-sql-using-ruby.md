---
title: 'Étape 3 : Preuve de concept pour la connexion à SQL avec Ruby | Microsoft Docs'
ms.custom: ''
ms.date: 08/08/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: cac20b18-0a6d-4243-bbda-a5d1b9476441
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 10ff3f651695b172396b89dc7de97d62a2824e84
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80926721"
---
# <a name="step-3-proof-of-concept-connecting-to-sql-using-ruby"></a>Étape 3 : Preuve de concept pour se connecter à SQL à l’aide de Ruby

Cet exemple être considéré comme une preuve de concept uniquement.  L’exemple de code est simplifié par souci de clarté et ne représente pas nécessairement les meilleures pratiques recommandées par Microsoft.  
  
## <a name="step-1--connect"></a>Étape 1 :  Se connecter  
  
La fonction [TinyTDS::Client](https://github.com/rails-sqlserver/tiny_tds) permet de se connecter à Base de données SQL.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
```  
  
## <a name="step-2--execute-a-query"></a>Étape 2 :  Exécuter une requête  
  
Copiez et collez le code suivant dans un fichier vide. Nommez ce fichier test.rb. Puis exécutez-le en entrant la commande suivante à partir de l’invite de commandes :  
  
    ruby test.rb  
  
Dans l’exemple de code, la fonction [TinyTds::Result](https://github.com/rails-sqlserver/tiny_tds) permet de récupérer un jeu de résultats d’une requête effectuée dans la base de données SQL. Cette fonction accepte une requête et retourne un jeu de résultats. Une itération est effectuée sur le jeu de résultats en utilisant [result.each do |row|](https://github.com/rails-sqlserver/tiny_tds).  
  
``` ruby 
    require 'tiny_tds'    
    print 'test'       
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SELECT c.CustomerID, c.CompanyName,COUNT(soh.SalesOrderID) AS OrderCount FROM SalesLT.Customer AS c LEFT OUTER JOIN SalesLT.SalesOrderHeader AS soh ON c.CustomerID = soh.CustomerID GROUP BY c.CustomerID, c.CompanyName ORDER BY OrderCount DESC")  
    results.each do |row|  
    puts row  
    end  
```  
  
## <a name="step-3--insert-a-row"></a>Étape 3 :  Insérer une ligne  
  
Dans cet exemple, vous allez découvrir comment exécuter une instruction [INSERT](../../t-sql/statements/insert-transact-sql.md) en toute sécurité, passer des paramètres pour protéger votre application de la valeur [Injection SQL](../../relational-databases/tables/primary-and-foreign-key-constraints.md).    
  
Pour utiliser TinyTDS avec Azure, il est recommandé d’exécuter plusieurs instructions `SET` pour modifier la façon dont la session en cours gère des informations spécifiques. Les instructions `SET` recommandées sont fournies dans l’exemple de code. Par exemple, `SET ANSI_NULL_DFLT_ON` permet aux nouvelles colonnes créées d’autoriser les valeurs Null même si la possibilité d’utiliser ces valeurs dans ces colonnes n’est pas explicitement définie.  
  
Pour être en harmonie avec le format [datetime](../../t-sql/data-types/datetime-transact-sql.md) (date et heure) de Microsoft SQL Server, utilisez la fonction [strftime](https://ruby-doc.org/core-2.2.0/Time.html#method-i-strftime) pour effectuer une conversion au format datetime correspondant.  
  
``` ruby
    require 'tiny_tds'  
    client = TinyTds::Client.new username: 'yourusername@yourserver', password: 'yourpassword',  
    host: 'yourserver.database.windows.net', port: 1433,  
    database: 'AdventureWorks', azure:true  
    results = client.execute("SET ANSI_NULLS ON")  
    results = client.execute("SET CURSOR_CLOSE_ON_COMMIT OFF")  
    results = client.execute("SET ANSI_NULL_DFLT_ON ON")  
    results = client.execute("SET IMPLICIT_TRANSACTIONS OFF")  
    results = client.execute("SET ANSI_PADDING ON")  
    results = client.execute("SET QUOTED_IDENTIFIER ON")  
    results = client.execute("SET ANSI_WARNINGS ON")  
    results = client.execute("SET CONCAT_NULL_YIELDS_NULL ON")  
    require 'date'  
    t = Time.now  
    curr_date = t.strftime("%Y-%m-%d %H:%M:%S.%L")  
    results = client.execute("INSERT SalesLT.Product (Name, ProductNumber, StandardCost, ListPrice, SellStartDate)  
    OUTPUT INSERTED.ProductID VALUES ('SQL Server Express New', 'SQLEXPRESS New', 0, 0, '#{curr_date}' )")  
    results.each do |row|  
    puts row  
    end  
```
