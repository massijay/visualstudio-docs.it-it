---
title: "DBG_ATTRIB_FLAGS | Microsoft Docs"
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
  - "DBG_ATTRIB_FLAGS"
helpviewer_keywords: 
  - "Enumerazioni DBGPROP_ATTRIB_FLAGS"
ms.assetid: 2f13e601-dadc-476e-a8ec-01c4515082e7
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# DBG_ATTRIB_FLAGS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Vengono descritti i vari attributi per [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) un'interfaccia o [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) .  Membro [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md) della struttura.  
  
## Sintassi  
  
```cpp#  
#define DBG_ATTRIB_NONE                 0x0000000000000000,  
#define DBG_ATTRIB_ALL                  0x00000000ffffffff,  
  
// Attributes about the object itself  
  
#define DBG_ATTRIB_OBJ_IS_EXPANDABLE    0x0000000000000001,  
#define DBG_ATTRIB_OBJ_HAS_ID           0x0000000000000002,  
#define DBG_ATTRIB_OBJ_CAN_HAVE_ID      0x0000000000000004,  
  
// Attributes about the value of the object  
  
#define DBG_ATTRIB_VALUE_READONLY       0x0000000000000010,  
#define DBG_ATTRIB_VALUE_ERROR          0x0000000000000020,  
#define DBG_ATTRIB_VALUE_SIDE_EFFECT    0x0000000000000040,  
#define DBG_ATTRIB_OVERLOADED_CONTAINER 0x0000000000000080,  
#define DBG_ATTRIB_VALUE_BOOLEAN        0x0000000000000100,  
#define DBG_ATTRIB_VALUE_BOOLEAN_TRUE   0x0000000000000200,  
#define DBG_ATTRIB_VALUE_INVALID        0x0000000000000400,  
#define DBG_ATTRIB_VALUE_NAT            0x0000000000000800,  
#define DBG_ATTRIB_VALUE_AUTOEXPANDED   0x0000000000001000,  
#define DBG_ATTRIB_VALUE_TIMEOUT        0x0000000000002000,  
#define DBG_ATTRIB_VALUE_RAW_STRING     0x0000000000004000,  
#define DBG_ATTRIB_VALUE_CUSTOM_VIEWER  0x0000000000008000,  
  
// Attributes about field access types for the object  
  
#define DBG_ATTRIB_ACCESS_NONE          0x0000000000010000,  
#define DBG_ATTRIB_ACCESS_PUBLIC        0x0000000000020000,  
#define DBG_ATTRIB_ACCESS_PRIVATE       0x0000000000040000,  
#define DBG_ATTRIB_ACCESS_PROTECTED     0x0000000000080000,  
#define DBG_ATTRIB_ACCESS_FINAL         0x0000000000100000,  
#define DBG_ATTRIB_ACCESS_ALL           0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
#define DBG_ATTRIB_STORAGE_NONE         0x0000000001000000,  
#define DBG_ATTRIB_STORAGE_GLOBAL       0x0000000002000000,  
#define DBG_ATTRIB_STORAGE_STATIC       0x0000000004000000,  
#define DBG_ATTRIB_STORAGE_REGISTER     0x0000000008000000,  
#define DBG_ATTRIB_STORAGE_ALL          0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
#define DBG_ATTRIB_TYPE_NONE            0x0000000100000000,  
#define DBG_ATTRIB_TYPE_VIRTUAL         0x0000000200000000,  
#define DBG_ATTRIB_TYPE_CONSTANT        0x0000000400000000,  
#define DBG_ATTRIB_TYPE_SYNCHRONIZED    0x0000000800000000,  
#define DBG_ATTRIB_TYPE_VOLATILE        0x0000001000000000,  
#define DBG_ATTRIB_TYPE_ALL             0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
#define DBG_ATTRIB_DATA                 0x0000010000000000,  
#define DBG_ATTRIB_METHOD               0x0000020000000000,  
#define DBG_ATTRIB_PROPERTY             0x0000040000000000,  
#define DBG_ATTRIB_CLASS                0x0000080000000000,  
#define DBG_ATTRIB_BASECLASS            0x0000100000000000,  
#define DBG_ATTRIB_INTERFACE            0x0000200000000000,  
#define DBG_ATTRIB_INNERCLASS           0x0000400000000000,  
#define DBG_ATTRIB_MOSTDERIVED          0x0000800000000000,  
#define DBG_ATTRIB_CHILD_ALL            0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
#define DBG_ATTRIB_MULTI_CUSTOM_VIEWERS 0x0001000000000000  
  
typedef UINT64 DBG_ATTRIB_FLAGS;  
```  
  
