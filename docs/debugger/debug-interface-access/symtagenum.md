---
title: "SymTagEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SymTagEnum (enumerazione)"
ms.assetid: 528a50cf-e13d-46ec-a98c-323d5d047de9
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# SymTagEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Specifica il tipo di simbolo.  
  
## Sintassi  
  
```cpp#  
enum SymTagEnum {   
   SymTagNull,  
   SymTagExe,  
   SymTagCompiland,  
   SymTagCompilandDetails,  
   SymTagCompilandEnv,  
   SymTagFunction,  
   SymTagBlock,  
   SymTagData,  
   SymTagAnnotation,  
   SymTagLabel,  
   SymTagPublicSymbol,  
   SymTagUDT,  
   SymTagEnum,  
   SymTagFunctionType,  
   SymTagPointerType,  
   SymTagArrayType,   
   SymTagBaseType,   
   SymTagTypedef,   
   SymTagBaseClass,  
   SymTagFriend,  
   SymTagFunctionArgType,   
   SymTagFuncDebugStart,   
   SymTagFuncDebugEnd,  
   SymTagUsingNamespace,   
   SymTagVTableShape,  
   SymTagVTable,  
   SymTagCustom,  
   SymTagThunk,  
   SymTagCustomType,  
   SymTagManagedType,  
   SymTagDimension,  
   SymTagCallSite,  
   SymTagInlineSite,  
   SymTagBaseInterface,  
   SymTagVectorType,  
   SymTagMatrixType,  
   SymTagHLSLType  
};  
```  
  
## Elementi  
 `SymTagNull`  
 Indica che il simbolo dispone di alcun tipo.  
  
 `SymTagExe`  
 Indica che il simbolo è un file exe.  È disponibile un solo `SymTagExe` un simbolo per l'archivio dei simboli.  Funge da ambito globale e non ha un padre lessicale.  
  
 `SymTagCompiland`  
 Indica il simbolo di modulo per ogni componente modulo di archivio di simboli.  Per le applicazioni native, `SymTagCompiland` i simboli corrispondano per i file oggetto collegati nell'immagine.  Per alcuni tipi di immagini Microsoft Intermediate Language \(MSIL\), è disponibile un modulo per ogni classe.  
  
 `SymTagCompilandDetails`  
 Indica che il simbolo contiene gli attributi estesi del modulo.  Il recupero di tali proprietà potrebbe richiedere il caricamento di simboli del modulo.  
  
 `SymTagCompilandEnv`  
 Indica che il simbolo è una stringa di ambiente definita per il modulo.  
  
 `SymTagFunction`  
 Indica che il simbolo è una funzione.  
  
 `SymTagBlock`  
 Indica che il simbolo è un blocco nidificato.  
  
 `SymTagData`  
 Indica che il simbolo di dati.  
  
 `SymTagAnnotation`  
 Indica che il simbolo è per un'annotazione del codice.  Gli elementi figlio di questo simbolo sono stringhe di dati costanti \(`SymTagData`, `LocIsConstant`, `DataIsConstant`\).  La maggior parte dei client ignora questo simbolo.  
  
 `SymTagLabel`  
 Indica che il simbolo è un'etichetta.  
  
 `SymTagPublicSymbol`  
 Indica che il simbolo è un simbolo public.  Per le applicazioni native, questo simbolo è il simbolo esterno COFF rilevato durante il collegamento dell'immagine.  
  
 `SymTagUDT`  
 Indica che il simbolo è un tipo definito dall'utente \(struttura, classe o unione\).  
  
 `SymTagEnum`  
 Indica che il simbolo è un'enumerazione.  
  
 `SymTagFunctionType`  
 Indica che il simbolo è un tipo di firma della funzione.  
  
 `SymTagPointerType`  
 Indica che il simbolo è un tipo puntatore.  
  
 `SymTagArrayType`  
 Indica che il simbolo è un tipo matrice.  
  
 `SymTagBaseType`  
 Indica che il simbolo è un tipo di base.  
  
 `SymTagTypedef`  
 Indica che il simbolo è un `typedef`, vale a dire un alias per un altro tipo.  
  
 `SymTagBaseClass`  
 Indica che il simbolo è una classe base di un tipo definito dall'utente.  
  
 `SymTagFriend`  
 Indica che il simbolo è un amico di un tipo definito dall'utente.  
  
 `SymTagFunctionArgType`  
 Indica che il simbolo è un argomento di funzione.  
  
 `SymTagFuncDebugStart`  
 Indica che il simbolo è la posizione di fine del codice di prologo della funzione.  
  
 `SymTagFuncDebugEnd`  
 Indica che il simbolo è la posizione di inizio del codice di epilogo della funzione.  
  
 `SymTagUsingNamespace`  
 Indica che il simbolo è un nome di spazio dei nomi attivo nell'ambito corrente.  
  
 `SymTagVTableShape`  
 Indica che il simbolo è una descrizione della tabella virtuale.  
  
 `SymTagVTable`  
 Indica che il simbolo è un puntatore di tabella virtuale.  
  
 `SymTagCustom`  
 Indica che il simbolo è un simbolo personalizzato e non viene interpretato da dia.  
  
 `SymTagThunk`  
 Indica che il simbolo è un thunk utilizzato per la condivisione dei dati tra 16 e il codice a 32 bit.  
  
 `SymTagCustomType`  
 Indica che il simbolo è un simbolo di compilazione personalizzata.  
  
 `SymTagManagedType`  
 Indica che il simbolo è nei metadati.  
  
 `SymTagDimension`  
 Indica che il simbolo è una matrice multidimensionale FORTRAN.  
  
 `SymTagCallSite`  
 Indica che il simbolo rappresenta il sito di chiamata.  
  
 `SymTagInlineSite`  
 Indica che il simbolo rappresenta il sito in linea.  
  
 `SymTagBaseInterface`  
 Indica che il simbolo è un'interfaccia di base.  
  
 `SymTagVectorType`  
 Indica che il simbolo è un tipo vettore.  
  
 `SymTagMatrixType`  
 Indica che il simbolo è un tipo matrice.  
  
 `SymTagHLSLType`  
 Indica che il simbolo è un tipo di linguaggio di alto livello Shader.  
  
## Note  
 Tutti i simboli all'interno di un file di debug dispone di un tag di identificazione che specifica il tipo del simbolo.  
  
 I valori di questa enumerazione vengono restituiti da una chiamata per il [IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md) metodo.  
  
 I valori di questa enumerazione vengono passati ai seguenti metodi per limitare l'ambito della ricerca a un tipo di simbolo specifico:  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)  
  
-   [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
  
## Requisiti  
 Intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)   
 [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)   
 [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)   
 [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)   
 [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)   
 [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)   
 [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)