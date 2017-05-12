---
title: "IActiveScriptParse::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptParse.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptParse_ParseScriptText"
ms.assetid: 2d237d6c-cc65-415b-8808-72791304a136
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptParse::ParseScriptText
Analizza lo scriptlet di codice specificato, aggiungendo le dichiarazioni dello spazio dei nomi e valutando il codice in base alle proprie esigenze.  
  
## Sintassi  
  
```  
HRESULT ParseScriptText(  
    LPCOLESTR pstrCode,              // address of scriptlet text  
    LPCOLESTR pstrItemName,          // address of item name  
    IUnknown *punkContext,           // address of debugging context  
    LPCOLESTR pstrDelimiter,         // address of end-of-scriptlet delimiter  
    DWORD_PTR dwSourceContextCookie, // cookie for debugging  
    ULONG ulStartingLineNumber,      // starting line of the script  
    DWORD dwFlags,                   // scriptlet flags  
    VARIANT *pvarResult,             // address of buffer for results  
    EXCEPINFO *pexcepinfo            // address of buffer for error data  
);  
```  
  
#### Parametri  
  
|||  
|-|-|  
|`pstrCode`|\[in\] Indirizzo del testo dello scriptlet da valutare.  L'interpretazione di questa stringa dipende dal linguaggio di script.|  
|`pstrItemName`|\[in\] Indirizzo del nome dell'elemento che fornisce il contesto in cui lo scriptlet deve essere valutato.  Se questo parametro è NULL, il codice viene valutato nel contesto globale del motore di script.|  
|`punkContext`|\[in\] Indirizzo dell'oggetto di contesto.  Questo oggetto è riservato all'utilizzo in un ambiente di debug, in cui tale contesto possa essere fornito dal debugger per rappresentare un contesto per la fase esecuzione attivo.  Se questo parametro è NULL, il motore utilizza `pstrItemName` per identificare il contesto.|  
|`pstrDelimiter`|\[in\] Indirizzo del delimitatore end\-of\-scriptlet.  Quando `pstrCode` viene analizzato da un flusso di testo, l'host utilizza in genere un delimitatore, ad esempio due virgolette singole \('\), per rilevare la fine dello scriptlet.  Questo parametro specifica il delimitatore utilizzato dall'host, consentendo al motore di gestione di scripting di fornire alcune pre\-elaborazioni primitive condizionali \(ad esempio la sostituzione di una virgoletta singola \['\] con due virgolette singole da utilizzare come delimitatore\).  L'utilizzo di queste informazioni da parte del motore di script \(e se le utilizza\) dipende dal motore di script.  Impostare questo parametro su `NULL` se l'host non utilizzava un delimitatore per contrassegnare la fine dello scriptlet.|  
|`dwSourceContextCookie`|\[in\] Cookie utilizzato per eseguire il debug.|  
|`ulStartingLineNumber`|\[in\] Valore in base zero che specifica la riga in cui inizierà l'analisi.|  
|`dwFlags`|\[in\] Flag associati allo scriptlet.  Può trattarsi di una combinazione di questi valori:|  
  
|Valore|Significato|  
|------------|-----------------|  
|SCRIPTTEXT\_ISEXPRESSION|Se la distinzione tra un'espressione di calcolo e un'istruzione è importante ma sintatticamente ambigua nel linguaggio di script, questo flag specifica che lo scriptlet deve essere interpretato come un'espressione, anziché come un'istruzione o un elenco di istruzioni.  Per impostazione predefinita, le istruzioni vengono presupposte a meno che la scelta corretta possa essere determinata dalla sintassi del testo dello scriptlet.|  
|SCRIPTTEXT\_ISPERSISTENT|Indica che il codice aggiunto durante la chiamata deve essere salvato quando il motore di scripting viene salvato, ad esempio tramite una chiamata a `IPersist*::Save`\), o se il motore di scripting viene reimpostato tramite una transizione di nuovo allo stato inizializzato.|  
|SCRIPTTEXT\_ISVISIBLE|Indica che il testo dello script è visibile \(e pertanto può essere chiamato per nome\) come metodo globale nello spazio dei nomi dello script.|  
  
|||  
|-|-|  
|`pvarResult`|\[out\] Indirizzo di un buffer che riceve i risultati dell'elaborazione di scriptlet o `NULL` se il chiamante non prevede risultati, ossia il valore di SCRIPTTEXT\_ISEXPRESSION non è impostato\).|  
|`pexcepinfo`|\[out\] Indirizzo di una struttura che riceve informazioni sull'eccezione.  Questa struttura viene compilata se `IActiveScriptParse::ParseScriptText` restituisce DISP\_E\_EXCEPTION.|  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`DISP_E_EXCEPTION`|Eccezione nell'elaborazione dello scriptlet.  Il parametro `pexcepinfo` contiene informazioni sull'eccezione.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_NOTIMPL`|Metodo non supportato.  Il motore di script non supporta la valutazione in fase di esecuzione delle espressioni o delle istruzioni.|  
|`E_UNEXPECTED`|La chiamata non era attesa \(ad esempio, il modulo di gestione di scripting è nello stato di non inizializzato o chiuso oppure è stato impostato il flag SCRIPTTEXT\_ISEXPRESSION e il motore di scripting è nello stato di inizializzato\).|  
|`OLESCRIPT_E_SYNTAX`|Nello scriptlet si è verificato un errore di sintassi non specificato.|  
  
## Note  
 Se il motore di script è nello stato inizializzato, non verrà in effetti eseguita la valutazione del codice durante questa chiamata. Il codice verrà invece accodato ed eseguito quando verrà eseguita la transizione del motore di script allo \(o tramite lo\) stato avviato.  Poiché l'esecuzione non è consentita nello stato inizializzato, è un errore chiamare il metodo con il flag SCRIPTTEXT\_ISEXPRESSION quando si trova nello stato inizializzato.  
  
 Lo scriptlet può essere un'espressione, un elenco di istruzioni o un valore consentito dal linguaggio di script.  Ad esempio, questo metodo viene utilizzato nella valutazione del tag HTML \<SCRIPT\>, che consente l'esecuzione delle istruzioni durante la costruzione della pagina HTML, anziché limitarsi alla loro compilazione nello script.  
  
 Il codice passato a questo metodo deve essere una parte di codice valida e completa.  Ad esempio, in VBScript non è consentito chiamare questo metodo una volta con Sub Function\(x\) e la seconda volta con `End Sub`.  Il parser non deve attendere che la seconda chiamata completi la subroutine, piuttosto deve generare un errore di analisi in quanto una dichiarazione di subroutine è stata avviata ma non è stata completata.  
  
 Per ulteriori informazioni sugli stati dello script, vedere la sezione relativa agli stati dei motori di script di [Motori di script Windows](../../winscript/windows-script-engines.md).  
  
## Vedere anche  
 [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md)