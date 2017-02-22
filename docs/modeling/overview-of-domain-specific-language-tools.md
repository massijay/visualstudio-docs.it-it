---
title: "Informazioni generali sugli strumenti di linguaggio specifico di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio"
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 54
caps.handback.revision: 54
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Informazioni generali sugli strumenti di linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Strumenti di linguaggio specifico di dominio \(strumenti DSL\), che sono ospitati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], e consentono di progettare un linguaggio specifico di dominio quindi generare tutto ciò che gli utenti devono disporre creare modelli in base al linguaggio.  
  
 I seguenti strumenti sono inclusi in strumenti DSL:  
  
-   Una procedura guidata di progetto che utilizza i modelli diversi della soluzione per consentire l'avvio compilare il linguaggio specifico di dominio.  
  
-   una finestra di progettazione grafica per creare e modificare la definizione di linguaggio specifico di dominio.  
  
-   Un motore di convalida per assicurare che la definizione di linguaggio specifico di dominio sia corretto e visualizzare gli errori e gli avvisi se sono presenti problemi.  
  
-   Un generatore di codice che accetta una definizione di linguaggio specifico di dominio come input e genera il codice sorgente come output.  
  
## Il modello DSL gli strumenti della soluzione  
 La procedura guidata specifico del dominio della finestra di progettazione fornisce i seguenti modelli della soluzione:  
  
-   flusso di attività  
  
-   diagrammi classi  
  
-   linguaggio minimo  
  
-   modelli componenti  
  
-   WPF minimo  
  
-   Windows.Forms minimo  
  
-   Raccolta DSL  
  
 Per ulteriori informazioni, vedere [Scelta di un modello di soluzione per un linguaggio specifico di dominio](../modeling/choosing-a-domain-specific-language-solution-template.md).  
  
 La procedura guidata crea un oggetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] soluzione che contiene i seguenti progetti:  
  
-   Dsl  
  
     Il progetto di Dsl definisce il linguaggio specifico di dominio e gli strumenti di elaborazione e di modifica.  
  
-   **DslPackage**  
  
     Il progetto DslPackage determina quali strumenti del linguaggio si integrano con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Il modello DSL gli strumenti l'interfaccia grafica  
 È possibile utilizzare l'interfaccia grafica degli strumenti DSL per aggiungere gli elementi e le relazioni al linguaggio specifico di dominio.  Dopo aver aggiunto gli elementi, è possibile definire il relativo aspetto eseguendone il mapping a forme, personalizzazione dei colori e aggiungendo elementi Decorator.  È anche possibile aggiungere elementi alla casella degli strumenti.  
  
## Convalida in strumenti DSL  
 Il Dsl fornisce un livello di convalida per assicurarsi che il modello di dominio soddisfi i requisiti per la generazione di codice.  In genere, quando si crea proprietari del linguaggio specifico di dominio, è aggiunto diventi proprietaria della convalida per esprimere le regole di logica di business.  Per ulteriori informazioni sulla convalida personalizzata, vedere [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
 È consigliabile convalidare spesso il linguaggio specifico di dominio quando si progettandolo.  Se il linguaggio specifico di dominio presenta errori di convalida, non è possibile generare codice sorgente.  Il processo di generazione del codice sorgente dai modelli viene eseguito facendo clic su **Trasformazione di tutti i modelli** nella barra degli strumenti di Esplora soluzioni.  Ogni volta che si modifica la definizione di linguaggio, assicurarsi inoltre a **Trasformazione di tutti i modelli**.  Per ulteriori informazioni, vedere [Procedura: creare una soluzione per un linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## Personalizzazione degli strumenti DSL  
 È possibile fornire codice aggiuntivo per perfezionare il comportamento del modello e per definire vincoli sul linguaggio.  Se necessario, è possibile apportare modifiche significative modificando i modelli di testo.  
  
## Distribuire la soluzione DSL  
 Gli strumenti DSL genera un pacchetto che è ospitato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Il pacchetto verrà visualizzata una casella degli strumenti, un esplora DSL e altri elementi di interfaccia utente che consentono agli utenti di creare modelli tramite il linguaggio specifico di dominio.  
  
 Quando si compila e si esegue il modello DSL gli strumenti della soluzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], una seconda istanza di  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene illustrato come gli aspetti del linguaggio specifico di dominio all'utente del linguaggio. Una volta verificato che tutto il lavoro completato correttamente, è possibile distribuire  `.vsix` archiviare disponibili nella cartella di compilazione del progetto DslPackage.  Questo file può essere utilizzato per installare il modello DSL ad esempio [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione in altri computer.  Per ulteriori informazioni, vedere [Distribuzione di soluzioni per un linguaggio specifico di dominio](../modeling/deploying-domain-specific-language-solutions.md).  
  
## Vedere anche  
 [L'istanza sperimentale](../extensibility/the-experimental-instance.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)