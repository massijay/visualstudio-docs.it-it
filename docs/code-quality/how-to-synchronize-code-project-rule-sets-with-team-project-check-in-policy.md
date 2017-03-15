---
title: "Procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.selecttfsruleset"
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Procedura: sincronizzare i set di regole del progetto di codice con i criteri di archiviazione del progetto team
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sincronizzare le impostazioni dell'analisi del codice per i progetti di codice ai criteri di archiviazione per il progetto team specificando un set di regole che contiene almeno le regole specificate nel set di regole per i criteri di archiviazione.  Lo sviluppatore responsabile offre informazioni su nome e percorso del set di regole per i criteri di archiviazione.  È possibile utilizzare una delle opzioni seguenti per assicurarsi che l'analisi del codice per il progetto utilizzi il set di regole corretto:  
  
-   Se i criteri di archiviazione utilizzano un set di regole incorporate Microsoft, aprire la finestra di dialogo delle proprietà per il progetto di codice, visualizzare la pagina Analisi codice e selezionare il set di regole nella pagina Analisi codice delle impostazioni del progetto di codice.  I set di regole standard Microsoft vengono installati automaticamente con Visual Studio, sono di sola lettura e non devono essere modificati.  Se i set di regole non vengono modificati, la corrispondenza delle regole nei set di regole locali e dei criteri è garantita.  
  
-   Se i criteri di archiviazione utilizzano un set di regole personalizzato, eseguire un'operazione get nel file del set di regole nel controllo della versione per creare una copia locale.  Quindi specificare tale percorso locale nelle impostazioni dell'analisi del codice per il progetto di codice.  La corrispondenza delle regole è garantita se il set di regole per i criteri di archiviazione è aggiornato.  
  
     Se si esegue il mapping del percorso del controllo della versione a una cartella locale nella stessa relazione della radice del progetto team come progetto di codice, il percorso del set di regole viene impostato tramite un percorso relativo.  Il percorso relativo assicura che l'impostazione del progetto di codice per l'analisi del codice possa essere spostata in altri computer.  
  
-   Personalizzare una copia del set di regole per i criteri di archiviazione per un progetto di codice.  Assicurarsi che il nuovo set di regole contenga tutte le regole dei criteri di archiviazione e qualsiasi altra regola che si desidera includere.  È necessario verificare che il set di regole includa tutte le regole nel set di regole per i criteri di archiviazione.  
  
### Per specificare un set di regole standard Microsoft  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di codice, quindi scegliere **Proprietà**.  
  
2.  Fare clic su **Analisi codice**.  
  
3.  Nell'elenco a discesa **Esegui set di regole**, fare clic sul set di regole dei criteri di archiviazione:  
  
### Per specificare un set di regole dei criteri di archiviazione personalizzato  
  
1.  Se necessario, eseguire un'operazione get nel file del set di regole che specifica i criteri di archiviazione.  
  
2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di codice, quindi scegliere **Proprietà**.  
  
3.  Fare clic su **Analisi codice**.  
  
4.  Nell'elenco **Esegui il set di regole**, fare clic su **\<Sfoglia...\>**.  
  
5.  Nella finestra di dialogo **Apri**, specificare il file del set di regole dei criteri di archiviazione.  
  
### Per creare un set di regole personalizzato per un progetto di codice  
  
1.  Seguire una delle procedure illustrate in precedenza in questo argomento per selezionare i criteri di archiviazione del progetto team nella pagina Analisi codice della finestra di dialogo delle impostazioni del progetto.  
  
2.  Fare clic su **Apri**.  
  
3.  Aggiungere o rimuovere regole tramite l'editor del set di regole.  
  
     Per ulteriori informazioni, vedere [Creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4.  Salvare il set di regole modificato in un file con estensione ruleset nel computer locale o in un percorso UNC.  
  
5.  Aprire la finestra di dialogo delle proprietà per il progetto di codice e visualizzare la pagina **Analisi codice**.  
  
6.  Nell'elenco **Esegui il set di regole**, fare clic su **\<Sfoglia...\>**.  
  
7.  Nella finestra di dialogo **Apri**, specificare il file del set di regole.