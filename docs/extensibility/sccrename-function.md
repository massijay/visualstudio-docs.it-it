---
title: "Funzione SccRename | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccRename"
helpviewer_keywords: 
  - "Funzione SccRename"
ms.assetid: b467ade6-a1db-4c0b-b60f-7850ec4f79eb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzione SccRename
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione consente di rinominare un file nel sistema di controllo di origine.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccRename(  
   LPVOID pvContext,  
   HWND   hWnd,  
   LPCSTR lpFileName,  
   LPCSTR lpNewName  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpFileName  
 \[in\] Il nome file completo del file rinominato.  
  
 lpNewName  
 \[in\] Il nuovo nome completo. Se il percorso della directory è diverso, quindi il file è stato spostato da una sottodirectory a un altro.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|L'operazione di ridenominazione completata.|  
|SCC\_E\_PROJNOTOPEN|Il progetto non è aperto in controllo del codice sorgente.|  
|SCC\_E\_FILENOTCONTROLLED|Il file non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è autorizzato a completare l'operazione.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Impossibile creare il progetto come parte del processo di ridenominazione.|  
|SCC\_E\_OPNOTPERFORMED|Non è stata eseguita l'operazione.|  
|SCC\_E\_NONSPECIFICERROR|Si è verificato un errore non specificato o generale.|  
  
## Note  
 Questa funzione è utilizzabile per rinominare un file o lo spostamento da un percorso a un altro nel sistema di controllo di origine. Il plug\-in del controllo del codice sorgente non tentare di accedere al file su disco. È responsabilità dell'IDE per rinominare il file locale.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)