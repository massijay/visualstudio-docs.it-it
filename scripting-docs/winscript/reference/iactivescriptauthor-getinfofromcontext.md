---
title: "IActiveScriptAuthor::GetInfoFromContext | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetInfoFromContext
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetInfoFromContext"
ms.assetid: 9891b095-6eb5-4473-87c0-c2e5cd2afc1a
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::GetInfoFromContext
Restituisce informazioni sul tipo e percorsi di ancoraggio di un carattere specificato in un blocco di codice.  Ciò fornisce informazioni per il membro IntelliSense, elenchi globali e i suggerimenti di parametro.  
  
## Sintassi  
  
```  
HRESULT GetInfoFromContext(  
   LPCOLESTR  pszCode,  
   ULONG      cchCode,  
   ULONG      ichCurrentPosition,  
   DWORD      dwListTypesRequested,  
   DWORD      *pdwListTypesProvided,  
   ULONG      *pichListAnchorPosition,  
   ULONG      *pichFuncAnchorPosition,  
   MEMBERID   *pmemid,  
   LONG       *piCurrentParameter,  
   IUnknown   **ppunk  
);  
```  
  
#### Parametri  
 `pszCode`  
 \[in\] indirizzo della stringa del blocco di codice utilizzata per generare le informazioni risultati.  
  
 `cchCode`  
 \[in\] la lunghezza del blocco di codice.  
  
 `ichCurrentPosition`  
 \[in\] la posizione del carattere all'inizio del blocco.  
  
 `dwListTypesRequested`  
 \[in\] i tipi di elenco necessari.  Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|SCRIPT\_CMPL\_NOLIST|0x0000|Nessun elenco.|  
|SCRIPT\_CMPL\_MEMBERLIST|0x0001|Elenco di membri.|  
|SCRIPT\_CMPL\_ENUMLIST|0x0002|Elenco di Enumeratori.|  
|SCRIPT\_CMPL\_PARAMLIST|0x0004|Elenco dei parametri del metodo.|  
|SCRIPT\_CMPL\_GLOBALLIST|0x0008|Elenco globale.|  
  
 Il tipo di SCRIPT\_CMPL\_GLOBALLIST viene considerato come elemento di completamento predefinito che può essere combinate utilizzando l'operatore OR con altri elementi di completamento.  Il motore di creazione di script viene innanzitutto tentata la compilazione delle informazioni sul tipo per altri elementi dell'elenco di completamento.  Se tale autenticazione non riesce, il motore popola per SCRIPT\_CMPL\_GLOBALLIST.  
  
 `pdwListTypesProvided`  
 \[out\] tipo di elenco fornito.  
  
 `pichListAnchorPosition`  
 \[out\] indirizzo di inizio di contesto contenente la posizione corrente.  Indice iniziale è relativo all'inizio del blocco.  
  
 Ciò viene visualizzato solo quando `dwListTypesRequested` include SCRIPT\_CMPL\_MEMBERLIST, SCRIPT\_CMPL\_ENUMLIST, o SCRIPT\_CMPL\_GLOBALLIST.  Per altri tipi di elenco, il risultato sarà indefinito.  
  
 `pichFuncAnchorPosition`  
 \[out\] indice iniziale della chiamata di funzione contenente la posizione corrente.  Indice iniziale è relativo all'inizio del blocco.  
  
 Ciò viene visualizzato solo quando il contesto contenente la posizione corrente è una chiamata di funzione e quando `dwListTypesRequested` include SCRIPT\_CMPL\_PARAMLIST.  In caso contrario, il risultato sarà indefinito.  
  
 `pmemid`  
 \[out\] Il MEMBERID della funzione, come definito da un tipo di parametro out `IProvideMultipleClassInfo``ppunk`.  
  
 Ciò viene visualizzato solo quando `dwListTypesRequested` include SCRIPT\_CMPL\_PARAMLIST.  
  
 `piCurrentParameter`  
 \[out\] indice del parametro contenente la posizione corrente.  Se la posizione corrente è il nome della funzione, \-1 viene restituito.  
  
 Il valore `piCurrentParameter` viene popolato solo quando `dwListTypesRequested` include SCRIPT\_CMPL\_PARAMLIST.  
  
 `ppunk`  
 Le informazioni sul tipo, che sono fornite sotto forma di oggetto `IProvideMultipleClassInfo`.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IProvideMultipleClassInfo>   
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)