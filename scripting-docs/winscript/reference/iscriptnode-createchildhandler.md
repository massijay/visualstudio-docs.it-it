---
title: "IScriptNode::CreateChildHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.CreateChildHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildHandler"
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IScriptNode::CreateChildHandler
Aggiunge uno scriptlet come istanze figlio `IScriptNode`.  
  
## Sintassi  
  
```  
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parametri  
 `pszDefaultName`  
 \[in\] indirizzo del nome predefinito da associare allo scriptlet.  
  
 `prgpszNames`  
 \[in, size\_is `cpszNames`\)\] Un elenco di identificatori dal nome completo dell'host.  
  
 `cpszNames`  
 \[in\] numero di identificatori nel parametro `prgpszNames`.  
  
 `pszEvent`  
 \[in\] indirizzo del buffer che identifica il nome di evento è associato allo scriptlet.  
  
 `pszDelimiter`  
 \[in\] indirizzo del delimitatore di entità finale\-de\-script\- blocco.  Per analizzare, l'host utilizza in genere un delimitatore \(come due virgolette singole\), per individuare la fine del blocco di script.  
  
 Il delimitatore abilita la pre\-elaborazione dal motore di creazione di script.  Ad esempio, il motore potrebbe sostituire una virgoletta con due virgolette semplici da utilizzare come delimitatore.  Il motore determina come delimitatore viene utilizzato.  
  
 Set FROM NULL se nessun delimitatore viene utilizzato per identificare la fine del blocco di script.  
  
 `ptiSignature`  
 \[in\] informazioni sui tipi per un oggetto funzione.  
  
 `iMethodSignature`  
 \[in\] indirizzo della funzione nel parametro `ITypeInfo``ptiSignature`.  
  
 `isn`  
 \[in\] indirizzo figlio nel padre.  
  
 `dwCookie`  
 \[in\] un valore definito dall'applicazione viene utilizzato per associare la voce con l'oggetto host.  
  
 `ppse`  
 \[out\] l'indirizzo di una variabile che riceve un puntatore a un'interfaccia `IScriptEntry` di istanze figlio.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Uno scriptlet specifica un gestore eventi.  Questo metodo crea uno scriptlet se viene chiamato da un oggetto `IScriptNode` che rappresenta una pagina Web.  Questo metodo non riesce se viene chiamato da altre interfacce.  
  
## Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)