```c#  
public const int DBG_ATTRIB_NONE                 = 0x0000000000000000,  
public const int DBG_ATTRIB_ALL                  = 0x00000000ffffffff,  
  
// Attributes about the object itself  
  
public const int DBG_ATTRIB_OBJ_IS_EXPANDABLE    = 0x0000000000000001,  
public const int DBG_ATTRIB_OBJ_HAS_ID           = 0x0000000000000002,  
public const int DBG_ATTRIB_OBJ_CAN_HAVE_ID      = 0x0000000000000004,  
  
// Attributes about the value of the object  
  
public const int DBG_ATTRIB_VALUE_READONLY       = 0x0000000000000010,  
public const int DBG_ATTRIB_VALUE_ERROR          = 0x0000000000000020,  
public const int DBG_ATTRIB_VALUE_SIDE_EFFECT    = 0x0000000000000040,  
public const int DBG_ATTRIB_OVERLOADED_CONTAINER = 0x0000000000000080,  
public const int DBG_ATTRIB_VALUE_BOOLEAN        = 0x0000000000000100,  
public const int DBG_ATTRIB_VALUE_BOOLEAN_TRUE   = 0x0000000000000200,  
public const int DBG_ATTRIB_VALUE_INVALID        = 0x0000000000000400,  
public const int DBG_ATTRIB_VALUE_NAT            = 0x0000000000000800,  
public const int DBG_ATTRIB_VALUE_AUTOEXPANDED   = 0x0000000000001000,  
public const int DBG_ATTRIB_VALUE_TIMEOUT        = 0x0000000000002000,  
public const int DBG_ATTRIB_VALUE_RAW_STRING     = 0x0000000000004000,  
public const int DBG_ATTRIB_VALUE_CUSTOM_VIEWER  = 0x0000000000008000,  
  
// Attributes about field access types for the object  
  
public const int DBG_ATTRIB_ACCESS_NONE          = 0x0000000000010000,  
public const int DBG_ATTRIB_ACCESS_PUBLIC        = 0x0000000000020000,  
public const int DBG_ATTRIB_ACCESS_PRIVATE       = 0x0000000000040000,  
public const int DBG_ATTRIB_ACCESS_PROTECTED     = 0x0000000000080000,  
public const int DBG_ATTRIB_ACCESS_FINAL         = 0x0000000000100000,  
public const int DBG_ATTRIB_ACCESS_ALL           = 0x00000000001f0000,  
  
// Attributes for the storage types of the object  
  
public const int DBG_ATTRIB_STORAGE_NONE         = 0x0000000001000000,  
public const int DBG_ATTRIB_STORAGE_GLOBAL       = 0x0000000002000000,  
public const int DBG_ATTRIB_STORAGE_STATIC       = 0x0000000004000000,  
public const int DBG_ATTRIB_STORAGE_REGISTER     = 0x0000000008000000,  
public const int DBG_ATTRIB_STORAGE_ALL          = 0x000000000f000000,  
  
// Attributes for the type modifiers on the object  
  
public const int DBG_ATTRIB_TYPE_NONE            = 0x0000000100000000,  
public const int DBG_ATTRIB_TYPE_VIRTUAL         = 0x0000000200000000,  
public const int DBG_ATTRIB_TYPE_CONSTANT        = 0x0000000400000000,  
public const int DBG_ATTRIB_TYPE_SYNCHRONIZED    = 0x0000000800000000,  
public const int DBG_ATTRIB_TYPE_VOLATILE        = 0x0000001000000000,  
public const int DBG_ATTRIB_TYPE_ALL             = 0x0000001f00000000,  
  
// Attributes that describe the type of object  
  
public const int DBG_ATTRIB_DATA                 = 0x0000010000000000,  
public const int DBG_ATTRIB_METHOD               = 0x0000020000000000,  
public const int DBG_ATTRIB_PROPERTY             = 0x0000040000000000,  
public const int DBG_ATTRIB_CLASS                = 0x0000080000000000,  
public const int DBG_ATTRIB_BASECLASS            = 0x0000100000000000,  
public const int DBG_ATTRIB_INTERFACE            = 0x0000200000000000,  
public const int DBG_ATTRIB_INNERCLASS           = 0x0000400000000000,  
public const int DBG_ATTRIB_MOSTDERIVED          = 0x0000800000000000,  
public const int DBG_ATTRIB_CHILD_ALL            = 0x0000ff0000000000,  
  
// Miscellaneous attributes  
  
public const int DBG_ATTRIB_MULTI_CUSTOM_VIEWERS = 0x0001000000000000  
```  
  
