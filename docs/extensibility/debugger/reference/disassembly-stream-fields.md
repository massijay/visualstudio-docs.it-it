---
title: "DISASSEMBLY_STREAM_FIELDS | Microsoft Docs"
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
  - "DISASSEMBLY_STREAM_FIELDS"
helpviewer_keywords: 
  - "Enumerazione DISASSEMBLY_STREAM_FIELDS"
ms.assetid: cfc9b4de-c756-4844-bea7-d9f186a51d1b
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# DISASSEMBLY_STREAM_FIELDS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica le informazioni da recuperare su un campo di disassembly.  
  
## Sintassi  
  
```cpp#  
enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
typedef DWORD DISASSEMBLY_STREAM_FIELDS;  
```  
  
```c#  
public enum enum_DISASSEMBLY_STREAM_FIELDS {   
   DSF_ADDRESS          = 0x00000001,  
   DSF_ADDRESSOFFSET    = 0x00000002,  
   DSF_CODEBYTES        = 0x00000004,  
   DSF_OPCODE           = 0x00000008,  
   DSF_OPERANDS         = 0x00000010,  
   DSF_SYMBOL           = 0x00000020,  
   DSF_CODELOCATIONID   = 0x00000040,  
   DSF_POSITION         = 0x00000080,  
   DSF_DOCUMENTURL      = 0x00000100,  
   DSF_BYTEOFFSET       = 0x00000200,  
   DSF_FLAGS            = 0x00000400,  
   DSF_OPERANDS_SYMBOLS = 0x00010000,  
   DSF_ALL              = 0x000107ff  
};  
```  
  
## Membri  
 DSF\_ADDRESS  
 Inizializzare\/utilizzare il campo di `bstrAddress` .  
  
 DSF\_ADDRESSOFFSET  
 Inizializzare\/utilizzare il campo di `bstrAddressOffset` .  
  
 DSF\_CODEBYTES  
 Inizializzare\/utilizzare il campo di `bstrCodeBytes` .  
  
 DSF\_OPCODE  
 Inizializzare\/utilizzare il campo di `bstrOpCode` .  
  
 DSF\_OPERANDS  
 Inizializzare\/utilizzare il campo di `bstrOperands` .  
  
 DSF\_SYMBOL  
 Inizializzare\/utilizzare il campo di `bstrSymbol` .  
  
 DSF\_CODELOCATIONID  
 Inizializzare\/utilizzare il campo di `uCodeLocationId` .  
  
 DSF\_POSITION  
 Inizializzare\/utilizzare i campi di `posEnd` e di `posBeg` .  
  
 DSF\_DOCUMENTURL  
 Inizializzare\/utilizzare il campo di `bstrDocumentUrl` .  
  
 DSF\_BYTEOFFSET  
 Inizializzare\/utilizzare il campo di `dwByteOffset` .  
  
 DSF\_FLAGS  
 Inizializzare\/utilizzare il campo di `dwFlags` \([DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)\).  
  
 DSF\_OPERANDS\_SYMBOLS  
 Includere i nomi dei simboli nel campo di `bstrOperands` .  
  
 DSF\_ALL  
 Specifica tutti i campi per il flusso di disassembly.  
  
## Note  
 Passato come parametro [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) al metodo per indicare i campi [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) della struttura devono essere inizializzati.  
  
 Utilizzato per il membro di `dwFields` della struttura di `DisassemblyData` per indicare quali campi vengono utilizzati e valido quando la struttura viene restituita.  
  
 Questi valori possono essere combinate con `OR`bit per bit.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)   
 [Lettura](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)   
 [DISASSEMBLY\_FLAGS](../../../extensibility/debugger/reference/disassembly-flags.md)