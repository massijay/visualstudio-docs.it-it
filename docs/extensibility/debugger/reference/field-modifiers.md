---
title: "FIELD_MODIFIERS | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FIELD_MODIFIERS"
helpviewer_keywords: 
  - "Enumerazione FIELD_MODIFIERS"
ms.assetid: 1e44681c-1f03-41a9-9c04-b79f231b0822
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# FIELD_MODIFIERS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Specifica i modificatori di un tipo di campo.  
  
## Sintassi  
  
```cpp#  
enum enum_FIELD_MODIFIERS {   
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
typedef DWORD FIELD_MODIFIERS;  
```  
  
```c#  
public enum enum_FIELD_MODIFIERS {  
   FIELD_MOD_NONE             = 0x00000000,  
  
   // Modifier of the field  
   FIELD_MOD_ACCESS_NONE      = 0x00000001,  
   FIELD_MOD_ACCESS_PUBLIC    = 0x00000002,  
   FIELD_MOD_ACCESS_PROTECTED = 0x00000004,  
   FIELD_MOD_ACCESS_PRIVATE   = 0x00000008,  
  
   // Storage modifier of the field  
   FIELD_MOD_NOMODIFIERS      = 0x00000010,  
   FIELD_MOD_STATIC           = 0x00000020,  
   FIELD_MOD_CONSTANT         = 0x00000040,  
   FIELD_MOD_TRANSIENT        = 0x00000080,  
   FIELD_MOD_VOLATILE         = 0x00000100,  
   FIELD_MOD_ABSTRACT         = 0x00000200,  
   FIELD_MOD_NATIVE           = 0x00000400,  
   FIELD_MOD_SYNCHRONIZED     = 0x00000800,  
   FIELD_MOD_VIRTUAL          = 0x00001000,  
   FIELD_MOD_INTERFACE        = 0x00002000,  
   FIELD_MOD_FINAL            = 0x00004000,  
   FIELD_MOD_SENTINEL         = 0x00008000,  
   FIELD_MOD_INNERCLASS       = 0x00010000,  
   FIELD_TYPE_OPTIONAL        = 0x00020000,  
   FIELD_MOD_BYREF            = 0x00040000,  
   FIELD_MOD_HIDDEN           = 0x00080000,  
   FIELD_MOD_MARSHALASOBJECT  = 0x00100000,  
   FIELD_MOD_SPECIAL_NAME     = 0x00200000,  
   FIELD_MOD_HIDEBYSIG        = 0x00400000,  
  
   FIELD_MOD_WRITEONLY        = 0x80000000,  
   FIELD_MOD_ACCESS_MASK      = 0x000000ff,  
   FIELD_MOD_MASK             = 0xffffff00,  
   FIELD_MOD_ALL              = 0x7fffffff  
};  
```  
  
## Membri  
 FIELD\_MOD\_ACCESS\_TYPE  
 Indica che il campo non è possibile accedervi.  
  
 FIELD\_MOD\_ACCESS\_PUBLIC  
 indica che il campo ha accesso pubblico.  
  
 FIELD\_MOD\_ACCESS\_PROTECTED  
 indica che il campo ha accesso protetto.  
  
 FIELD\_MOD\_ACCESS\_PRIVATE  
 indica che il campo ha accesso privato.  
  
 FIELD\_MOD\_NOMODIFIERS  
 Indica che il campo non possiede modificatori.  
  
 FIELD\_MOD\_STATIC  
 indica che il campo è statico.  
  
 FIELD\_MOD\_CONSTANT  
 indica che il campo è una costante.  
  
 FIELD\_MOD\_TRANSIENT  
 indica che il campo è temporaneo.  
  
 FIELD\_MOD\_VOLATILE  
 indica che il campo è volatile.  
  
 FIELD\_MOD\_ABSTRACT  
 indica che il campo è astratto.  
  
 FIELD\_MOD\_NATIVE  
 indica che il campo è nativo.  
  
 FIELD\_MOD\_SYNCHRONIZED  
 indica che il campo è sincronizzato.  
  
 FIELD\_MOD\_VIRTUAL  
 indica che il campo è virtuale.  
  
 FIELD\_MOD\_INTERFACE  
 indica che il campo è un'interfaccia.  
  
 FIELD\_MOD\_FINAL  
 indica che il campo è finale.  
  
 FIELD\_MOD\_SENTINEL  
 Indica che il campo è una sentinel.  
  
 FIELD\_MOD\_INNERCLASS  
 indica che il campo è una classe interna.  
  
 FIELD\_TYPE\_OPTIONAL  
 indica che il campo è facoltativo.  
  
 FIELD\_MOD\_BYREF  
 indica che il campo è un argomento di riferimento.  Ciò è specificamente per gli argomenti del metodo.  
  
 FIELD\_MOD\_HIDDEN  
 Indica che il campo deve essere nascosto o presentato in un altro contesto, ad esempio, locali statico di [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .  
  
 FIELD\_MOD\_MARSHALASOBJECT  
 indica che il campo rappresenta un oggetto con un'interfaccia di `IUnknown` .  
  
 FIELD\_MOD\_SPECIAL\_NAME  
 Indica che il campo dispone di un nome speciale, ad esempio, `.ctor` per un costruttore \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] solo\).  
  
 FIELD\_MOD\_HIDEBYSIG  
 Indica che il campo contiene la parola chiave di `Overloads` applicata a \([!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] solo\).  
  
 FIELD\_MOD\_WRITEONLY  
 indica che il campo è di sola scrittura.  Questo valore non è incluso in `FIELD_MOD_ALL`, poiché il solo utilizzo di tali campi di sola scrittura è per la valutazione della funzione.  Un utente deve esplicitamente porre i campi di `FIELD_MOD_WRITEONLY` .  
  
 FIELD\_MOD\_ACCESS\_MASK  
 Indica una maschera di accesso del campo.  
  
 FIELD\_MOD\_MASK  
 Indica una maschera per i modificatori del campo.  
  
## Note  
 Utilizzato per il membro di `dwModifiers` [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md) della struttura.  
  
 Questi valori vengono passati [EnumFields](../Topic/IDebugContainerField::EnumFields.md) al metodo al filtro per i campi specifici.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)   
 [EnumFields](../Topic/IDebugContainerField::EnumFields.md)