---
title: "Funzione SccRunScc | Microsoft Docs"
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
  - "SccRunScc"
helpviewer_keywords: 
  - "Funzione SccRunScc"
ms.assetid: bbe7c931-b17a-4779-9cf6-59e5f9f0c172
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccRunScc
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione richiama lo strumento di amministrazione di controllo di origine.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccRunScc(  
   LPVOID  pvContext,  
   HWND    hWnd,  
   LONG    nFiles,  
   LPCSTR* lpFileNames  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 nFiles  
 \[in\] Numero di file specificato per il `lpFileNames` matrice.  
  
 lpFileNames  
 \[in\] Matrice di nomi di file selezionato.  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Lo strumento di amministrazione di controllo di origine è stato richiamato correttamente.|  
|SCC\_I\_OPERATIONCANCELED|L'operazione è stata annullata.|  
|SCC\_E\_INITIALIZEFAILED|Impossibile inizializzare il controllo del codice sorgente.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete.|  
|SCC\_E\_CONNECTIONFAILURE|Impossibile connettersi al sistema di controllo di origine.|  
|SCC\_E\_FILENOTCONTROLLED|Il file selezionato non è incluso nel controllo del codice sorgente.|  
|SCC\_E\_NONSPECIFICERROR|Errore non specificato.|  
  
## Note  
 Questa funzione consente al chiamante di accedere all'intera gamma di funzionalità del sistema di controllo di origine tramite uno strumento esterno. Se il sistema di controllo di origine non dispone di alcuna interfaccia utente, il plug\-in del controllo del codice sorgente può implementare un'interfaccia per eseguire funzioni amministrative necessarie.  
  
 Questa funzione viene chiamata con un conteggio e una matrice di nomi di file per i file attualmente selezionati. Se supporta lo strumento di amministrazione, è possibile utilizzare l'elenco di file per preselezionare file nell'interfaccia di amministrazione; in caso contrario, l'elenco può essere ignorato.  
  
 In genere, questa funzione viene richiamata quando l'utente seleziona il **avvio \< Server di controllo di origine \>** dal **File** \-\> **controllo del codice sorgente** menu. Questo **avviare** opzione di menu può essere sempre disabilitata o persino nascosti impostando una voce del Registro di sistema. Per informazioni dettagliate, vedere [Procedura: installare un plug\-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md). Questa funzione viene chiamata solo se [SccInitialize](../extensibility/sccinitialize-function.md) restituisce il `SCC_CAP_RUNSCC` bit funzionalità \(vedere [Flag di capacità](../extensibility/capability-flags.md) per informazioni dettagliate su questo e gli altri bit funzionalità\).  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [Procedura: installare un plug\-in del controllo del codice sorgente](../extensibility/internals/how-to-install-a-source-control-plug-in.md)   
 [Flag di capacità](../extensibility/capability-flags.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)