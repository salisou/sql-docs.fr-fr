---
title: Spécification de fonctions de conversion explicite dans les requêtes XPath (SQLXML 4,0) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 43e7067f00e21f57d64f2206fb1008f21d77dd4b
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66010697"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a>Spécification de fonctions de conversion explicite dans les requêtes XPath (SQLXML 4.0)
  Les exemples suivants montrent comment les fonctions de conversion explicite sont spécifiées dans les requêtes XPath. Les requêtes XPath de ces exemples sont spécifiées par rapport au schéma de mappage contenu dans SampleSchema1.xml. Pour plus d’informations sur cet exemple de schéma, consultez [exemple de schéma XSD annoté pour les exemples XPath &#40;SQLXML 4,0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).  
  
## <a name="examples"></a>Exemples  
  
### <a name="a-use-the-number-explicit-conversion-function"></a>R. Utiliser la fonction de conversion explicite number()  
 La fonction `number()` convertit un argument en un nombre.  
  
 En supposant que la valeur de **ContactID** n’est pas numérique, la requête suivante convertit **ContactID** en nombre et le compare à la valeur 4. La requête retourne ensuite tous ** \<** les enfants de>élément du nœud de contexte avec l’attribut **ContactID** qui a une valeur numérique de 4 :  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 Il est possible de spécifier un raccourci vers l'axe `attribute` (@), et comme l'axe `child` est la valeur par défaut, il peut être absent de la requête :  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 En termes relationnels, la requête retourne un employé avec un **ContactID** de 4.  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Pour tester la requête XPath par rapport au schéma de mappage  
  
1.  Copiez l' [exemple de code de schéma](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom SampleSchema1.xml.  
  
2.  Créez le modèle suivant (ExplicitConversionA.xml) et enregistrez-le dans le même répertoire que SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleSchema1.xml) varie en fonction du répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Le jeu de résultats pour cette exécution de modèle est :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a>B. Utiliser la fonction de conversion explicite string()  
 La fonction `string()` convertit un argument en une chaîne.  
  
 La requête suivante convertit **ContactID** en une chaîne et le compare à la valeur de chaîne « 4 ». La requête retourne tous ** \<** les enfants de l’élément>d’un employé du nœud de contexte avec un **ContactID** avec une valeur de chaîne de « 4 » :  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 Il est possible de spécifier un raccourci vers l'axe `attribute` (@), et comme l'axe `child` est la valeur par défaut, il peut être absent de la requête :  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 Fonctionnellement, cette requête retourne les mêmes résultats que l'exemple de requête précédent, bien que l'évaluation soit effectuée contre une valeur de chaîne et non la valeur numérique (autrement dit, le nombre 4).  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a>Pour tester la requête XPath par rapport au schéma de mappage  
  
1.  Copiez l' [exemple de code de schéma](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) et collez-le dans un fichier texte. Enregistrez ce fichier sous le nom SampleSchema1.xml.  
  
2.  Créez le modèle suivant (ExplicitConversionB.xml) et enregistrez-le dans le même répertoire que SampleSchema1.xml.  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     Le chemin d'accès au répertoire spécifié pour le schéma de mappage (SampleSchema1.xml) varie en fonction du répertoire où le modèle est enregistré. Vous pouvez également spécifier un chemin d'accès absolu, par exemple :  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  Créez et utilisez le script de test SQLXML 4.0 (Sqlxml4test.vbs) pour exécuter le modèle.  
  
     Pour plus d’informations, consultez [utilisation d’ADO pour exécuter des requêtes SQLXML 4,0](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).  
  
 Voici le jeu de résultats de l'exécution du modèle :  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
