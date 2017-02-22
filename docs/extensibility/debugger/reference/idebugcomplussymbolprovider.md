---
title: "IDebugComPlusSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugComPlusSymbolProvider"
ms.assetid: 5b98e908-fd15-49a6-9010-933c9b948085
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugComPlusSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rappresenta un provider del simbolo COM\+ con i metodi specifici del codice gestito.  
  
## Sintassi  
  
```  
IDebugComPlusSymbolProvider : IDebugSymbolProvider  
```  
  
## Note per gli implementatori  
 Sebbene non sia presente la separazione tra le interfacce che sono utili a un analizzatore di espressioni \(EE\) e quelle che possono essere utilizzati dal motore \(DE\) di debug, i seguenti metodi di solo probabilmente interest DE developers: AreSymbolsLoaded, GetAddressesInModuleFromPosition, GetEntryPoint, GetFunctionLineOffset, GetLocalVariableLayout, IsFunctionStale, LoadSymbols, LoadSymbolsFromStream, ReplaceSymbols, UnloadSymbols e UpdateSymbols.  
  
## Metodi  
 Oltre ai metodi [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) in un'interfaccia, l'interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[AreSymbolsLoaded](../Topic/IDebugComPlusSymbolProvider::AreSymbolsLoaded.md)|Determina se i simboli di debug vengono caricati dal modulo specificato fornito identificatore del dominio applicazione.|  
|[CreateTypeFromPrimitive](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-createtypefromprimitive.md)|Crea un tipo dal tipo primitivo specificato.|  
|[GetAddressesInModuleFromPosition](../Topic/IDebugComPlusSymbolProvider::GetAddressesInModuleFromPosition.md)|Esegue il mapping di una posizione del documento nel modulo specificato in una matrice degli indirizzi di debug.|  
|[GetArrayTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getarraytypefromaddress.md)|Recupera le informazioni sui tipi per la matrice specificata in base al relativo indirizzo di debug.|  
|[GetAssemblyName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getassemblyname.md)|Recupera il nome di assembly fornito il modulo e dominio applicazione.|  
|[GetAttributedClassesForLanguage](../Topic/IDebugComPlusSymbolProvider::GetAttributedClassesForLanguage.md)|Recupera le classi con l'attributo specificato implementate nel linguaggio di programmazione specificato.|  
|[GetAttributedClassesinModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getattributedclassesinmodule.md)|recupera le classi con l'attributo specificato in un modulo specificato.|  
|[GetEntryPoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getentrypoint.md)|Recupera il punto di ingresso dell'applicazione.|  
|[GetFunctionLineOffset](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getfunctionlineoffset.md)|Viene recuperato l'indirizzo di una funzione che rappresenta l'offset specificato della riga.|  
|[GetLocalVariablelayout](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getlocalvariablelayout.md)|Recupera il layout delle variabili locali per un set di metodi.|  
|[GetNameFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getnamefromtoken.md)|Restituisce il nome associato al token specificato fornito il relativo oggetto dei metadati.|  
|[GetSymAttribute](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymattribute.md)|recupera i simboli di debug con l'attributo padre specificato per il modulo specificato.|  
|[GetSymUnmanagedReader](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-getsymunmanagedreader.md)|Recupera il reader di simboli da utilizzare dal codice non gestito.|  
|[GetTypeFromAddress](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-gettypefromaddress.md)|Recupera il simbolo un tipo fornito il relativo indirizzo di debug.|  
|[IsFunctionDeleted](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctiondeleted.md)|Determina se la funzione all'indirizzo specificato di debug viene eliminato.|  
|[IsFunctionStale](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-isfunctionstale.md)|Determina se la funzione all'indirizzo specificato di debug è considerata non aggiornata.|  
|[IsHiddenCode](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-ishiddencode.md)|Determina se il codice all'indirizzo specificato il debugger è nascosto.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbols.md)|Carica simboli di debug specificati in memoria.|  
|[LoadSymbolsFromStream](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-loadsymbolsfromstream.md)|Carica simboli di debug forniti il flusso di dati.|  
|[ReplaceSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-replacesymbols.md)|Sostituisce i simboli di debug correnti con quelli del flusso di dati specificato.|  
|[UnloadSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-unloadsymbols.md)|Consente di scaricare i simboli di debug per il modulo specificato dalla memoria.|  
|[UpdateSymbols](../../../extensibility/debugger/reference/idebugcomplussymbolprovider-updatesymbols.md)|Aggiorna i simboli di debug in memoria con quelli il flusso di dati specificato.|  
  
## Requisiti  
 intestazione: Sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll