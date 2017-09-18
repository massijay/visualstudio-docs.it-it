---
title: "IDebugDocumentText2::GetText | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2::GetText"
helpviewer_keywords: 
  - "IDebugDocumentText2::GetText"
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugDocumentText2::GetText
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera il testo nella posizione specificata nel documento.  
  
## Sintassi  
  
```cpp#  
HRESULT GetText(   
   TEXT_POSITION pos,  
   ULONG         cMaxChars,  
   WCHAR*        pText,  
   ULONG*        pcNumChars  
);  
```  
  
```c#  
int GetText(   
   eumn_TEXT_POSITION pos,  
   uint               cMaxChars,  
   IntPtr             pText,  
   out uint           pcNumChars  
);  
```  
  
#### Parametri  
 `pos`  
 \[in\]  [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) Una struttura che indica la posizione del testo da recuperare.  
  
 `cMaxChars`  
 \[in\]  Il numero massimo di caratteri del testo da recuperare.  
  
 `pText`  
 \[in, out\]  Un puntatore a un buffer che sia compilato con testo desiderato.  Questo buffer deve essere in grado di contenere almeno il numero di `cMaxChars` i caratteri di tipo " wide ".  
  
 `pcNumChars`  
 \[out\]  Restituisce il numero di caratteri in realtà recuperato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Esempio  
 In questo esempio viene illustrato come questo metodo può essere chiamato da c\#.  
  
```c#  
using System.Runtime.Interop.Services;  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Debugger.Interop;  
  
namespace Mynamespace  
{  
    class MyClass  
    {  
         string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)  
        {  
             string documentText = string.Empty;  
             if (pText != null)  
             {  
                  uint numLines = 0;  
                  uint numChars = 0;  
                  int hr;  
                  hr = pText.GetSize(ref numLines, ref numChars);  
                  if (ErrorHandler.Succeeded(hr))  
                  {  
                       IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));  
                       uint actualChars = 0;  
                       hr = pText.GetText(pos, numChars, buffer, out actualChars);  
                       if (ErrorHandler.Succeeded(hr))  
                       {  
                            documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);  
                       }  
                       Marshal.FreeCoTaskMem(buffer);  
                  }  
              }  
              return documentText;  
         }  
    }  
}  
```  
  
## Vedere anche  
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)