---
title: La generazione di codice da un linguaggio specifico di dominio | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e3706cc9-2afd-456a-a879-68425a248ebc
caps.latest.revision: "13"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 98811cc3e7830dfcbf548bc34c5b3ee268e6f858
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="generating-code-from-a-domain-specific-language"></a>Generazione di codice da un linguaggio specifico di dominio
Microsoft [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] fornisce un potente strumento per generare codice, documenti, file di configurazione e altri elementi da dati rappresentati nei modelli. Utilizzando [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], è possibile creare un set di classi che rappresentano i dati, è possibile scrivere modelli di testo nelle classi i cui nomi e le proprietà riflettono i dati.  
  
 Ad esempio, Fabrikam disponga di un file XML di nomi di clienti e indirizzi di posta elettronica. Gli sviluppatori di creare un modello in cui i clienti sono una classe, con il nome di proprietà e il messaggio di posta elettronica. La scrittura di diversi modelli di testo per elaborare i dati, inclusi il frammento che produce una tabella di tutti i clienti come parte di una pagina HTML:  
  
```  
<table>  
<# foreach (Customer c in ContactList) {  #>  
  <tr><td> <#= c.FullName #> </td>   
      <td> <#= c.EmailAddress #> </td> </tr>  
<# } #>  </table>  
```  
  
 Quando viene elaborato il database dei clienti, il file XML viene letto nell'archivio modelli. Oggetto *processore di direttiva*, creato tramite [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], rende disponibili per il codice della classe Customer nel modello di testo. Molti modelli di testo possono essere eseguiti con lo stesso archivio.  
  
 Modelli di testo sono essenziali per [!INCLUDE[dsl](../modeling/includes/dsl_md.md)]. Vengono utilizzati per generare il codice sorgente per gli elementi del modello di dominio nonché per il pacchetto VSPackage e i controlli che consentono di integrare gli strumenti con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
 In questa sezione vengono illustrati alcuni modi per creare, modificare ed eseguire il debug di modelli di testo utilizzati in [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md)  
  
 Fornisce informazioni di base che fa riferimento al linguaggio specifico di dominio nei modelli di testo.  
  
 [Procedura dettagliata: debug di un modello di testo che accede a un modello](../modeling/walkthrough-debugging-a-text-template-that-accesses-a-model.md)  
  
 Viene descritto come eseguire la risoluzione dei problemi e debug in un modello di testo che fa riferimento a un linguaggio specifico di dominio.  
  
 [Procedura dettagliata: connessione di un host a un processore di direttiva generato](../modeling/walkthrough-connecting-a-host-to-a-generated-directive-processor.md)  
  
 Viene descritto come connettersi a un host personalizzato per un processore di direttiva generato.  
  
 [Comando DslTextTransform](../modeling/the-dsltexttransform-command.md)  
  
 Descrive il file di comando che esegue il file eseguibile TextTransform nella riga di comando per i modelli di testo che fanno riferimento a linguaggi specifici di dominio.  
  
## <a name="reference"></a>Riferimento  
 [Scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md)  
  
 Fornisce la sintassi delle direttive di modello di testo e blocchi di controllo.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)  
  
 Viene illustrato il processo di trasformazione di modello di testo.  
  
 [Generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md)  
  
 Se si siano generando file da un linguaggio DSL in un server di compilazione, leggere questo argomento.