---
title: Fournisseur Microsoft OLE DB pour le service de Active Directory Microsoft | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADSI provider [ADO]
- Active Directory Service Interfaces provider [ADO]
- providers [ADO], OLE DB provider for Active Directory service
- OLE DB provider for Active Directory service [ADO]
ms.assetid: f9e81452-5675-4cfc-9949-cfbd2fe57534
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e204a4f6f7f395ca93198bc560f4a216d5a70673
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "67926675"
---
# <a name="microsoft-ole-db-provider-for-microsoft-active-directory-service"></a>Fournisseur Microsoft OLE DB pour le service Microsoft Active Directory
Le fournisseur ADSI (Active Directory Service Interfaces) permet à ADO de se connecter à des services d’annuaire hétérogènes par le biais d’ADSI. Cela donne aux applications ADO un accès en lecture seule aux services d’annuaire Microsoft Windows NT 4,0 et Microsoft Windows 2000, en plus des services d’annuaire compatibles LDAP et des services d’annuaire Novell. ADSI est basé sur un modèle de fournisseur, de sorte que si un nouveau fournisseur donne accès à un autre annuaire, l’application ADO peut y accéder en toute transparence. Le fournisseur ADSI est libre de thread et Unicode est activé.  
  
## <a name="connection-string-parameters"></a>Paramètres de chaîne de connexion  
 Pour vous connecter à ce fournisseur, définissez l’argument **Provider** de la propriété [ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md) sur ce qui suit :  
  
```vb
ADSDSOObject  
```  
  
 La lecture de la propriété [Provider](../../../ado/reference/ado-api/provider-property-ado.md) retourne également cette chaîne.  
  
## <a name="typical-connection-string"></a>Chaîne de connexion classique  
 Une chaîne de connexion classique pour ce fournisseur est la suivante :  
  
```vb
"Provider=ADSDSOObject;User ID=MyUserID;Password=MyPassword;"  
```  
  
 La chaîne se compose des mots clés suivants.  
  
|Mot clé|Description|  
|-------------|-----------------|  
|**Fournisseur**|Spécifie le fournisseur de OLE DB pour Active Directory Service.|  
|**ID d'utilisateur**|Spécifie le nom d'utilisateur. Si ce mot clé est omis, la connexion active est utilisée.|  
|**Mot de passe**|Spécifie le mot de passe de l’utilisateur. Si ce mot clé est omis. L’ouverture de session actuelle est alors utilisée.|  
  
> [!NOTE]
>  Si vous vous connectez à un fournisseur de sources de données qui prend en charge l’authentification Windows, vous devez spécifier **Trusted_Connection = Yes** ou **Integrated Security = SSPI** à la place des informations d’ID d’utilisateur et de mot de passe dans la chaîne de connexion.  
  
## <a name="command-text"></a>Texte de la commande  
 Une chaîne de texte de commande en quatre parties est reconnue par le fournisseur dans la syntaxe suivante :  
  
```vb
"Root; Filter; Attributes[; Scope]"  
```  
  
|Valeur|Description|  
|-----------|-----------------|  
|*Causes*|Indique l’objet **ADsPath** à partir duquel démarrer la recherche (c’est-à-dire la racine de la recherche).|  
|*Filter*|Indique le filtre de recherche au format RFC 1960.|  
|*Attributs*|Indique une liste d’attributs délimités par des virgules à retourner.|  
|*Étendue*|Facultatif. **Chaîne** qui spécifie la portée de la recherche. Il peut s’agir de l’un des éléments suivants :<br /><br /> -Base-recherche uniquement l’objet de base (racine de la recherche).<br />-OneLevel-Rechercher un seul niveau.<br />-Sous-arborescence-recherchez la sous-arborescence entière.|  
  
 Par exemple :  
  
```vb
"<LDAP://DC=ArcadiaBay,DC=COM>;(objectClass=*);sn, givenName; subtree"  
```  
  
 Le fournisseur prend également en charge SQL SELECT pour le texte de la commande. Par exemple :  
  
```vb
"SELECT title, telephoneNumber From 'LDAP://DC=Microsoft, DC=COM' WHERE   
objectClass='user' AND objectCategory='Person'"  
```  
  
## <a name="remarks"></a>Notes  
 Le fournisseur n’accepte pas les appels de procédure stockée ou les noms de tables simples (par exemple, la propriété [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md) sera toujours **adCmdText**). Pour une description plus complète des éléments de texte de la commande, consultez la documentation sur les interfaces de service Active Directory.  
  
