---
title: "Strutture e unioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strutture [Visual Studio SDK]"
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Strutture e unioni
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Di seguito sono strutture e le unioni in Visual Studio per il debug SDK.  
  
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 specifica l'ID processo, che può essere un sistema ID o un GUID.  
  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Vengono descritte le condizioni in cui un punto di interruzione verrà generato.  
  
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Viene descritta la risoluzione di un punto di interruzione di errori, incluso il percorso, il programma e il thread.  
  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Specifica il tipo di struttura utilizzato per descrivere la posizione del punto di interruzione.  
  
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Definisce i componenti che descrivono la posizione di un punto di interruzione a un indirizzo nel codice.  
  
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Viene descritta la posizione di un punto di interruzione associato direttamente a un indirizzo nel programma sottoposto a debug.  
  
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Viene descritta la posizione di un punto di interruzione alla riga in un file di origine del codice.  
  
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Viene descritta la posizione di offset di un punto di interruzione su una funzione nel codice.  
  
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Utilizzato per impostare i punti di interruzione di codice in base a una stringa che l'utente può immettere IDE.  
  
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Utilizzato per impostare i punti di interruzione di dati basati su una stringa che l'utente può immettere IDE.  
  
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Viene descritta la risoluzione di un punto di interruzione in una posizione specifica.  
  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Viene descritto il conteggio e le condizioni in cui un punto di interruzione verrà successivamente in precedenza passaggio generato.  
  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Contiene le informazioni necessarie per implementare un punto di interruzione.  
  
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Contiene le informazioni necessarie per implementare un punto di interruzione \(stesso [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) della struttura ma include informazioni del fornitore GUID, il vincolo e il punto di analisi\).  
  
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Viene descritta la posizione di un punto di interruzione di codice.  
  
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Viene illustrato il risultato di associare un punto di interruzione dei dati.  
  
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Vengono descritte le informazioni associate del punto di interruzione per un punto di interruzione di codice o un punto di interruzione dei dati.  
  
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Specifica la struttura della posizione di risoluzione del punto di interruzione.  
  
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Viene descritta una matrice di stringhe.  
  
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Specifica le informazioni su un tipo di campo utilizzato dai metadati.  
  
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Viene descritta una chiamata a una funzione o un metodo.  
  
 [COMPUTER\_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Viene descritto il computer in cui il debugger è in esecuzione.  
  
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Viene descritto un elenco di GUID.  
  
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Viene descritto un contesto o un contesto di codice di memoria.  
  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Viene descritto un indirizzo in un programma sottoposto a debug.  
  
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Rappresenta uno tra diversi tipi diversi degli indirizzi.  
  
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Identifica un visualizzatore o un visualizzatore personalizzato del tipo.  
  
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Viene descritta una proprietà di debug che a sua volta descrive un oggetto di una natura gerarchica con il nome, il tipo e il valore.  
  
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 descrive un riferimento.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Viene descritto il disassembly all'IDE per la visualizzazione.  
  
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Viene descritta un'eccezione o un errore di runtime generato dal programma sottoposto a debug.  
  
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Viene descritta una variabile locale, un parametro, o un altro campo.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Viene descritto uno stack frame.  
  
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Viene descritta una matrice di identificatori univoci per i motori di debug.  
  
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Viene utilizzato per impostare le informazioni di JustMyCode per un modulo.  
  
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Descrive un particolare computer.  
  
 [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Descrive un elemento di matrice in una matrice.  
  
 [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Viene descritto l'indirizzo di un campo di una classe o struttura.  
  
 [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Viene descritto l'indirizzo di una variabile locale all'interno di un ambito in genere una funzione o un metodo.  
  
 [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Viene descritto l'indirizzo di un metodo di una classe.  
  
 [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Viene descritto un parametro di un metodo o una funzione.  
  
 [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Viene descritto un valore restituito da un metodo o una funzione.  
  
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Descrive un tipo di campo utilizzato dai metadati.  
  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Viene descritto un modulo specifico \(DLL, EXE, o assembly\).  
  
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Vengono descritte le informazioni sullo stato dei percorsi di ricerca dei simboli che sono stati trovati.  
  
 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Viene descritto un indirizzo nativo.  
  
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Descrive un tipo di campo ottenuto da un simbolo PDB.  
  
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Viene descritto lo stato di un punto di interruzione che è pronto per l'associazione a un percorso di codice.  
  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)  
 descrive un processo.  
  
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Viene descritto un [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) elenco di oggetti che rappresentano i nodi del programma.  
  
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Vengono descritti i processi in esecuzione in un computer.  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Viene descritta la posizione di riga nel testo specificato.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Vengono descritte le proprietà di un thread.  
  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Descrive un tipo di campo.  
  
 [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Viene descritto un indirizzo fisico.  
  
 [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Viene descritto un indirizzo relativo a un puntatore di `this` \(`Me` in Visual Basic\).  
  
## Requisiti  
 intestazione: msdbg.h, sh.h, o ee.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)