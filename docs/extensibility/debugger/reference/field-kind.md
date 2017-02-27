---
title: "FIELD_KIND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_KIND"
helpviewer_keywords: 
  - "Enumerazione FIELD_KIND"
ms.assetid: fd522b9c-52e2-42fa-939d-343347d5c3b1
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# FIELD_KIND
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

specifica il tipo di campo contenuto [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) in un oggetto.  
  
## Sintassi  
  
```cpp#  
enum enum_FIELD_KIND {   
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
typedef DWORD FIELD_KIND;  
```  
  
```c#  
public enum enum_FIELD_KIND {  
   FIELD_KIND_NONE       = 0x00000000,  
  
   // Type of field  
   FIELD_KIND_TYPE       = 0x00000001,  
   FIELD_KIND_SYMBOL     = 0x00000002,  
  
   // Storage type of the field  
   FIELD_TYPE_PRIMITIVE  = 0x00000010,  
   FIELD_TYPE_STRUCT     = 0x00000020,  
   FIELD_TYPE_CLASS      = 0x00000040,  
   FIELD_TYPE_INTERFACE  = 0x00000080,  
   FIELD_TYPE_UNION      = 0x00000100,  
   FIELD_TYPE_ARRAY      = 0x00000200,  
   FIELD_TYPE_METHOD     = 0x00000400,  
   FIELD_TYPE_BLOCK      = 0x00000800,  
   FIELD_TYPE_POINTER    = 0x00001000,  
   FIELD_TYPE_ENUM       = 0x00002000,  
   FIELD_TYPE_LABEL      = 0x00004000,  
   FIELD_TYPE_TYPEDEF    = 0x00008000,  
   FIELD_TYPE_BITFIELD   = 0x00010000,  
   FIELD_TYPE_NAMESPACE  = 0x00020000,  
   FIELD_TYPE_MODULE     = 0x00040000,  
   FIELD_TYPE_DYNAMIC    = 0x00080000,  
   FIELD_TYPE_PROP       = 0x00100000,  
   FIELD_TYPE_INNERCLASS = 0x00200000,  
   FIELD_TYPE_REFERENCE  = 0x00400000,  
   FIELD_TYPE_EXTENDED   = 0x00800000,  
  
   // Specific information about symbols  
   FIELD_SYM_MEMBER      = 0x01000000,  
   FIELD_SYM_LOCAL       = 0x02000000,  
   FIELD_SYM_PARAM       = 0x04000000,  
   FIELD_SYM_THIS        = 0x08000000,  
   FIELD_SYM_GLOBAL      = 0x10000000,  
   FIELD_SYM_PROP_GETTER = 0x20000000,  
   FIELD_SYM_PROP_SETTER = 0x40000000,  
   FIELD_SYM_EXTENDED    = 0x80000000,  
  
   FIELD_KIND_MASK       = 0x0000000f,  
   FIELD_TYPE_MASK       = 0x00fffff0,  
   FIELD_SYM_MASK        = 0xff000000,  
  
   FIELD_KIND_ALL        = 0xffffffff  
};  
```  
  
## Membri  
 FIELD\_KIND\_TYPE  
 Indica che il campo è un tipo solo.  
  
 FIELD\_KIND\_SYMBOL  
 Indica che il campo è un simbolo, con tipo, nome e altre informazioni.  
  
 FIELD\_TYPE\_PRIMITIVE  
 indica che il campo è un tipo di dati primitivo.  
  
 FIELD\_TYPE\_STRUCT  
 indica che il campo è una struttura.  
  
 FIELD\_TYPE\_CLASS  
 Indica che il campo è una classe.  
  
 FIELD\_TYPE\_INTERFACE  
 indica che il campo è un'interfaccia.  
  
 FIELD\_TYPE\_UNION  
 indica che il campo è un'unione.  
  
 FIELD\_TYPE\_ARRAY  
 indica che il campo è una matrice.  
  
 FIELD\_TYPE\_METHOD  
 indica che il campo è un metodo.  
  
 FIELD\_TYPE\_BLOCK  
 indica che il campo è un blocco.  
  
 FIELD\_TYPE\_POINTER  
 indica che il campo è un puntatore.  
  
 FIELD\_TYPE\_ENUM  
 indica che il campo è un tipo di dati enumerato.  
  
 FIELD\_TYPE\_LABEL  
 Indica che il campo sia un'etichetta.  
  
 FIELD\_TYPE\_TYPEDEF  
 indica che il campo è un typedef.  
  
 FIELD\_TYPE\_BITFIELD  
 indica che il campo è un campo di bit.  
  
 FIELD\_TYPE\_NAMESPACE  
 Indica che il campo è uno spazio dei nomi.  
  
 FIELD\_TYPE\_MODULE  
 indica che il campo è un modulo.  
  
 FIELD\_TYPE\_DYNAMIC  
 indica che il campo è dinamico.  
  
 FIELD\_TYPE\_PROP  
 indica che il campo è una proprietà.  
  
 FIELD\_TYPE\_INNERCLASS  
 indica che il campo è una classe interna.  
  
 FIELD\_TYPE\_REFERENCE  
 indica che il campo è un riferimento.  
  
 FIELD\_TYPE\_EXTENDED  
 Riservato per un utilizzo futuro.  
  
 FIELD\_SYM\_MEMBER  
 indica che il campo è un membro.  
  
 FIELD\_SYM\_LOCAL  
 indica che il campo è locale.  
  
 FIELD\_SYM\_PARAMETER  
 indica che il campo è un parametro.  
  
 FIELD\_SYM\_THIS  
 Indica che il campo è “this„ puntatore.  
  
 FIELD\_SYM\_GLOBAL  
 indica che il campo è globale.  
  
 FIELD\_SYM\_PROP\_GETTER  
 indica che il campo recupera le proprietà.  
  
 FIELD\_SYM\_PROP\_SETTER  
 indica che il campo imposta le proprietà.  
  
 FIELD\_SYM\_EXTENDED  
 Riservato per un utilizzo futuro.  
  
 FIELD\_KIND\_MASK  
 Indica una maschera per i tipi di campo.  
  
 FIELD\_TYPE\_MASK  
 indica una maschera per i tipi di campo.  
  
 FIELD\_SYM\_MASK  
 Indica una maschera per informazioni sui simboli.  
  
## Note  
 Restituito da una chiamata [GetKind](../Topic/IDebugField::GetKind.md) al metodo.  
  
 A seconda del tipo di campo, [QueryInterface](/visual-cpp/atl/queryinterface) può essere chiamata [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) perinterfaccia per un form più specifico dell'interfaccia.  Ad esempio, se [GetKind](../Topic/IDebugField::GetKind.md) restituisce `FIELD_TYPE_METHOD`, è possibile chiamare `QueryInterface` su I`DebugField` per [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) ottenere l'interfaccia.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetKind](../Topic/IDebugField::GetKind.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)