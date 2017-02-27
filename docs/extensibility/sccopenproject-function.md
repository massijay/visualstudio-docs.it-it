---
title: "Funzione SccOpenProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccOpenProject"
helpviewer_keywords: 
  - "Funzione SccOpenProject"
ms.assetid: d609510b-660a-46d7-b93d-2406df20434d
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Funzione SccOpenProject
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione apre un progetto di controllo di origine esistente o ne crea uno nuovo.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccOpenProject (  
   LPVOID        pvContext,  
   HWND          hWnd,  
   LPSTR         lpUser,  
   LPCSTR        lpProjName,  
   LPCSTR        lpLocalProjPath,  
   LPSTR         lpAuxProjPath,  
   LPCSTR        lpComment,  
   LPTEXTOUTPROC lpTextOutProc,  
   LONG          dwFlags  
);  
```  
  
#### Parametri  
 pvContext  
 \[in\] La struttura di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpUser  
 \[in, out\] Il nome dell'utente \(che non devono superare SCC\_USER\_SIZE, compreso il terminatore NULL\).  
  
 lpProjName  
 \[in\] Stringa che identifica il nome del progetto.  
  
 lpLocalProjPath  
 \[in\] Il percorso alla cartella di lavoro per il progetto.  
  
 lpAuxProjPath  
 \[in, out\] Stringa facoltativa ausiliaria che identifica il progetto \(non devono superare SCC\_AUXPATH\_SIZE, compreso il terminatore NULL\).  
  
 lpComment  
 \[in\] Impostare come commento a un nuovo progetto da creare.  
  
 lpTextOutProc  
 \[in\] Una funzione di callback facoltativo per visualizzare il testo di output di plug\-in del controllo del codice sorgente.  
  
 dwFlags  
 \[in\] Segnala se un nuovo progetto deve essere creato se il progetto è sconosciuto all'origine del controllo plug\-in. Valore può essere una combinazione di `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN.`  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Esito positivo in aprendo il progetto.|  
|SCC\_E\_INITIALIZEFAILED|Impossibile inizializzare il progetto.|  
|SCC\_E\_INVALIDUSER|L'utente non è grado di accedere al sistema di controllo di origine.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Il progetto non esisteva prima della chiamata.  il `SCC_OPT_CREATEIFNEW` è stato impostato, ma il progetto non è stato creato.|  
|SCC\_E\_PROJSYNTAXERR|Sintassi non valida del progetto.|  
|SCC\_E\_UNKNOWNPROJECT|Il progetto è sconosciuto per il controllo del codice sorgente plug\-in e `SCC_OPT_CREATEIFNEW` flag non è stato impostato.|  
|SCC\_E\_INVALIDFILEPATH|Percorso del file non valido o inutilizzabile.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_NONSPECFICERROR|Un errore non specificato. il controllo del codice sorgente non è stato inizializzato.|  
  
## Note  
 L'IDE può passare un nome utente \(`lpUser`\), o può semplicemente passare un puntatore a una stringa vuota. Se è presente un nome utente, il plug\-in del controllo del codice sorgente necessario utilizzarlo come valore predefinito. Tuttavia, se è stato passato alcun nome o l'account di accesso non riuscito con il nome specificato, il plug\-in deve richiedere all'utente di accesso e restituirà il nome valido in `lpUser` quando riceve un account di accesso valido`.` perché il plug\-in possono modificare la stringa del nome utente, l'IDE verrà sempre allocare un buffer di dimensione \(`SCC_USER_LEN`\+ 1 o SCC\_USER\_SIZE, che include lo spazio per il carattere di terminazione null\).  
  
> [!NOTE]
>  La prima azione IDE potrebbe essere necessario eseguire può essere una chiamata al `SccOpenProject` funzione o [SccGetProjPath](../extensibility/sccgetprojpath-function.md). Per questo motivo, entrambe riportano identica `lpUser` parametro.  
  
 `lpAuxProjPath` e`lpProjName` vengono letti dal file di soluzione, o vengono restituiti da una chiamata al `SccGetProjPath` \(funzione\). Questi parametri contengono le stringhe che associa il controllo del codice sorgente del plug\-in al progetto e sono significativi solo per il plug\-in. Se non tali stringhe nel file di soluzione e l'utente non è stato richiesto di passare \(che restituirà una stringa tramite il `SccGetProjPath` funzione\), l'IDE passa stringhe vuote per entrambi `lpAuxProjPath` e `lpProjName`, e non prevede questi valori da aggiornare tramite il plug\-in quando questa funzione restituisce.  
  
 `lpTextOutProc` è un puntatore a una funzione di callback fornito dall'IDE per il controllo del codice sorgente del plug\-in per la visualizzazione dell'output di risultato del comando. Questa funzione di callback è descritto dettagliatamente in [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
> [!NOTE]
>  Se il plug\-in del controllo del codice sorgente intende sfruttare i vantaggi di questo, è necessario impostare il `SCC_CAP_TEXTOUT` flag nel [SccInitialize](../extensibility/sccinitialize-function.md). Se questo flag non è stata impostata o se l'IDE non supporta questa funzionalità, `lpTextOutProc` sarà `NULL`.  
  
 Il `dwFlags` parametro controlla il risultato nel caso in cui il progetto viene aperto non esiste. È costituito da due flag di bit, `SCC_OP_CREATEIFNEW` e `SCC_OP_SILENTOPEN`. Se esiste il progetto è già aperto, la funzione semplicemente il progetto verrà aperto e restituisce `SCC_OK`. Se il progetto non esiste e se il `SCC_OP_CREATEIFNEW` flag è attivato, il plug\-in del controllo del codice sorgente può creare il progetto nel sistema di controllo di origine, aprirlo e restituire `SCC_OK`. Se il progetto non esiste e se il `SCC_OP_CREATEIFNEW` flag è disattivata, il plug\-in deve quindi verificare la presenza di `SCC_OP_SILENTOPEN` flag. Se questo flag non è abilitata, il plug\-in potrebbe richiedere all'utente un nome di progetto. Se tale flag è attivato, il plug\-in deve semplicemente indicare `SCC_E_UNKNOWNPROJECT`.  
  
## Ordine di chiamata  
 Durante il normale funzionamento degli eventi, il [SccInitialize](../extensibility/sccinitialize-function.md) potrebbe essere chiamato per primo per avviare una sessione di controllo di origine. Una sessione può essere costituita da una chiamata a `SccOpenProject`, seguito da altre chiamate di funzioni API plug\-in controllo di origine e terminerà con una chiamata al [SccCloseProject](../extensibility/scccloseproject-function.md). Tali sessioni possono essere ripetuti più volte prima di [SccUninitialize](../extensibility/sccuninitialize-function.md) viene chiamato.  
  
 Se il controllo origine set di plug\-in di `SCC_CAP_REENTRANT` bit `SccInitialize`, quindi la sequenza di una sessione precedente può essere ripetuta più volte in parallelo. Diversi `pvContext` strutture di tenere traccia delle sessioni diverse, in cui ogni `pvContext` è associata a un progetto aperto in un momento. In base il`pvContext` parametro, il plug\-in grado di determinare il progetto in cui viene fatto riferimento in qualsiasi particolare chiamata. Se la funzionalità di bit `SCC_CAP_REENTRANT` non è impostata, nonreentrant plug\-in del controllo codice sorgente sono limitate per la capacità di lavorare con più progetti.  
  
> [!NOTE]
>  Il `SCC_CAP_REENTRANT` bit è stato introdotto nella versione 1.1 dell'API dei plug\-in controllo di origine. Non è impostata oppure viene ignorato nella versione 1.0 e vengono considerate come nonreentrant tutti versione 1.0 origine plug\-in del controllo.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCloseProject](../extensibility/scccloseproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)   
 [SccInitialize](../extensibility/sccinitialize-function.md)   
 [SccUninitialize](../extensibility/sccuninitialize-function.md)   
 [Limitazioni sulle lunghezze di stringa](../extensibility/restrictions-on-string-lengths.md)   
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)