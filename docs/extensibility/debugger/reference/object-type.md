---
title: "OBJECT_TYPE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OBJECT_TYPE"
helpviewer_keywords: 
  - "Enumerazione OBJECT_TYPE"
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica il tipo di oggetto dall'analizzatore di espressioni.  
  
## Sintassi  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```c#  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## Membri  
 OBJECT\_TYPE\_BOOLEAN  
 Indicare che l'oggetto è un valore booleano.  
  
 OBJECT\_TYPE\_CHAR  
 Indica che l'oggetto sia un carattere.  
  
 OBJECT\_TYPE\_I1  
 Indicare che l'oggetto è un intero con segno di dati.  
  
 OBJECT\_TYPE\_U1  
 Indicare che l'oggetto è Unsigned Integer a dati.  
  
 OBJECT\_TYPE\_I2  
 Indicare che l'oggetto è un intero con segno a due byte.  
  
 OBJECT\_TYPE\_U2  
 Indicare che l'oggetto è un intero senza segno a due byte.  
  
 OBJECT\_TYPE\_I4  
 Indicare che l'oggetto è un intero con segno a quattro byte.  
  
 OBJECT\_TYPE\_U4  
 Indicare che l'oggetto è un intero senza segno a quattro byte.  
  
 OBJECT\_TYPE\_I8  
 Indicare che l'oggetto è un intero con segno del otto\-byte.  
  
 OBJECT\_TYPE\_U8  
 Indicare che l'oggetto è Unsigned Integer a otto\-byte.  
  
 OBJECT\_TYPE\_R4  
 Indicare che l'oggetto è un numero a virgola mobile a quattro byte.  
  
 OBJECT\_TYPE\_R8  
 Indicare che l'oggetto è un numero a virgola mobile del otto\-byte.  
  
 OBJECT\_TYPE\_OBJECT  
 Indica che l'oggetto sia un oggetto.  
  
 OBJECT\_TYPE\_NULL  
 Indicare che l'oggetto è NULL.  
  
 OBJECT\_TYPE\_CLASS  
 Indicare che l'oggetto è una classe.  
  
## Note  
 Passato come argomento [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) ai metodi e.  
  
## Requisiti  
 intestazione: ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)