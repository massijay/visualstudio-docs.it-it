---
title: "Selezione e la valuta nell&#39;IDE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "valuta, IDE di Visual Studio"
  - "IDE, selezione"
  - "selezione, l'IDE di Visual Studio"
  - "IDE, valuta"
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Selezione e la valuta nell&#39;IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato \(IDE\) gestisce informazioni degli utenti oggetti attualmente selezionati tramite selezione *contesto*. Con il contesto di selezione, package VS possono essere incluse nella valuta di rilevamento in due modi:  
  
-   Per la propagazione dei informazioni valuta il package VS all'IDE.  
  
-   Monitorando le selezioni attualmente attive degli utenti all'interno dell'IDE.  
  
## Contesto della selezione  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalmente tiene traccia della valuta IDE nell'oggetto contesto selezione globale. Nella tabella seguente vengono mostrati gli elementi che costituiscono il contesto della selezione.  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Gerarchia corrente.|In genere il progetto corrente. una gerarchia corrente NULL indica che la soluzione nel suo complesso è corrente.|  
|ID elemento corrente|L'elemento selezionato all'interno della gerarchia corrente; Quando sono presenti più selezioni in una finestra del progetto, possono esistere più elementi correnti.|  
|Corrente `SelectionContainer`|Contiene uno o più oggetti per cui la finestra proprietà dovrebbe visualizzare le proprietà.|  
  
 Inoltre, l'ambiente gestisce due elenchi globali:  
  
-   Un elenco di identificatori di comando attivi dell'interfaccia utente  
  
-   Un elenco di tipi di elementi attualmente attivo.  
  
### Selezione e tipi di finestra  
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organizzati due tipi generali di windows:  
  
-   Windows tipo di gerarchia  
  
-   Finestre cornice, ad esempio finestre degli strumenti e documenti  
  
 L'IDE valuta tiene traccia in modo diverso per ognuno di questi tipi di finestra.  
  
 La finestra di tipo di progetto più comune è Esplora soluzioni, che controlla l'IDE. Una finestra del tipo di progetto tiene traccia della gerarchia globale e l'ID del contesto di selezione globale e la finestra si basa sulla selezione dell'utente per determinare la gerarchia corrente. Per windows di tipo di progetto, l'ambiente fornisce il servizio globale <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, tramite i package VS possibile monitorare i valori correnti per gli elementi aperti. Proprietà di navigazione nell'ambiente dipende da questo servizio globale.  
  
 Finestre cornice, utilizzano d'altra parte, dell'oggetto documento all'interno della finestra cornice per inserire il valore di SelectionContext \(il trio di gerarchia\/ItemID\/SelectionContainer\). . Finestre cornice usare il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> a questo scopo. Dell'oggetto documento può inserire solo i valori per il contenitore di selezione, lasciando i valori locali per la gerarchia e ItemID invariato, come avviene per i documenti figlio MDI.  
  
### Eventi e valuta  
 Potrebbero verificarsi due tipi di eventi che influiscono sulla nozione dell'ambiente di valuta:  
  
-   Eventi che sono stati propagati a livello globale e cambiare il contesto di selezione cornice di finestra. Esempi di questo tipo di evento includono una finestra figlio MDI viene aperta una finestra degli strumenti globale in corso l'apertura o una finestra degli strumenti del tipo di progetto viene aperto.  
  
-   Eventi che modificano gli elementi tracciati all'interno del contesto di selezione cornice di finestra. Esempi includono la modifica di selezione all'interno di DocObject o selezione in una finestra del tipo di progetto.  
  
## Vedere anche  
 [Selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md)   
 [Commenti e suggerimenti all'utente](../../extensibility/internals/feedback-to-the-user.md)