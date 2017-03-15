---
title: "Creazione di cartelle del contenitore padre per le soluzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "soluzioni, la creazione di contenitori padre"
  - "origine plug-in del controllo, la creazione di contenitori padre"
ms.assetid: 961e68ed-2603-4479-a306-330eda2b2efa
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Creazione di cartelle del contenitore padre per le soluzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nella versione 1,2 di plug\-in controllo del codice sorgente API, un utente può specificare una sola destinazione radice del controllo del codice sorgente per tutti i progetti Web nella soluzione.  Questa radice viene chiamata una radice unificata super \(SUR\).  
  
 Nella versione 1,1 di plug\-in controllo del codice sorgente API, se l'utente aggiunge una soluzione di multiproject al controllo del codice sorgente, l'utente è stato richiesto di specificare una destinazione del controllo del codice sorgente per ogni progetto Web.  
  
## nuovi flag di funzionalità  
 `SCC_CAP_CREATESUBPROJECT`  
  
 `SCC_CAP_GETPARENTPROJECT`  
  
## nuove funzioni  
 [SccCreateSubProject](../../extensibility/scccreatesubproject-function.md)  
  
 [SccGetParentProjectPath](../../extensibility/sccgetparentprojectpath-function.md)  
  
 L'ide di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] crea quasi sempre una cartella di SUR quando si aggiunge una soluzione al controllo del codice sorgente.  In particolare, viene eseguita questa operazione nei seguenti casi:  
  
-   Il progetto è un progetto Web di condivisione di file.  
  
-   Esistono unità del progetto e il file della soluzione.  
  
-   Esistono condivisioni del progetto e il file della soluzione.  
  
-   I progetti sono stati aggiunti separatamente in una soluzione di controllo\).  
  
 In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene suggerito dal nome della cartella di SUR corrisponda al nome della soluzione senza estensione.  Nella tabella seguente viene riepilogato il comportamento delle due versioni.  
  
|Funzionalità|versione 1,1 del plug\-in API del controllo di tSource|Versione 1,2 di plug\-in controllo del codice sorgente API|  
|------------------|------------------------------------------------------------|----------------------------------------------------------------|  
|aggiungere la soluzione a SCC|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccOpenProject\(\)|SccInitialize\(\)<br /><br /> SccGetProjPath\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccCreateSubProject\(\)<br /><br /> SccOpenProject\(\)|  
|Aggiungere il progetto alla soluzione di controllo|SccGetProjPath\(\)<br /><br /> OpenProject\(\)|SccGetParentProjectPath\(\)<br /><br /> SccOpenProject\(\) **Note:**  Visual Studio si presuppone che una soluzione sia un elemento figlio diretto di SUR.|  
  
## Esempi  
 Nella seguente tabella sono riportati due esempi.  In entrambi i casi, l'utente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene richiesto il percorso di destinazione per la soluzione nel controllo del codice sorgente fino a specificare *user\_choice* come destinazione. Quando il user\_choice è specificato, la soluzione e due progetti vengono aggiunti senza richiedere all'utente per le destinazioni del controllo del codice sorgente.  
  
|la soluzione contiene|Le posizioni del disco|Struttura di impostazione predefinita del database|  
|---------------------------|----------------------------|--------------------------------------------------------|  
|sln1.sln<br /><br /> Web1<br /><br /> Web2|C\#: \\Solutions \\ sln1<br /><br /> C\#: \\Inetpub\\wwwroot\\Web 1<br /><br /> \\ \\ server \\ wwwroot$ \\ web2|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/C\/Web1<br /><br /> $*user\_choice*\/Web2|  
|sln1.sln<br /><br /> Web1<br /><br /> Win1|C\#: \\Solutions \\ sln1<br /><br /> d: \\Inetpub\\wwwroot\\Web 1<br /><br /> C\#: \\solutions\\sln1\\Win 1|$*user\_choice*\/sln1<br /><br /> $*user\_choice*\/D\/web1<br /><br /> $*user\_choice*\/sln1\/win1|  
  
 La cartella e le sottocartelle di SUR vengono create indipendentemente dal fatto che l'operazione viene annullata o negativo a causa di un errore.  Automaticamente non vengono rimossi nell'annullamento o nelle condizioni di errore.  
  
 impostazioni predefinite di[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] alla versione comportamento 1,1 se il plug\-in controllo del codice sorgente non restituisce `SCC_CAP_CREATESUBPROJECT` e i flag di funzionalità di `SCC_CAP_GETPARENTPROJECT` .  Inoltre, gli utenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono scegliere per ripristinare il comportamento della versione 1,1 impostando il valore della chiave seguente a dword: 00000001:  
  
 \[\=dword HKEY\_CURRENT\_USER \\Software\\Microsoft\\VisualStudio\\8.0\\SourceControl\] "DoNotCreateSolutionRootFolderInSourceControl ": 00000001  
  
## Vedere anche  
 [Novità di origine controllo plug\-in API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)