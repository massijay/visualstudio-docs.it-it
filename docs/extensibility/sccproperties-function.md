---
title: "Funzione SccProperties | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccProperties"
helpviewer_keywords: 
  - "Funzione SccProperties"
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccProperties
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di visualizzare proprietà di controllo di origine per un file o progetto.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccProperties (  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpFileName  
 \[in\] Il nome e percorso completo del file o progetto.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Le proprietà sono state visualizzate correttamente.|  
|SCC\_I\_RELOADFILE|Il sistema di controllo della versione ha modificato le proprietà di file, in modo l'IDE deve caricare questo file.|  
|SCC\_E\_PROJNOTOPEN|Il progetto specificato non è stato aperto nel controllo del codice sorgente.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è autorizzato a visualizzare le proprietà del file o progetto.|  
|SCC\_E\_FILENOTCONTROLLED|Il progetto o al file specificato non è sotto controllo del codice sorgente.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Si è verificato un errore sconosciuto o generale.|  
  
## Note  
 Il plug\-in del controllo del codice sorgente consente di visualizzare le proprietà in una finestra di dialogo.  
  
 Le proprietà sono definite per il plug\-in del controllo del codice sorgente e possono differire dal plug\-in a plug\-in. Se il plug\-in consente all'utente di modificare le proprietà del controllo di origine di un file, deve restituire `SCC_I_RELOAD` per segnalare l'IDE in cui il file o il progetto deve essere ricaricato.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)