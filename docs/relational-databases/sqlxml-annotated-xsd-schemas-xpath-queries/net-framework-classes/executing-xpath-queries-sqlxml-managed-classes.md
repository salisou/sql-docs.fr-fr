---
title: Exécution de requêtes XPath (SQLXML)
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], SQLXML Managed Classes
- queries [SQLXML], SQLXML Managed Classes
- Managed Classes [SQLXML], executing XPath queries
- mapping schema [SQLXML], XPath queries
- SQLXML Managed Classes, executing XPath queries
ms.assetid: 8bef4c4d-bf0e-4236-a875-fd7d3e058396
author: MightyPen
ms.author: genemi
ms.custom: seo-lt-2019
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 999ab1ad269b32c0e02cff2fb143777dc1e2e24a
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "75244338"
---
# <a name="executing-xpath-queries-sqlxml-managed-classes"></a>Exécution de requêtes XPath (classes managées SQLXML)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  Cet exemple illustre la façon dont les requêtes XPath sont exécutées sur un schéma de mappage.  
  
 Examinez ce schéma :  
  
```  
<xsd:schema xmlns:xsd="http://www.w3.org/2001/XMLSchema"  
            xmlns:sql="urn:schemas-microsoft-com:mapping-schema">  
  <xsd:element name="Con" sql:relation="Person.Contact" >  
   <xsd:complexType>  
     <xsd:sequence>  
        <xsd:element name="FName"    
                     sql:field="FirstName"   
                     type="xsd:string" />   
        <xsd:element name="LName"    
                     sql:field="LastName"    
                     type="xsd:string" />  
     </xsd:sequence>  
     <xsd:attribute name="ContactID" type="xsd:integer" />  
    </xsd:complexType>  
  </xsd:element>  
</xsd:schema>  
```  
  
 Cette application C# exécute une requête XPath sur ce schéma (MySchema.xml).  
  
> [!NOTE]  
>  Dans le code, vous devez fournir le nom de l'instance de Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] dans la chaîne de connexion.  
  
```  
using System;  
using Microsoft.Data.SqlXml;  
using System.IO;  
class Test  
{  
      static string ConnString = "Provider=SQLOLEDB;Server=(local);database=AdventureWorks;Integrated Security=SSPI";  
  
      public static int testXPath()  
      {  
         Stream strm;  
         SqlXmlCommand cmd = new SqlXmlCommand(ConnString);  
         cmd.CommandText = "Con";  
         cmd.CommandType = SqlXmlCommandType.XPath;  
         cmd.RootTag = "ROOT";  
         cmd.SchemaPath = "MySchema.xml";  
         strm = cmd.ExecuteStream();  
         using (StreamReader sr = new StreamReader(strm)){  
            Console.WriteLine(sr.ReadToEnd());  
         }  
         return 0;  
      }  
      public static int Main(String[] args)  
      {  
         testXPath();  
         return 0;  
      }  
   }  
```  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1.  Assurez-vous que le [!INCLUDE[msCoName](../../../includes/msconame-md.md)] .NET Framework est installé sur votre ordinateur.  
  
2.  Enregistrez dans un dossier le schéma XSD (MySchema.xml) fourni dans cet exemple.  
  
3.  Enregistrez le code C# (DocSample.cs) fourni dans cet exemple dans le même dossier que celui dans lequel le schéma est stocké. (Si vous stockez les fichiers dans un dossier différent, vous devrez modifier le code et spécifier le chemin d'accès approprié au répertoire pour le schéma de mappage.)  
  
4.  Compilez le code. Pour compiler le code à l'invite de commandes, utilisez :  
  
    ```  
    csc /reference:Microsoft.Data.SqlXML.dll DocSample.cs  
    ```  
  
     Un fichier exécutable (DocSample.exe) est alors créé.  
  
5.  À l'invite de commandes, exécutez DocSample.exe.  
  
  
