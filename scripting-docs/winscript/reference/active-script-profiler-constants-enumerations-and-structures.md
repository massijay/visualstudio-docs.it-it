---
title: "Costanti, enumerazioni e strutture del profiler di script ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Costanti, enumerazioni e strutture del profiler di script ActiveX
Le seguenti enumerazioni vengono utilizzate dalle interfacce attive del profiler dello script.  
  
## Costanti, enumerazioni e strutture  
  
|Costanti|Descrizione|  
|--------------|-----------------|  
|[Tipo PROFILER\_EXTERNAL\_OBJECT\_ADDRESS](../../winscript/reference/profiler-external-object-address-type.md)|L'indirizzo esterno dell'oggetto del profiler.  Utilizzato in [Struttura PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) e [Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Tipo PROFILER\_HEAP\_OBJECT\_ID](../../winscript/reference/profiler-heap-object-id-type.md)|L'ID dell'oggetto heap.  Utilizzato in [Struttura PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md) [Struttura PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [Struttura PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md), e [Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Tipo PROFILER\_HEAP\_OBJECT\_NAME\_ID](../../winscript/reference/profiler-heap-object-name-id-type.md)|L'id del nome dell'oggetto heap.  Utilizzato in [Struttura PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
  
|Enumerazioni|Descrizione|  
|------------------|-----------------|  
|[Enumerazione PROFILER\_EVENT\_MASK](../../winscript/reference/profiler-event-mask-enumeration.md)|Indica i tipi di eventi che devono essere profilati.|  
|[Enumerazione PROFILER\_HEAP\_ENUM\_FLAGS](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Flag che rappresentano se viene esposta un'informazione aggiuntiva su un oggetto heap puntato in una relazione tra oggetti.  Utilizzato in [Metodo IActiveScriptProfilerControl5::EnumHeap2](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md).|  
|[Enumerazione PROFILER\_HEAP\_OBJECT\_FLAGS](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flag che rappresentano le informazioni di base sull'oggetto heap.  Utilizzato in [Struttura PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md).|  
|[Enumerazione PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Rappresenta diversi tipi di informazioni facoltative.  Utilizzato in [Struttura PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md).|  
|[Enumerazione PROFILER\_INFO\_OBJECT\_FLAGS](../../winscript/reference/profiler-relationship-info-enumeration.md)|Rappresenta informazioni sull'oggetto nella relazione.  Utilizzato in [Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[Enumerazione PROFILER\_SCRIPT\_TYPE](../../winscript/reference/profiler-script-type-enumeration.md)|Specifica il tipo di script.|  
  
|Strutture|Descrizione|  
|---------------|-----------------|  
|[Struttura PROFILER\_HEAP\_OBJECT](../../winscript/reference/profiler-heap-object-structure.md)|Rappresenta gli oggetti heap raccolti da [Metodo IActiveScriptProfilerControl3::EnumHeap](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md).|  
|[Struttura PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Rappresenta le informazioni facoltative sugli oggetti heap.|  
|[Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Rappresenta una relazione di un oggetto heap.|  
|[Struttura PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Rappresenta un elenco di relazioni che appartengono a un oggetto heap.|  
|[Struttura PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Questa struttura viene associata sono agli oggetti funzione.  L'elenco di ambito rappresenta la chiusura della funzione come elenco di ambiti dove ogni ambito è un oggetto heap con un elenco di proprietà associate che rappresenta le variabili di ogni ambito specificato.  In alcuni casi, i nomi degli oggetti in quell'ambito potrebbero non essere disponibili, solo il relativo ID.|  
  
## Vedere anche  
 [Interfacce del profiler dello script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)