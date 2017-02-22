---
title: "DISASSEMBLY_FLAGS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DISASSEMBLY_FLAGS"
helpviewer_keywords: 
  - "Enumerazione DISASSEMBLY_FLAGS"
ms.assetid: c1ec5a4d-5d42-4660-932c-7348550140cb
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DISASSEMBLY_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

specifica i flag per disassembly.  
  
## Sintassi  
  
```cpp#  
enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
typedef DWORD DISASSEMBLY_FLAGS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_FLAGS {   
   DF_DOCUMENTCHANGE     = 0x00000001,  
   DF_DISABLED           = 0x00000002,  
   DF_INSTRUCTION_ACTIVE = 0x00000004,  
   DF_DATA               = 0x00000008,  
   DF_HASSOURCE          = 0x00000010,  
   DF_DOCUMENT_CHECKSUM  = 0x00000020  
};  
```  
  
## Membri  
 DF\_DOCUMENTCHANGE  
 Indica che questa istruzione è in un documento diverso da quello precedente.  
  
 DF\_DISABLED  
 Indica che questa istruzione non verrà eseguita.  
  
 DF\_INSTRUCTION\_ACTIVE  
 Indica che questa istruzione è una delle istruzioni seguenti essere eseguita \(possono essere presenti più di uno\).  
  
 DF\_DATA  
 Indica che questa istruzione è effettivamente dati \(non codice.  
  
 DF\_HASSOURCE  
 indica che questa istruzione ha database di origine.  Alcune istruzioni, come codice di Garbage Collection o profilare, non dispongono di origine corrispondente.  
  
 DF\_DOCUMENT\_CHECKSUM  
 indica che il campo di `bstrDocumentUrl` contiene i dati di checksum dopo il documento URL.  Vedere la sezione relativa alle osservazioni per [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) la struttura per l'aggiornamento dei dati di checksum sono archiviati.  
  
## Note  
 Utilizzato come membro di `dwFlags` [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) della struttura.  
  
 Questi flag possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)