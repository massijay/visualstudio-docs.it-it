---
title: "IActiveScript::InterruptScriptThread | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.InterruptScriptThread
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_InterruptScriptThread"
ms.assetid: 2304d035-6d39-4811-acd3-8a9640fdbef6
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::InterruptScriptThread
Interrompere l'esecuzione di un thread in esecuzione dello script \(un sink di evento, l'esecuzione immediata, o una chiamata di macro\).  Questo metodo può essere utilizzato per terminare uno script che verrebbe è, ad esempio in un ciclo infinito\).  Può essere chiamato dai thread non di base senza con conseguente callout di non base agli oggetti host o al metodo [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Sintassi  
  
```  
HRESULT InterruptScriptThread(  
    SCRIPTTHREADID   stidThread,  // identifier of thread  
    const EXCEPINFO *pexcepinfo,  // receives error information  
    DWORD dwFlags  
);  
```  
  
#### Parametri  
 `stidThread`  
 \[in\] identificatore del thread da interrompere, o uno dell'identificatore speciale di thread stima:  
  
|Valore|Significato|  
|------------|-----------------|  
|SCRIPTTHREADID\_ALL|Tutti i thread.  Si applica attualmente a tutti i metodi di script corrente.  Si noti che a meno che il chiamante ha richiesto che lo script è disconnesso, il codice di script basati su script seguente di cause di evento per eseguire nuovamente chiamando il metodo [IActiveScript::SetScriptState](../../winscript/reference/iactivescript-setscriptstate.md) con il flag di SCRIPTSTATE\_INITIALIZED o di SCRIPTSTATE\_DISCONNECTED.|  
|SCRIPTTHREADID\_BASE|Il thread di base; ovvero il thread in cui il motore di scripting è stata creata un'istanza.|  
|SCRIPTTHREADID\_CURRENT|Il thread attualmente in esecuzione.|  
  
 `pexcepinfo`  
 \[in\] indirizzo di una struttura `EXCEPINFO` contenente informazioni che devono essere restituite allo script interrotto.  
  
 `dwFlags`  
 \[in\] i flag di opzione associato all'interruzione.  Può essere uno dei seguenti valori:  
  
|Valore|Significato|  
|------------|-----------------|  
|SCRIPTINTERRUPT\_DEBUG|Se supportato, registrare il debugger del motore di scripting al punto corrente di esecuzione degli script.|  
|SCRIPTINTERRUPT\_RAISEEXCEPTION|Se supportato dal motore di scripting, lasciare lo script gestire l'eccezione.  In caso contrario, il metodo lo script viene interrotto e il codice di errore viene restituito al chiamante, ovvero il invoker di macro o di origine evento.|  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\).|  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)