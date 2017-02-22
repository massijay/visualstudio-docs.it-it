---
title: "Scrittura di codice per personalizzare un linguaggio specifico di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, programmazione"
ms.assetid: a4a17f5b-9c97-4575-b2d1-3182c1896b72
caps.latest.revision: 29
caps.handback.revision: 29
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Scrittura di codice per personalizzare un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa sezione viene illustrato come utilizzare codice personalizzato per accedere, modificare, o creare un modello in un linguaggio specifico di dominio.  
  
 Esistono diversi contesti in cui è possibile scrivere codice che utilizza un modello DSL:  
  
-   **Controlli personalizzati.** È possibile creare un comando che gli utenti possono richiamare fare clic con il pulsante destro del mouse sul diagramma e che può modificare il modello.  Per ulteriori informazioni, vedere [Procedura: aggiungere un comando al menu di scelta rapida](../modeling/how-to-add-a-command-to-the-shortcut-menu.md).  
  
-   **convalida.** È possibile scrivere codice che verifica che il modello sia in uno stato corretto.  Per ulteriori informazioni, vedere [Convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).  
  
-   **Eseguire l'override del comportamento predefinito.** È possibile modificare molti aspetti del codice generato da DslDefinition.dsl.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).  
  
-   **Trasformazione di testo.** È possibile scrivere modelli di testo che contengono il codice che accede a un modello e genera un file di testo, ad esempio per generare codice programma.  Per ulteriori informazioni, vedere [Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
-   **altre estensioni di Visual Studio.** È possibile scrivere estensioni separate VSIX che leggono e modificare modelli.  Per ulteriori informazioni, vedere [Procedura: aprire un modello da file nel codice del programma](../modeling/how-to-open-a-model-from-file-in-program-code.md).  
  
 Le istanze delle classi definite in DslDefinition.dsl vengono inserite in una struttura di dati chiamata *Archiviare in memoria* \(IMS\) o *archivio*.  Le classi definite in un modello DSL hanno sempre un archivio come argomento al costruttore.  Ad esempio, se il modello DSL definisce Example chiamato classe:  
  
 `Example element = new Example (theStore);`  
  
 mantenimento degli oggetti nell'archivio \(anziché come oggetti comuni\) fornisce molti vantaggi.  
  
-   **transazioni**.  È possibile raggruppare una serie di correlato modifiche in un'unica transazione:  
  
     `using (Transaction t = store.TransactionManager.BeginTransaction("updates"))`  
  
     `{`  
  
     `// make several changes to Store elements here`  
  
     `t.Commit();`  
  
     `}`  
  
     Se si verifica un'eccezione durante le modifiche, in modo che Commit\(\) finale non viene eseguita, quest'ultimo verrà reimpostato allo stato precedente.  Ciò consente di garantire che gli errori non lasciare il modello in uno stato incoerente.  Per ulteriori informazioni, vedere [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **relazioni binarie**.  Se si definisce una relazione tra due classi, le istanze in entrambe le estremità dispongono di una proprietà che consente di passare all'altra estremità.  Le due estremità vengono sincronizzate sempre.  Ad esempio, se si definisce una relazione di paternità con i ruoli denominati Parents e figlio, è possibile scrivere:  
  
     `John.Children.Add(Mary)`  
  
     Entrambe le espressioni seguenti sono vere:  
  
     `John.Children.Contains(Mary)`  
  
     `Mary.Parents.Contains(John)`  
  
     È inoltre possibile ottenere lo stesso risultato scrivendo:  
  
     `Mary.Parents.Add(John)`  
  
     Per ulteriori informazioni, vedere [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
-   **Regole ed eventi**.  È possibile definire regole che vengono generati quando le modifiche specificate vengono apportate.  Le regole vengono utilizzate, ad esempio, mantenere le forme del diagramma aggiornato con gli elementi del modello che presentano.  Per ulteriori informazioni, vedere [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).  
  
-   **serializzazione**.  L'archivio fornisce una modalità standard per serializzare gli oggetti in essa contenuti in un file.  È possibile personalizzare le regole per la serializzazione e la deserializzazione.  Per ulteriori informazioni, vedere [Personalizzazione dell'archiviazione dei file e della serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md).  
  
## Vedere anche  
 [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)