---
title: "Implementazione di criteri di archiviazione dell&#39;analisi codice personalizzati per codice gestito | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.code.analysis.selecttfsrulesets"
  - "vs.code.analysis.browsefortfsruleset"
  - "vs.code.analysis.policyeditor"
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Implementazione di criteri di archiviazione dell&#39;analisi codice personalizzati per codice gestito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I criteri di archiviazione dell'analisi codice specificano un set di regole che membri di un progetto team devono eseguire su codice sorgente prima che venga archiviato nel controllo della versione.  Microsoft fornisce *set di regole* standard che raggruppano regole di analisi codice in aree funzionali.  I *set di regole dei criteri di archiviazione personalizzati* specificano un set di regole di analisi codice specifiche di un progetto team.  Un set di regole viene archiviato in un file con estensione ruleset.  
  
 I criteri di archiviazione vengono impostati al livello del progetto team e specificati in base al percorso di un file con estensione ruleset nella struttura ad albero del controllo della versione.  Non esistono restrizioni relative al percorso del controllo della versione per il set di regole personalizzate dei criteri del team.  
  
 L'analisi codice è configurata per singoli progetti di codice nella finestra delle proprietà di ogni progetto.  Un set di regole personalizzate per un progetto di codice viene specificato in base alla posizione fisica del file con estensione ruleset sul computer locale.  Quando per un file con estensione .ruleset che si trova sulla stessa unità del progetto di codice, Visual Studio utilizza un percorso relativo del file nella configurazione del progetto.  
  
 Una pratica consigliata per la creazione di un set di regole personalizzate per un progetto team consiste nell'archiviare il file con estensione ruleset dei criteri di archiviazione in una cartella speciale che non faccia parte di alcun progetto di codice.  Se si archivia il file in una cartella dedicata, è possibile applicare autorizzazioni che limitano la modifica del file di regole a determinati utenti e spostare facilmente la struttura di directory contenente il progetto in un'altra directory o un altro computer.  
  
## Creazione del set di regole di archiviazione personalizzate per il progetto team  
 Per creare un set di regole personalizzate per un progetto team, è necessario innanzitutto creare una cartella speciale per il set di regole dei criteri di archiviazione in **Esplora controllo codice sorgente**.  Si creerà quindi il file del set di regole e si aggiungerà il file al controllo della versione.  Infine si specificherà il set di regole come criteri di archiviazione dell'analisi codice per il progetto team.  
  
