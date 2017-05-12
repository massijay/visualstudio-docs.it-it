---
title: "IActiveScriptSite::GetItemInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetItemInfo"
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetItemInfo
Consente al motore di scripting ottenere informazioni su un elemento aggiunto al metodo [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).  
  
## Sintassi  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### Parametri  
 `pstrName`  
 \[in\] il nome associato all'elemento, come specificato nel metodo [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).  
  
 `dwReturnMask`  
 \[in\] specifica della maschera di bit che informazioni sull'elemento che devono essere restituite.  Il motore di scripting deve richiedere la quantità di informazioni minima possibile perché alcuni dei parametri restituiti, ad esempio `ITypeInfo`\) possono richiedere molto tempo caricare o generare.  Può essere una combinazione dei valori seguenti:  
  
|Valore|Significato|  
|------------|-----------------|  
|SCRIPTINFO\_IUNKNOWN|Restituisce l'interfaccia `IUnknown` per l'elemento.|  
|SCRIPTINFO\_ITYPEINFO|Restituisce l'interfaccia `ITypeInfo` per l'elemento.|  
  
 `ppunkItem`  
 \[out\] l'indirizzo di una variabile che riceve un puntatore a un'interfaccia `IUnknown` associata all'elemento specificato.  Il motore di scripting può utilizzare il metodo `IUnknown::QueryInterface` per ottenere l'interfaccia `IDispatch` per l'elemento.  Questo parametro riceve NULL se `dwReturnMask` non include il valore di SCRIPTINFO\_IUNKNOWN.  Inoltre, riceve NULL se non esiste alcun oggetto associato al nome dell'elemento; questo meccanismo viene utilizzato per creare una classe semplice quando l'elemento denominato viene aggiunto al flag di SCRIPTITEM\_CODEONLY impostato nel metodo [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md).  
  
 `ppTypeInfo`  
 \[out\] l'indirizzo di una variabile che riceve un puntatore a un'interfaccia `ITypeInfo` associata all'elemento.  Questo parametro riceve NULL se `dwReturnMask` non include il valore di SCRIPTINFO\_ITYPEINFO, o se le informazioni sul tipo non sono disponibili per questo elemento.  Se le informazioni sul tipo non sono disponibili, l'oggetto non può originare gli eventi e l'associazione di nomi deve essere eseguita dal metodo `IDispatch::GetIDsOfNames`.  Si noti che l'interfaccia `ITypeInfo` viene recuperata la coclasse dell'elemento \(TKIND\_COCLASS\) perché l'oggetto può supportare più interfacce e le interfacce eventi.  Se l'elemento supporta l'interfaccia `IProvideMultipleTypeInfo`, l'interfaccia `ITypeInfo` recuperata è uguale a indice zero `ITypeInfo` che sarebbe ottenuto utilizzando il metodo `IProvideMultipleTypeInfo::GetInfoOfIndex`.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`TYPE_E_ELEMENTNOTFOUND`|Un elemento con il nome specificato non è stato trovato.|  
  
## Note  
 Questo metodo recupera solo le informazioni visualizzate dal parametro `dwReturnMask` ; ciò migliora le prestazioni.  Ad esempio, se di un'interfaccia `ITypeInfo` non è necessario per un elemento, non viene specificata semplicemente in `dwReturnMask`.  
  
## Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)