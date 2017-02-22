---
title: "Funzione SccGetParentProjectPath | Microsoft Docs"
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
  - "SccGetParentProjectPath"
helpviewer_keywords: 
  - "Funzione SccGetParentProjectPath"
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Funzione SccGetParentProjectPath
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione determina il percorso del progetto padre di un progetto specificato. Questa funzione viene chiamata quando l'utente aggiunge un progetto di Visual Studio a controllo del codice sorgente.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] Il puntatore di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpUser  
 \[in, out\] Il nome utente \(fino a SCC\_USER\_SIZE, compreso il terminatore NULL\).  
  
 lpProjPath  
 \[in\] Stringa che identifica il percorso del progetto \(fino a SCC\_PRJPATH\_SIZE, compreso il terminatore NULL\).  
  
 lpAuxProjPath  
 \[in, out\] Stringa ausiliaria che identifica il progetto \(fino a SCC\_PRJPATH\_SIZE, compreso il terminatore NULL\).  
  
 lpParentProjPath  
 \[in, out\] Stringa di output che identifica il percorso del progetto padre \(fino a SCC\_PRJPATH\_SIZE, compreso il terminatore NULL\).  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Percorso del progetto padre è stata ottenuta correttamente.|  
|SCC\_E\_INITIALIZEFAILED|Impossibile inizializzare il progetto.|  
|SCC\_E\_INVALIDUSER|L'utente non può accedere al plug\-in del controllo del codice sorgente.|  
|SCC\_E\_UNKNOWNPROJECT|Progetto è sconosciuto per il plug\-in del controllo del codice sorgente.|  
|SCC\_E\_INVALIDFILEPATH|Percorso del file non valido o inutilizzabile.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_PROJSYNTAXERR|Sintassi non valida del progetto.|  
|SCC\_E\_CONNECTIONFAILURE|Problema di connessione di archivio.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Errore non specificato.|  
  
## Note  
 Questa funzione restituisce un codice di esito positivo o negativo e, se ha esito positivo, inserisce la variabile `lpParentProjPath` con il percorso di progetto completo per il progetto specificato.  
  
 Questa funzione restituisce l'elemento padre di percorso del progetto di un progetto esistente. Per il progetto di primo livello, la funzione restituisce il percorso del progetto che è stato passato \(vale a dire stesso progetto percorso radice\). Si noti che un percorso del progetto è una stringa che è significativa solo per il plug\-in del controllo del codice sorgente.  
  
 L'IDE è pronto ad accettare le modifiche per il `lpUser` e `lpAuxProjPath` anche parametri. L'IDE verrà mantenere queste stringhe e passarli al [SccOpenProject](../extensibility/sccopenproject-function.md) quando l'utente apre il progetto in futuro. Queste stringhe, pertanto, forniscono un modo per il plug\-in per le informazioni di traccia è necessario associare a un progetto di controllo del codice sorgente.  
  
 Questa funzione è simile al [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ad eccezione del fatto che non richiede all'utente di selezionare un progetto. Crea inoltre mai un nuovo progetto ma funziona solo con un progetto esistente.  
  
 Quando `SccGetParentProjectPath` viene chiamato, `lpProjPath` e `lpAuxProjPath` non sarà vuoto e corrisponde a un progetto valido. Queste stringhe sono in genere effettuate dall'IDE da una precedente chiamata al `SccGetProjPath` \(funzione\).  
  
 Il `lpUser` argomento è il nome utente. L'IDE verrà passato lo stesso nome utente che ha ricevuto in precedenza dal `SccGetProjPath` funzione e il plug\-in del controllo del codice sorgente deve utilizzare il nome come valore predefinito. Se l'utente ha già una connessione aperta con il plug\-in, il plug\-in deve provare a eliminare eventuali comandi per verificare che il funzionamento in modo invisibile. Tuttavia, se l'account di accesso non riesce, il plug\-in deve richiedere all'utente per un account di accesso e, quando riceve un account di accesso valido, passare il nome del nuovo `lpUser`. Perché il plug\-in possono modificare questa stringa, l'IDE verrà sempre allocare un buffer di dimensione \(`SCC_USER_LEN`\+ 1\). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido \(almeno come valido della stringa precedente\).  
  
## Note tecniche per SccCreateSubProject e SccGetParentProjectPath  
 Aggiunta di soluzioni e progetti al controllo del codice sorgente è stato semplificato in Visual Studio per ridurre al minimo il numero di volte in cui che un utente viene richiesto di selezionare i percorsi nel sistema di controllo di origine. Queste modifiche sono attivate da Visual Studio, se un controllo del codice sorgente del plug\-in supporta sia delle nuove funzioni, il [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) e `SccGetParentProjectPath` \(funzione\). Tuttavia, la seguente voce del Registro di sistema consente di disattivare queste modifiche e ripristinare il comportamento precedente di Visual Studio \(origine controllo plug\-in API versione 1.1\):  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl" \= DWORD: 00000001  
  
 Se questa voce del Registro di sistema non esiste o è impostata su DWORD: 00000000, Visual Studio tenta di utilizzare le nuove funzioni, `SccCreateSubProject`e`SccGetParentProjectPath`.  
  
 Se la voce del Registro di sistema è DWORD: 00000001, Visual Studio non tenta di utilizzare le nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)