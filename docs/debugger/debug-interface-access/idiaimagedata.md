---
title: "IDiaImageData | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaImageData (interfaccia)"
ms.assetid: b696f350-fc08-4352-9287-a15e87512c1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaImageData
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Espone i dettagli relativi agli offset di base di memoria e sulla posizione del modulo o dell'immagine.  
  
## Sintassi  
  
```  
IDiaImageData : IUnknown  
```  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDiaImageData`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaImageData::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-relativevirtualaddress.md)|Recupera la posizione in memoria virtuale del modulo relativo all'applicazione.|  
|[IDiaImageData::get\_virtualAddress](../../debugger/debug-interface-access/idiaimagedata-get-virtualaddress.md)|Recupera la posizione in memoria virtuale dell'immagine.|  
|[IDiaImageData::get\_imageBase](../../debugger/debug-interface-access/idiaimagedata-get-imagebase.md)|Recupera la posizione di memoria in cui l'immagine deve essere basata.|  
  
## Note  
 Alcuni flussi di debug \(XDATA, PDATA\) contengono copie dei dati anche archiviati nell'immagine.  Questi oggetti dati del flusso è possibile eseguire una query per `IDiaImageData` interfaccia.  Vedere la sezione “note per i chiamanti„ in questo argomento per i dettagli.  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando `QueryInterface` su  [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) oggetto.  si noti che non tutti i flussi di debug supportano `IDiaImageData` interfaccia.  Ad esempio, attualmente i flussi di PDATA e solo di XDATA supportano `IDiaImageData` interfaccia.  
  
## Esempio  
 In questo esempio vengono ricercati tutti i flussi di debug del flusso che supporta `IDiaImageData` interfaccia.  Se tale flusso viene trovato, alcune informazioni relative al flusso visualizzare.  
  
```cpp#  
void ShowImageData(IDiaSession *pSession)  
{  
    if (pSession != NULL)  
    {  
        CComPtr<IDiaEnumDebugStreams> pStreamsList;  
        HRESULT hr;  
  
        hr = pSession->getEnumDebugStreams(&pStreamsList);  
        if (SUCCEEDED(hr))  
        {  
            LONG numStreams = 0;  
            hr = pStreamsList->get_Count(&numStreams);  
            if (SUCCEEDED(hr))  
            {  
                ULONG fetched = 0;  
                for (LONG i = 0; i < numStreams; i++)  
                {  
                    CComPtr<IDiaEnumDebugStreamData> pStream;  
                    hr = pStreamsList->Next(1,&pStream,&fetched);  
                    if (fetched == 1)  
                    {  
                        CComPtr<IDiaImageData> pImageData;  
                        hr = pStream->QueryInterface(__uuidof(IDiaImageData),  
                                                     (void **)&pImageData);  
                        if (SUCCEEDED(hr))  
                        {  
                            CComBSTR name;  
                            hr = pStream->get_name(&name);  
                            if (SUCCEEDED(hr))  
                            {  
                                wprintf(L"Stream %s:\n",(BSTR)name);  
                            }  
                            else  
                            {  
                                wprintf(L"Failed to get name of stream\n");  
                            }  
  
                            ULONGLONG imageBase = 0;  
                            if (pImageData->get_imageBase(&imageBase) == S_OK)  
                            {  
                                wprintf(L"  image base = 0x%0I64x\n",imageBase);  
                            }  
  
                            DWORD relVA = 0;  
                            if (pImageData->get_relativeVirtualAddress(&relVA) == S_OK)  
                            {  
                                wprintf(L"  relative virtual address = 0x%08lx\n",relVA);  
                            }  
  
                            ULONGLONG va = 0;  
                            if (pImageData->get_virtualAddress(&va) == S_OK)  
                            {  
                                wprintf(L"  virtual address = 0x%0I64x\n", va);  
                            }  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
```  
  
## Requisiti  
 intestazione: Dia2.h  
  
 raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)