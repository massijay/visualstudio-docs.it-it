---
title: "IScriptNode:: CreateChildEntry | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode. CreateChildEntry
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::CreateChildEntry"
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# IScriptNode:: CreateChildEntry
Aggiunge un'istanza figlio `IScriptEntry`.  
  
## Sintassi  
  
```  
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parametri  
 `isn`  
 \[in\] indirizzo figlio nel padre.  
  
 `dwCookie`  
 \[in\] un valore definito dall'applicazione utilizzata per associare la voce figlio con l'oggetto host.  
  
 `pszDelimiter`  
 \[in\] indirizzo del delimitatore di entità finale\-de\-script\- blocco.  Per analizzare, l'host utilizza in genere un delimitatore \(come due virgolette singole\), per individuare la fine del blocco di script.  
  
 Il delimitatore consente al motore di creazione di script per fornire la pre\-elaborazione.  Ad esempio, il motore potrebbe sostituire una virgoletta con due virgolette semplici da utilizzare come delimitatore.  Il motore determina come delimitatore viene utilizzato.  
  
 Set FROM NULL se un delimitatore non contrassegna la fine del blocco di script.  
  
 `ppse`  
 \[out\] l'indirizzo di una variabile che riceve un puntatore a un'interfaccia `IScriptEntry` di istanze figlio.  
  
 Per gli oggetti `IScriptNode` che rappresentano una pagina Web, completamento del parametro un'istanza `IScriptEntry` che specifica un blocco di script.  
  
 Per gli oggetti `IScriptEntry` che rappresentano un blocco di script, completamento del parametro un'istanza `IScriptEntry` che specifica un oggetto funzione.  
  
 Per gli oggetti `IScriptEntry` che rappresentano un oggetto funzione, non riuscire di questo metodo.  
  
 Per gli oggetti `IScriptScriptlet`, questo metodo non riesce.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 L'interfaccia `IScriptNode` rappresenta una pagina Web o i relativi elementi.  L'interfaccia `IScriptEntry` \(derivata da `IScriptNode`\) rappresenta un blocco di script o un oggetto funzione.  L'interfaccia `IScriptScriptlet` \(derivata da `IScriptEntry`\) rappresenta un gestore eventi.  
  
## Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)