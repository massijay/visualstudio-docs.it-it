---
title: "File esterni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.newfile"
  - "VS.OpenWith"
  - "MiscellaneousFilesProject"
helpviewer_keywords: 
  - "soluzioni, file esterni"
  - "compilazioni [Visual Studio ALM], file esterni"
  - "file autonomi"
  - "Esplora soluzioni, file esterni"
  - "File esterni (cartella)"
  - "file [Visual Studio], esterni ai contenitori"
  - "file [Visual Studio], cartella File esterni"
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
caps.latest.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# File esterni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile utilizzare gli editor di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per lavorare in modo indipendente sui file di un progetto o di una soluzione.  Quando è aperta una soluzione, è possibile aprire e modificare file senza aggiungerli a un progetto o a una soluzione.  I file su cui si interviene indipendentemente dai contenitori sono chiamati file esterni.  Questi file si trovano al di fuori di soluzioni e progetti, non sono inclusi nelle compilazioni e non possono fare parte di una soluzione inclusa nel controllo del codice sorgente.  
  
 L'apertura di file in modo indipendente da un contenitore risulta utile per diverse ragioni.  Può, ad esempio, verificarsi il caso in cui, mentre si sviluppa una soluzione basata su un progetto, si desideri visualizzare un file che non è parte integrante dello sviluppo della soluzione.  Esempi tra i più comuni includono note o istruzioni di sviluppatori, schemi di database e parti di codice.  Inoltre, può essere necessario creare un file autonomo.  
  
 ![Progetti di soluzioni](~/ide/reference/media/projects_solutions_misc.gif "Projects\_Solutions\_Misc")  
  
 Se le opzioni relative alla cartella sono attivate, in Esplora soluzioni può essere visualizzata una cartella File esterni per i file.  È possibile impostare le opzioni in [Documenti, Ambiente, finestra di dialogo Opzioni](../../ide/reference/documents-environment-options-dialog-box.md).  Una volta chiuso un file esterno, questo non verrà associato ad alcuna particolare soluzione o alcun particolare progetto, a meno che non sia stata attivata anche in questo caso la relativa opzione.  
  
 Nella cartella File esterni i file sono rappresentati come collegamenti.  Nonostante questa cartella non faccia parte di una soluzione, all'apertura di una soluzione verranno riaperti alcuni o tutti i file esterni che risultavano aperti l'ultima volta che la soluzione era stata chiusa, in base alle impostazioni relative alla cartella.  
  
> [!NOTE]
>  Alcuni dei file che non vengono visualizzati nella cartella File esterni sono file che non possono essere modificati all'interno dell'IDE, come file con estensione zip e doc.  L'IDE non tiene traccia dei file che possono essere modificati solo utilizzando un editor esterno.  
  
## Comandi disponibili nell'IDE  
 I menu, le barre degli strumenti e i comandi contenuti nell'ambiente di sviluppo cambiano in base al formato del file che viene aperto.  Quando si apre un file di testo, ad esempio, viene visualizzata la barra degli strumenti dell'editor di testo e sono disponibili i relativi comandi.  Successivamente, se si apre un file XML Schema, viene visualizzata la relativa barra degli strumenti.  Durante la modifica dello schema XML, né i comandi della barra degli strumenti dell'editor di testo né la barra degli strumenti stessa sono disponibili.  Lo schema XML costituisce la finestra attiva, e come tale, presenta il contesto della selezione corrente.  Quando si passa da un file di progetto a un file esterno, tutti i comandi relativi al progetto non saranno disponibili e verranno visualizzati solo quelli direttamente correlati al file esterno.  
  
## Opzioni per la visualizzazione delle cartelle  
 È possibile impostare le opzioni di visualizzazione per la cartella File esterni in modo che tale cartella venga visualizzata anche se non è stato aperto alcun file esterno.  Con il file della soluzione non viene gestito in modo permanente un elenco di file esterni.  Grazie a una funzionalità opzionale viene memorizzato l'elenco dei file utilizzati di recente da ciascun utente.  
  
## Vedere anche  
 [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)   
 [Documenti, Ambiente, finestra di dialogo Opzioni](../../ide/reference/documents-environment-options-dialog-box.md)