## Membri  
 DBG\_ATTRIB\_NONE  
 non indica attributi.  
  
 DBG\_ATTRIB\_ALL  
 indica tutti gli attributi.  
  
 DBG\_ATTRIB\_OBJ\_IS\_EXPANDABLE  
 indica che il riferimento o la proprietà ha figli.  
  
 DBG\_ATTRIB\_OBJ\_HAS\_ID  
 Indica che un ID per la creazione di questo oggetto.  
  
 DBG\_ATTRIB\_OBJ\_CAN\_HAVE\_ID  
 Indica che un ID per questo oggetto può essere creato.  
  
 DBG\_ATTRIB\_VALUE\_READONLY  
 indica che il valore è di sola lettura.  
  
 DBG\_ATTRIB\_VALUE\_ERROR  
 indica che il valore è un errore.  
  
 DBG\_ATTRIB\_VALUE\_SIDE\_EFFECT  
 Indica che la valutazione ha un effetto collaterale.  
  
 DBG\_ATTRIB\_OVERLOADED\_CONTAINER  
 Indica che questa proprietà è effettivamente un contenitore degli overload.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è un valore booleano.  
  
 DBG\_ATTRIB\_VALUE\_BOOLEAN\_TRUE  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è un valore boolean e `TRUE`.  
  
 DBG\_ATTRIB\_VALUE\_INVALID  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` non è valido.  
  
 DBG\_ATTRIB\_VALUE\_NAT  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` è “*non è*„ \(NAT\).  Il NAT descrive un flag del registro in processore a 64 bit Intel che indica le eccezioni speculative differite.  
  
 DBG\_ATTRIB\_VALUE\_AUTOEXPANDED  
 Indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` eventualmente auto\-è stato espanso.  
  
 DBG\_ATTRIB\_VALUE\_TIMEOUT  
 indica che una valutazione ha cronometrato\-fuori.  
  
 DBG\_ATTRIB\_VALUE\_RAW\_STRING  
 indica che il valore in `DEBUG_PROPERTY_INFO::bstrValue` può essere rappresentato da una stringa non elaborata.  
  
 DBG\_ATTRIB\_VALUE\_CUSTOM\_VIEWER  
 Indica che questa proprietà è associata almeno un visualizzatore personalizzato.  
  
 DBG\_ATTRIB\_ACCESS\_NONE  
 Indica un oggetto che non ha né `public`, `private`, né accesso del tipo di `protected` .  
  
 DBG\_ATTRIB\_ACCESS\_PUBLIC  
 indica un oggetto che ha accesso pubblico.  
  
 DBG\_ATTRIB\_ACCESS\_PRIVATE  
 Indica un oggetto con accesso privato.  
  
 DBG\_ATTRIB\_ACCESS\_PROTECTED  
 indica un oggetto che ha accesso protetto.  
  
 DBG\_ATTRIB\_ACCESS\_FINAL  
 Indica un oggetto che dispone di accesso finale.  
  
 DBG\_ATTRIB\_ACCESS\_ALL  
 Maschera per disegnare gli attributi di accesso da `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_STORAGE\_NONE  
 Indica che non esiste un singolo tipo di archiviazione specificato.  
  
 DBG\_ATTRIB\_STORAGE\_GLOBAL  
 Indica archivio globale.  
  
 DBG\_ATTRIB\_STORAGE\_STATIC  
 Indica la memoria statica.  
  
 DBG\_ATTRIB\_STORAGE\_REGISTER  
 Indica l'archiviazione nel log.  
  
 DBG\_ATTRIB\_STORAGE\_ALL  
 Maschera per disegnare gli attributi di archiviazione da `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_TYPE\_NONE  
 Indica che non esiste alcun modificatore di tipo.  
  
 DBG\_ATTRIB\_TYPE\_VIRTUAL  
 indica che il tipo di oggetto è virtuale.  
  
 DBG\_ATTRIB\_TYPE\_CONSTANT  
 indica che il tipo di oggetto è costante.  
  
 DBG\_ATTRIB\_TYPE\_SYNCHRONIZED  
 indica che il tipo di oggetto è sincronizzato.  
  
 DBG\_ATTRIB\_TYPE\_VOLATILE  
 indica che il tipo di oggetto è volatile.  
  
 DBG\_ATTRIB\_TYPE\_ALL  
 Maschera per disegnare gli attributi del tipo da `DBG_ATTRIB_FLAGS`.  
  
 DBG\_ATTRIB\_DATA  
 Indica che l'oggetto è un campo dati.  
  
 DBG\_ATTRIB\_METHOD  
 Indica che l'oggetto è un metodo.  
  
 DBG\_ATTRIB\_PROPERTY  
 Indica che è una proprietà.  
  
 DBG\_ATTRIB\_CLASS  
 Indica che questo oggetto è una classe.  
  
 DBG\_ATTRIB\_BASECLASS  
 Indica che questo oggetto è una classe base.  
  
 DBG\_ATTRIB\_INTERFACE  
 indica che questo oggetto è un'interfaccia.  
  
 DBG\_ATTRIB\_INNERCLASS  
 indica che questo oggetto è una classe interna.  
  
 DBG\_ATTRIB\_MOSTDERIVED  
 indica che questo oggetto “più\-*è derivato*„.  Significa “*più\-derivati*„ termine del tipo effettivo dell'oggetto e non il tipo del riferimento.  
  
 DBG\_ATTRIB\_CHILD\_ALL  
 indica una maschera di `DBG_ATTRIB_DATA` con `DBG_ATTRIB_MOSTDERIVED`.  
  
 DBG\_ATTRIB\_MULTI\_CUSTOM\_VIEWERS  
 Indica che l'oggetto ha visualizzatori personalizzati più associati.  
  
## Note  
  
> [!NOTE]
>  I valori in questa enumerazione non sono effettivamente definiti nell'assembly per c\#.  Al contrario, è necessario copiare le definizioni al file di origine.  
  
 Questi flag vengono utilizzati per filtrare gli elementi figlio di un oggetto, ad esempio, una volta passati come argomento a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md).  I valori possono essere combinate con `OR`bit per bit.  
  
 Il flag di `DBG_ATTRIB_VALUE_CUSTOM_VIEWER` è sufficiente a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] di ottenere [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) l'interfaccia [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) dall'interfaccia e la richiesta [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) per un elenco di visualizzatori personalizzati.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)