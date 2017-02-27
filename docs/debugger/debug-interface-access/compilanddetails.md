---
title: "CompilandDetails | Microsoft Docs"
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
  - "CompilandDetails (simbolo)"
ms.assetid: ddc7d794-c622-4c63-b2a6-72f8b2d0022a
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# CompilandDetails
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le informazioni di Modulo sono divise tra i simboli con un oggetto `SymTagCompiland` tag \(dettaglio basso\) e  `SymTagCompilandDetails` tag \(dettaglio alto\).  `SymTagCompilandDetails` richiede simboli aggiuntivi di carico.  Tuttavia, fornisce una ricca di informazioni sul modulo che non è disponibile con un oggetto `SymTagCompiland` simbolo.  
  
## Proprietà  
 Nella tabella seguente vengono illustrate le proprietà che sono valide per questo tipo del simbolo.  
  
|Proprietà|Tipo di dati|Descrizione|  
|---------------|------------------|-----------------|  
|[IDiaSymbol::get\_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|`DWORD`|Numero di build back\-end del compilatore.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|`DWORD`|Numero di versione principale di back\-end del compilatore.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|`DWORD`|Numero di versione secondaria di back\-end del compilatore.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|`BSTR`|Nome del compilatore che ha generato questo modulo \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|`BOOL`|`TRUE` se la Modifica e continuazione è attivata alla compilazione.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|`DWORD`|Numero di build front\-end del compilatore.|  
|[IDiaSymbol::get\_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|`DWORD`|Numero di versione principale front\-end del compilatore.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|`DWORD`|Numero di versione secondario front\-end del compilatore.|  
|[IDiaSymbol::get\_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|`BOOL`|`TRUE` se questo modulo contiene informazioni di debug \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|`BOOL`|`TRUE` se questo modulo contiene codice gestito \(solo DIA SDK in v8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|`BOOL`|`TRUE` se il modulo è stato compilato con  [\/GS \(Controllo sicurezza buffer\)](/visual-cpp/build/reference/gs-buffer-security-check) opzione del compilatore \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|`BOOL`|`TRUE` se il modulo è stato convertito dal codice comune \(CIL\) di Microsoft Intermediate Language\) in codice nativo.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|`BOOL`|`TRUE` se i tipi definiti \(UDT\) dall'utente sono stati allineati al limite specificato di memoria \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|`BOOL`|`TRUE` se il modulo è stato compilato con  [\/hotpatch \(Crea immagine con funzionalità di patch a caldo\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) opzione del compilatore \(solo DIA SDK in v8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|`BOOL`|`TRUE` se il modulo è stato compilato con  [\/LTCG \(Generazione di codice in fase di collegamento\)](/visual-cpp/build/reference/ltcg-link-time-code-generation) opzione del compilatore \(solo DIA SDK in V8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|`BOOL`|TRUE se il modulo è un modulo MSIL \(solo DIA SDK in v8.0 o in versioni successive\).|  
|[IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|`DWORD`|Il linguaggio del codice sorgente.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|`IDiaSymbol*`|I simboli per il modulo.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|`DWORD`|ID del simbolo padre lessicale.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|`DWORD`|Piattaforma in cui il modulo è stato compilato \(uno di [Enumerazione CV\_CPU\_TYPE\_e](../../debugger/debug-interface-access/cv-cpu-type-e.md) valori\).|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|`DWORD`|Indice ID del simbolo.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|`DWORD`|Restituisce `SymTagCompilandDetails` \(uno di  [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) valori\).|  
  
## Note  
 I compilatori sono spesso in un form noto come un compilatore in due passaggi per; in alcune versioni del compilatore, ogni sessione viene gestita da un programma separato.  Questi sono noti come i compilatori back\-end e del front\-end, rispettivamente, le proprietà dei simboli per i numeri di versione back\-end e front\-end.  
  
## Vedere anche  
 [Compilando](../../debugger/debug-interface-access/compiland.md)   
 [Gerarchia lessicale dei tipi di simboli](../../debugger/debug-interface-access/lexical-hierarchy-of-symbol-types.md)