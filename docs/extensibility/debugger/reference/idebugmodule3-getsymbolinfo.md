---
title: "IDebugModule3::GetSymbolInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule3::GetSymbolInfo"
helpviewer_keywords: 
  - "Metodo GetSymbolInfo"
  - "Metodo IDebugModule3::GetSymbolInfo"
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un elenco di percorsi in cui vengono ricercati i simboli, nonché i risultati di ogni percorso di ricerca.  
  
## Sintassi  
  
```cpp#  
HRESULT GetSymbolInfo(  
   SYMBOL_SEARCH_INFO_FIELDS  dwFields,  
   MODULE_SYMBOL_SEARCH_INFO* pInfo  
);  
```  
  
```c#  
int GetSymbolInfo(  
   enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,   
   MODULE_SYMBOL_SEARCH_INFO[]    pinfo  
);  
  
```  
  
#### Parametri  
 `dwFields`  
 \[in\] Una combinazione di flag dal [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumerazione che specifica quali campi di `pInfo` deve essere compilata.  
  
 `pInfo`  
 \[out\] Oggetto [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) struttura i cui membri sono da riempire con le informazioni specificate. Se questo è un valore null, questo metodo restituisce `E_INVALIDARG`.  
  
## Valore restituito  
 Se il metodo ha esito positivo, restituisce `S_OK`; in caso contrario, viene restituito un codice di errore.  
  
> [!NOTE]
>  La stringa restituita \(nel `MODULE_SYMBOL_SEARCH_INFO` struttura\) potrebbe essere vuoto se `S_OK` viene restituito. In questo caso, si è verificato alcun informazioni di ricerca da restituire.  
  
## Note  
 Se il `bstrVerboseSearchInfo` campo di `MODULE_SYMBOL_SEARCH_INFO` struttura non è vuota, quindi contiene un elenco di percorsi di ricerca e i risultati della ricerca. L'elenco viene formattato con un percorso, seguito da puntini di sospensione \("..."\), seguite dal risultato. Se è presente più di una coppia di risultati di percorso, ogni coppia è separato da una coppia di "\\r\\n" \(ritorno a capo\-ritorno\/avanzamento riga\). Il modello è simile al seguente:  
  
 \< percorso \>... \< risultato \> \\r\\n \< percorso \>... \< risultato \> \\r\\n \< percorso \>... \< risultato \>  
  
 Si noti che l'ultima voce non dispone di una sequenza \\r\\n.  
  
## Esempio  
 In questo esempio, questo metodo restituisce tre percorsi con i tre risultati diversi. Ogni riga viene terminata con una coppia di ritorno a capo ritorno avanzamento riga. L'output di esempio consente di stampare solo i risultati della ricerca come un'unica stringa.  
  
> [!NOTE]
>  Un risultato di stato è tutto quello che segue immediatamente il "..." fino alla fine della riga.  
  
```cpp#  
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)  
{  
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };  
    HRESULT hr;  
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);  
    if (SUCCEEDED(hr)) {  
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;  
        if (searchInfo.Length() != 0) {  
            std::wcout << (wchar_t *)(BSTR)searchInfo;  
            std::wcout << std::endl;  
        }  
    }  
}  
```  
  
 **c:\\symbols\\user32.pdb... File non trovato. c:\\winnt\\symbols\\user32.pdb... Versione non corrisponde. \\\\symbols\\symbols\\user32.dll\\0a8sd0ad8ad\\user32.pdb... Caricare i simboli.**   
## Vedere anche  
 [SYMBOL\_SEARCH\_INFO\_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)