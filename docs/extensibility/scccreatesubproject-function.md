---
title: "Funzione SccCreateSubProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SccCreateSubProject"
helpviewer_keywords: 
  - "Funzione SccCreateSubProject"
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 19
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 19
---
# Funzione SccCreateSubProject
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa funzione crea un sottoprogetto con il nome specificato in un progetto padre esistente specificato per il `lpParentProjPath` argomento.  
  
## Sintassi  
  
```cpp#  
SCCRTN SccCreateSubProject(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpParentProjPath,  
   LPCSTR lpSubProjName,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpSubProjPath  
);  
```  
  
#### Parametri  
 pContext  
 \[in\] Il puntatore di contesto plug\-in del controllo di origine.  
  
 hWnd  
 \[in\] Handle di finestra IDE che il plug\-in del controllo del codice sorgente è possibile utilizzare come padre per finestre di dialogo che fornisce.  
  
 lpUser  
 \[in, out\] Il nome utente \(fino a SCC\_USER\_SIZE, compreso il terminatore NULL\).  
  
 lpParentProjPath  
 \[in\] Stringa che identifica il percorso del progetto principale \(fino a SCC\_PRJPATH\_SIZE, compreso il terminatore NULL\).  
  
 lpSubProjName  
 \[in\] Il nome suggerito sottoprogetto \(fino a SCC\_PRJPATH\_SIZE, compreso il terminatore NULL\).  
  
 lpAuxProjPath  
 \[in, out\] Stringa ausiliaria che identifica il progetto \(fino a SCC\_PRJPATH\_SIZE, compreso il terminatore NULL\).  
  
 lpSubProjPath  
 \[in, out\] Stringa di output che identifica il percorso per il sottoprogetto \(fino a SCC\_PRJPATH\_SIZE, compreso il terminatore NULL\).  
  
## Valore restituito  
 Implementazione di plug\-in controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:  
  
|Valore|Descrizione|  
|------------|-----------------|  
|SCC\_OK|Sottoprogetto è stato creato correttamente.|  
|SCC\_E\_INITIALIZEFAILED|Impossibile inizializzare il progetto principale.|  
|SCC\_E\_INVALIDUSER|L'utente non è grado di accedere al sistema di controllo di origine.|  
|SCC\_E\_COULDNOTCREATEPROJECT|Impossibile creare il sottoprogetto.|  
|SCC\_E\_PROJSYNTAXERR|Sintassi non valida del progetto.|  
|SCC\_E\_UNKNOWNPROJECT|Il progetto padre è sconosciuto per il plug\-in del controllo del codice sorgente.|  
|SCC\_E\_INVALIDFILEPATH|Percorso del file non valido o inutilizzabile.|  
|SCC\_E\_NOTAUTHORIZED|L'utente non è possibile eseguire questa operazione.|  
|SCC\_E\_ACCESSFAILURE|Si è verificato un problema di accesso di sistema di controllo di origine, probabilmente a causa di problemi di contesa o di rete. È consigliabile un nuovo tentativo.|  
|SCC\_E\_CONNECTIONFAILURE|Si è verificato un problema di connessione del plug\-in controllo di origine.|  
|SCC\_E\_NONSPECIFICERROR<br /><br /> SCC\_E\_UNKNOWNERROR|Errore non specificato.|  
  
## Note  
 Se esiste già un sottoprogetto con il nome, la funzione può modificare il nome predefinito per creare uno univoco, ad esempio aggiungendo "\_ \< numero \>". Il chiamante deve essere preparato ad accettare le modifiche ai `lpUser`, `lpSubProjPath`, e `lpAuxProjPath`. Il `lpSubProjPath` e`lpAuxProjPath` argomenti vengono quindi utilizzati in una chiamata al [SccOpenProject](../extensibility/sccopenproject-function.md). Non devono essere modificati dal chiamante al momento della restituzione. Queste stringhe offrono un modo per il plug\-in per tenere traccia delle informazioni che è necessario associare a un progetto di controllo del codice sorgente. Il chiamante IDE non verrà visualizzati questi due parametri al momento della restituzione, in quanto il plug\-in può utilizzare una stringa formattata che potrebbe non essere appropriata per la visualizzazione. La funzione restituisce un codice di esito positivo o negativo e, se ha esito positivo, inserisce la variabile `lpSubProjPath` con il percorso di progetto completo per il nuovo progetto.  
  
 Questa funzione è simile al [SccGetProjPath](../extensibility/sccgetprojpath-function.md), ad eccezione del fatto che viene creato automaticamente un progetto, anziché richiedere all'utente di selezionare uno. Quando il `SccCreateSubProject` funzione viene chiamata, `lpParentProjName` e `lpAuxProjPath` non sarà vuoto e corrisponde a un progetto valido. Queste stringhe sono in genere effettuate dall'IDE da una precedente chiamata al `SccGetProjPath` funzione o [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 Il `lpUser` argomento è il nome utente. L'IDE verrà passato lo stesso nome utente che ha ricevuto in precedenza da `SccGetProjPath`, e il plug\-in del controllo del codice sorgente deve utilizzare il nome come valore predefinito. Se l'utente ha già una connessione aperta con il plug\-in, il plug\-in deve provare a eliminare eventuali comandi per verificare che il funzionamento in modo invisibile. Tuttavia, se l'account di accesso non riesce, il plug\-in deve richiedere all'utente per un account di accesso e, quando riceve un account di accesso valido, passare il nome del nuovo `lpUser`. Poiché il plug\-in possono modificare questa stringa, l'IDE verrà sempre allocare un buffer di dimensione \(SCC\_USER\_LEN \+ 1 o SCC\_USER\_SIZE, che include lo spazio per il carattere di terminazione null\). Se la stringa viene modificata, la nuova stringa deve essere un nome di account di accesso valido \(almeno come valido della stringa precedente\).  
  
## Note tecniche per SccCreateSubProject e SccGetParentProjectPath  
 Aggiunta di soluzioni e progetti al controllo del codice sorgente è stato semplificato in Visual Studio per ridurre al minimo il numero di volte in cui che un utente viene richiesto di selezionare i percorsi nel sistema di controllo di origine. Queste modifiche sono attivate da Visual Studio, se un controllo del codice sorgente del plug\-in supporta sia delle nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath`. Tuttavia, è possibile utilizzare la seguente voce del Registro di sistema per disabilitare queste modifiche e tornare al comportamento precedente di Visual Studio \(origine controllo plug\-in API versione 1.1\):  
  
 \[HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl" \= DWORD: 00000001  
  
 Se questa voce del Registro di sistema non esiste o è impostata su DWORD: 00000000, Visual Studio tenta di utilizzare le nuove funzioni, `SccCreateSubProject` e `SccGetParentProjectPath`.  
  
 Se la voce del Registro di sistema è DWORD: 00000001, Visual Studio non tenta di utilizzare le nuove funzioni e le operazioni di aggiunta al controllo del codice sorgente funzionano come nelle versioni precedenti di Visual Studio.  
  
## Vedere anche  
 [Funzioni API plug\-in del controllo sorgente](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)