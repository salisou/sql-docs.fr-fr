---
title: Créer un nouvel exemple de clé étrangère (VC + +) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- RelatedTable property [ADOX], VC++ example
- Key Type property [ADOX], VC++ example
- UpdateRule property [ADOX], VC++ example
- Append method [ADOX], VC++ example
- Keys Append method [ADOX], VC++ example
- RelatedColumn property [ADOX], VC++ example
ms.assetid: 28495b8f-18dc-482c-995d-a120f6ae2006
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c812f0503b8801e861364a04e5621cb975adb009
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "76918068"
---
# <a name="keys-append-method-key-type-relatedcolumn-relatedtable-and-updaterule-properties-example-vc"></a>Append (méthode) sur la collection Keys, Type de clé ; RelatedColumn, RelatedTable et UpdateRule, exemple de propriétés (VC++)
Le code suivant montre comment créer une nouvelle clé étrangère. Il suppose que deux tables (Customers et Orders) existent.  
  
```  
// BeginCreateKeyCpp.cpp  
// compile with: /EHsc  
#import "msado15.dll" rename("EOF", "EndOfFile")  
#import "msadox.dll" no_namespace  
  
#include "iostream"  
using namespace std;  
  
inline void TESTHR(HRESULT x) {if FAILED(x) _com_issue_error(x);};  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )   
      return -1;  
  
   HRESULT hr = S_OK;  
  
   // Define and initialize ADOX object pointers.  These are in ADODB namespace.  
   _KeyPtr m_pKeyForeign = NULL;   
   _CatalogPtr m_pCatalog = NULL;  
  
   // Define other variables  
   _bstr_t strcnn("Provider='Microsoft.JET.OLEDB.4.0';Data source = 'c:\\Northwind.mdb';");  
  
   try {  
      TESTHR(hr = m_pKeyForeign.CreateInstance(__uuidof(Key)));  
      TESTHR(hr = m_pCatalog.CreateInstance(__uuidof (Catalog)));  
      m_pCatalog->PutActiveConnection(strcnn);  
  
      // Define the foreign key.  
      m_pKeyForeign->Name = "CustOrder";  
      m_pKeyForeign->Type = adKeyForeign;  
      m_pKeyForeign->RelatedTable = "Customers";  
      m_pKeyForeign->Columns->Append("CustomerId",adVarWChar,0);  
      m_pKeyForeign->Columns->GetItem("CustomerId")->RelatedColumn = "CustomerId";  
      m_pKeyForeign->UpdateRule = adRICascade;  
  
      // To pass as column parameter to Key's Apppend method  
      _variant_t vOptional;  
      vOptional.vt = VT_ERROR;  
      vOptional.scode = DISP_E_PARAMNOTFOUND;  
  
      // Append the foreign key.  
      m_pCatalog->Tables->GetItem("Orders")->Keys->Append(_variant_t((IDispatch *)m_pKeyForeign),  
         adKeyPrimary,  
         vOptional,  
         L"",  
         L"");  
      printf("Foreign key 'CustOrder' is added.\n");  
  
      // Delete the key as this is a demonstration.  
      m_pCatalog->Tables->GetItem("Orders")->Keys->Delete(m_pKeyForeign->Name);  
      printf("Foreign key 'CustOrder' is deleted.\n");  
   }  
   catch(_com_error &e) {  
      // Notify the user of errors if any.  
      _bstr_t bstrSource(e.Source());  
      _bstr_t bstrDescription(e.Description());  
  
      printf("\n\tSource :  %s \n\tdescription : %s \n ", (LPCSTR)bstrSource, (LPCSTR)bstrDescription);  
   }  
  
   catch(...) {  
      cout << "Error occurred in include files...." << endl;  
   }  
   ::CoUninitialize();  
}  
```