> [!NOTE]
>  Per creare una cartella in un progetto team, è necessario innanzitutto mappare la radice del progetto team a un percorso sul computer locale.  Per ulteriori informazioni, vedere [Create and work with workspaces \(old\)](http://msdn.microsoft.com/it-it/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### Per creare la cartella del controllo della versione per il set di regole dei criteri di archiviazione  
  
1.  In [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] espandere il nodo del progetto team, quindi fare clic su **Controllo del codice sorgente**.  
  
2.  Nel riquadro **Cartelle** fare clic con il pulsante destro del mouse sul progetto team, quindi scegliere **Nuova cartella**.  
  
3.  Nel riquadro Controllo del codice sorgente principale fare clic con il pulsante destro del mouse su **Nuova cartella**, scegliere **Rinomina** e digitare un nome per la cartella del set di regole.  
  
#### Per creare il set di regole dei criteri di archiviazione  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi fare clic su **File**.  
  
2.  Nell'elenco **Categorie** fare clic su **Generale**.  
  
3.  Nell'elenco **Modelli** fare doppio clic **Set di regole di analisi del codice**.  
  
4.  Specificare le regole da includere nel set di regole, quindi salvare il file del set di regole nella cartella del set di regole creata.  
  
     Per ulteriori informazioni, vedere [Creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
#### Per aggiungere il file del set di regole al controllo della versione  
  
1.  In **Esplora controllo codice sorgente** fare clic con il pulsante destro del mouse sulla nuova cartella e scegliere **Aggiungi elementi alla cartella**.  
  
     Per ulteriori informazioni, vedere [Utilizzare il controllo della versione](../Topic/Use%20version%20control.md).  
  
2.  Fare clic sul file del set di regole creato, quindi scegliere **Fine**.  
  
     Il file verrà aggiunto al controllo del codice sorgente ed estratto.  
  
3.  Nella finestra dei dettagli di **Esplora controllo codice sorgente** fare clic con il pulsante destro del mouse sul nome file, quindi scegliere **Archivia modifiche in sospeso**.  
  
4.  Nella finestra di dialogo **Archivia** è possibile aggiungere un commento, quindi scegliere **Archivia**.  
  
    > [!NOTE]
    >  Se sono già stati configurati criteri di archiviazione dell'analisi codice per il progetto team ed è stato selezionato **Consenti archiviazione dei soli file della soluzione corrente**, verrà generato un avviso di errore dei criteri.  Nella finestra di dialogo Errore criteri selezionare **Ignora errore criteri e continua archiviazione**.  Aggiungere un commento obbligatorio, quindi fare clic su **OK**.  
  
#### Per specificare il file del set di regole come criteri di archiviazione  
  
1.  Scegliere **Impostazioni progetto team** dal menu **Team**, quindi fare clic su **Controllo del codice sorgente**.  
  
2.  Fare clic su **Criteri di archiviazione**, quindi su **Aggiungi**.  
  
3.  Nell'elenco **Criteri di archiviazione** fare doppio clic **Analisi codice** e verificare che la casella di controllo **Attiva analisi del codice gestito** sia selezionata.  
  
4.  Nell'elenco **Esegui il set di regole** , fare clic su **\<Seleziona set di regole dal controllo del codice sorgente\>**.  
  
5.  Digitare il percorso del file del set di regole dei criteri di archiviazione nel controllo della versione  
  
     Il percorso deve rispettare la sintassi seguente:  
  
     **$\/** `TeamProjectName` **\/** `VersionControlPath`  
  
    > [!NOTE]
    >  È possibile copiare il percorso tramite una delle procedure riportate di seguito in **Esplora controllo codice sorgente**:  
  
    -   Nel riquadro **Cartelle** fare clic sulla cartella contenente il file del set di regole.  Copiare il percorso di controllo della versione della cartella visualizzato nella casella **Origine** e digitare manualmente il nome del file del set di regole.  
  
    -   Nella finestra dei dettagli fare clic con il pulsante destro del mouse sul file del set di regole e scegliere **Proprietà**.  Nella scheda **Generale** copiare il valore in **Nome server**.  
  
## Sincronizzazione dei progetti di codice con il set di regole dei criteri di archiviazione  
 Per specificare un set di regole dei criteri di archiviazione per il progetto team come set di regole di analisi codice della configurazione di un progetto di codice, utilizzare la finestra di dialogo delle proprietà del progetto di codice.  Se il set di regole si trova sulla stessa unità del progetto di codice, per specificare il set di regole quando si il percorso viene selezionato nella finestra di dialogo del file, viene utilizzato un percorso relativo.  Il percorso relativo rende portabili le impostazioni delle proprietà del progetto su altri computer che utilizzano simili strutture di controllo della versione locali.  
  
#### Per specificare un set di regole per il progetto team come set di regole di un progetto di codice  
  
1.  Se necessario, recuperare il file e la cartella del set di regole dei criteri di archiviazione dal controllo della versione.  
  
     È possibile eseguire questo passaggio in **Esplora controllo codice sorgente** facendo clic con il pulsante destro del mouse sulla cartella del set di regole e quindi scegliendo **Leggi ultima versione**.  
  
2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di codice, quindi scegliere **Proprietà**.  
  
3.  Fare clic su **Analisi codice**.  
  
4.  Se necessario, fare clic sulle opzioni appropriate negli elenchi **Configurazione** e **Piattaforma**.  
  
5.  Per eseguire l'analisi codice ogni volta che il progetto di codice viene compilato con la configurazione specificata, selezionare la casella di controllo **Attiva analisi codice in fase di compilazione \(definisce la costante CODE\_ANALYSIS\)**.  
  
6.  Per ignorare codice nei componenti di altre società, selezionare la casella di controllo **Non visualizzare i risultati del codice generato**.  
  
7.  Nell'elenco **Esegui il set di regole**, fare clic su **\<Sfoglia...\>**.  
  
8.  Specificare la versione locale del file del set di regole dei criteri di archiviazione.