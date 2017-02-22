---
title: "Generazione di codice da un linguaggio specifico di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: 13
caps.handback.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Generazione di codice da un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] fornisce un sistema efficiente generare il codice, documenti, i file di configurazione e altri elementi dai dati rappresentati nei modelli.  Utilizzando [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], è possibile creare un set di classi che rappresentano i dati ed è possibile scrivere modelli di testo nelle classi di cui nomi e le proprietà riflettono i dati.  
  
 Ad esempio, Fabrikam dispone di un file XML dei nomi e degli indirizzi di posta elettronica del cliente.  Gli sviluppatori creano un modello in cui il cliente è una classe, con il nome della proprietà e la posta elettronica.  Scrivono diversi modelli di testo per elaborare i dati, inclusi questo frammento che scrive una tabella di tutti i clienti come parte di una pagina HTML:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Quando il database dei clienti deve essere elaborato, il file XML viene visualizzato nell' archivio modelli.  *Un processore di direttiva*, creato utilizzando [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], rende disponibile la classe customer del codice nel modello di testo. Molti modelli di testo possono essere eseguiti rispetto allo stesso archivio.  
  
 I modelli di testo sono indispensabili a [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  Vengono utilizzati per generare il codice sorgente per gli elementi del modello di dominio nonché per il package VS e i controlli utilizzati per integrare gli strumenti con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 In questa sezione vengono illustrate alcune modalità per creare, modificare ed eseguire il debug dei modelli di testo utilizzati in [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## In questa sezione  
 [Accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md)  
  
 Vengono fornite informazioni di base su riferimento al linguaggio specifico di dominio nei modelli di testo.  
  
 [Procedura dettagliata: debug di un modello di testo che accede a un modello](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Viene descritto come eseguire la risoluzione dei problemi e il debug in un modello di testo che fa riferimento a un linguaggio specifico di dominio.  
  
 [Procedura dettagliata: connessione di un host a un processore di direttiva generato](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Viene descritto come connettersi un host personalizzato a un processore di direttiva generato.  
  
 [Comando DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 Viene descritto il file di comando che consente di eseguire il file eseguibile di TextTransform nella riga di comando per i modelli di testo che linguaggi specifici di dominio di riferimento.  
  
## Riferimenti  
 [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md)  
  
 Fornisce la sintassi di direttive e blocchi di controllo del modello di testo.  
  
## Sezioni correlate  
 [Design\-Time Code Generation by using T4 Text Templates](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Viene illustrato il processo di trasformazione del modello di testo.  
  
 [Code Generation in a Build Process](../modeling/code-generation-in-a-build-process.md)  
  
 Leggere questo argomento si genera i file da un linguaggio specifico di dominio in un server di compilazione.