## <a name="recordset-behavior"></a>Comportement du Recordset  
 Les tableaux suivants répertorient les fonctionnalités disponibles sur un objet [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) ouvert à l’aide de ce fournisseur. Seul le type de curseur statique (**adOpenStatic**) est disponible.  
  
 Pour plus d’informations sur le comportement du **Recordset** pour la configuration de votre fournisseur, exécutez la méthode [supports](../../../ado/reference/ado-api/supports-method.md) et Énumérez la collection [Properties](../../../ado/reference/ado-api/properties-collection-ado.md) du **Recordset** pour déterminer si des propriétés dynamiques spécifiques au fournisseur sont présentes.  
  
 **Disponibilité des propriétés standard du Recordset ADO :**  
  
|Propriété|Disponibilité|  
|--------------|------------------|  
|[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)|lecture/écriture|  
|[AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)|lecture/écriture|  
|[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)|en lecture seule|  
|[Business](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|en lecture seule|  
|[Signet](../../../ado/reference/ado-api/bookmark-property-ado.md)|lecture/écriture|  
|[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)|lecture/écriture|  
|[Ait](../../../ado/reference/ado-api/cursorlocation-property-ado.md)|toujours **adUseServer**|  
|[CursorType](../../../ado/reference/ado-api/cursortype-property-ado.md)|toujours **adOpenStatic**|  
|[EditMode](../../../ado/reference/ado-api/editmode-property.md)|toujours **adEditNone**|  
|[EOF](../../../ado/reference/ado-api/bof-eof-properties-ado.md)|en lecture seule|  
|[Filter](../../../ado/reference/ado-api/filter-property.md)|lecture/écriture|  
|[Verrou](../../../ado/reference/ado-api/locktype-property-ado.md)|lecture/écriture|  
|[MarshalOptions](../../../ado/reference/ado-api/marshaloptions-property-ado.md)|non disponible|  
|[MaxRecords](../../../ado/reference/ado-api/maxrecords-property-ado.md)|lecture/écriture|  
|[PageCount](../../../ado/reference/ado-api/pagecount-property-ado.md)|en lecture seule|  
|[PageSize](../../../ado/reference/ado-api/pagesize-property-ado.md)|lecture/écriture|  
|[RecordCount](../../../ado/reference/ado-api/recordcount-property-ado.md)|en lecture seule|  
|[Source](../../../ado/reference/ado-api/source-property-ado-recordset.md)|lecture/écriture|  
|[State](../../../ado/reference/ado-api/state-property-ado.md)|en lecture seule|  
|[État](../../../ado/reference/ado-api/status-property-ado-recordset.md)|en lecture seule|  
  
 **Disponibilité des méthodes de l’ensemble d’enregistrements ADO standard :**  
  
|Méthode|Disponible ?|  
|------------|----------------|  
|[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)|Non|  
|[Annuler](../../../ado/reference/ado-api/cancel-method-ado.md)|Non|  
|[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|Non|  
|[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)|Non|  
|[Clone](../../../ado/reference/ado-api/clone-method-ado.md)|Oui|  
|[Fermer](../../../ado/reference/ado-api/close-method-ado.md)|Oui|  
|[Supprimer](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|Non|  
|[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)|Oui|  
|[Déplacer](../../../ado/reference/ado-api/move-method-ado.md)|Oui|  
|[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|  
|[MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|  
|[MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|  
|[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)|Oui|  
|[NextRecordset](../../../ado/reference/ado-api/nextrecordset-method-ado.md)|Oui|  
|[Ouvrir](../../../ado/reference/ado-api/open-method-ado-recordset.md)|Oui|  
|[Requery](../../../ado/reference/ado-api/requery-method.md)|Oui|  
|[Resynchroniser](../../../ado/reference/ado-api/resync-method.md)|Oui|  
|[Permet](../../../ado/reference/ado-api/supports-method.md)|Oui|  
|[Mise à jour](../../../ado/reference/ado-api/update-method.md)|Non|  
|[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)|Non|  
  
 Pour plus d’informations sur ADSI et les spécificités du fournisseur, reportez-vous à la documentation des interfaces de service Active Directory ou visitez la page Web ADSI.  
  
## <a name="see-also"></a>Voir aussi  
 [CommandType, propriété (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [ConnectionString, propriété (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [Properties, collection (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [Provider, propriété (ADO)](../../../ado/reference/ado-api/provider-property-ado.md)   
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Supports, méthode](../../../ado/reference/ado-api/supports-method.md)
