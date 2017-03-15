---
title: Come modelli di testo | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1ac2509-0479-47eb-809c-1f171245d0b6
caps.latest.revision: 11
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: b874c9c259664f7f07e3266781909f74ece6e60a
ms.lasthandoff: 02/22/2017

---
# <a name="how-to--with-text-templates"></a>Procedure relative ai modelli di testo
Modelli di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] forniscono un modo utile per la generazione di testo di qualsiasi tipo. È possibile utilizzare modelli di testo per generare testo in fase di esecuzione come parte dell'applicazione e in fase di progettazione per generare alcuni del codice del progetto. Questo argomento vengono riepilogati più di frequente frequenti "Ricerca per categorie..." domande.  
  
 In questo argomento, risposte multiple precedute da elenchi puntati sono suggerimenti alternativi.  
  
 Per un'introduzione generale ai modelli di testo, leggere [la generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="how-to-"></a>Come si fa...  
  
### <a name="generate-part-of-my-application-code"></a>Generare parte del codice dell'applicazione  
 Dispone di una configurazione o *modello* in un file o un database. Uno o più parti del codice dipendono da tale modello.  
  
-   Generare alcuni dei file di codice dai modelli di testo. Per ulteriori informazioni, vedere [la generazione del codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md) e [che cos'è il modo migliore per iniziare a scrivere un modello?](#starting).  
  
### <a name="generate-files-at-run-time-passing-data-into-the-template"></a>Generare file in fase di esecuzione, il passaggio di dati nel modello  
 In fase di esecuzione, l'applicazione genera file di testo, ad esempio report, che contengono una combinazione di testo standard e i dati. Si desidera evitare la scrittura di centinaia di `write` istruzioni.  
  
-   Aggiungere un modello di testo della fase di esecuzione per il progetto. Questo modello consente di creare una classe nel codice, che è possibile creare un'istanza e utilizzare per generare testo. È possibile passare dati nei parametri del costruttore. Per ulteriori informazioni, vedere [la generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
-   Se si desidera generare dai modelli che sono disponibili solo in fase di esecuzione, è possibile utilizzare modelli di testo standard. Se si sta scrivendo un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] estensione, è possibile richiamare il servizio del modello di testo. Per ulteriori informazioni, vedere [richiamo di trasformazione del testo in un'estensione di Visual Studio](../modeling/invoking-text-transformation-in-a-vs-extension.md). In altri contesti, è possibile utilizzare il motore del modello di testo. Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>.</xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>  
  
     Utilizzare il \<#@parameter#> (direttiva) per passare parametri a questi modelli. Per ulteriori informazioni, vedere [direttiva Parameter T4](../modeling/t4-parameter-directive.md).  
  
### <a name="read-another-project-file-from-a-template"></a>Leggere un altro file di progetto da un modello  
 Per leggere un file dalla stessa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] come modello di progetto:  
  
-   Inserire `hostSpecific="true"` nella direttiva `<#@template#>`.  
  
     Nel codice, utilizzare `this.Host.ResolvePath(filename)` per ottenere il percorso completo del file.  
  
### <a name="invoke-methods-from-a-template"></a>Richiamare i metodi da un modello  
 Se i metodi già esistono, ad esempio, nello standard [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] classi:  
  
-   Utilizzare il \<#@assembly#> direttiva per caricare l'assembly e utilizzare \<#@import#> per impostare il contesto dello spazio dei nomi. Per ulteriori informazioni, vedere [direttiva Import T4](../modeling/t4-import-directive.md).  
  
     Se si utilizzano lo stesso set di assembly spesso più semplice e direttive di importazione, è consigliabile scrivere un processore di direttiva. In ogni modello, è possibile richiamare il processore di direttiva, che è possibile caricare gli assembly e i file del modello e impostare il contesto dello spazio dei nomi. Per ulteriori informazioni, vedere [creazione personalizzata T4 testo modello direttiva processori](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
 Se si siano scrivendo i metodi manualmente:  
  
-   Se si scrive un modello di testo della fase di esecuzione, scrivere una definizione di classe parziale che ha lo stesso nome del modello di testo della fase di esecuzione. Aggiungere i metodi aggiuntivi in questa classe.  
  
-   Scrivere un blocco di controllo di funzionalità di classe `<#+ ... #>` in cui è possibile dichiarare metodi, proprietà e classi private. Quando viene compilato il modello di testo, viene trasformato in una classe. I blocchi di controllo standard `<#...#>` e testo vengono trasformati in un singolo metodo e blocchi della funzionalità di classe vengono inseriti come membri separati. Per ulteriori informazioni, vedere [blocchi di controllo del modello di testo](../modeling/text-template-control-blocks.md).  
  
     Metodi definiti come le funzionalità di classe possono anche includere blocchi di testo incorporato.  
  
     È consigliabile inserire le funzionalità di classe in un file separato che è possibile `<#@include#>` in uno o più file di modello.  
  
-   Scrivere i metodi in un assembly separato (libreria di classi) e chiamarli dal modello. Utilizzare il `<#@assembly#>` direttiva per caricare l'assembly e `<#@import#>` per impostare il contesto dello spazio dei nomi. Si noti che per ricompilare l'assembly durante il debug, potrebbe essere necessario arrestare e riavviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Per ulteriori informazioni, vedere [direttive di modello di testo T4](../modeling/t4-text-template-directives.md).  
  
### <a name="generate-many-files-from-one-model-schema"></a>Generare molti file dello schema di un modello  
 Se si generano spesso file dai modelli che hanno lo stesso schema XML o di database:  
  
-   È consigliabile scrivere un processore di direttiva. Ciò consente di sostituire più istruzioni di assembly e istruzioni import in ogni modello con un'unica direttiva personalizzata. Il processore di direttiva può inoltre caricare e analizzare il file del modello. Per ulteriori informazioni, vedere [creazione personalizzata T4 testo modello direttiva processori](../modeling/creating-custom-t4-text-template-directive-processors.md).  
  
### <a name="generate-files-from-a-complex-model"></a>Generare file da un modello complesso  
  
-   È consigliabile creare un linguaggio specifico di dominio (DSL) per rappresentare il modello. Questo rende molto più semplice scrivere i modelli, poiché si utilizzano tipi e le proprietà che riflettono i nomi degli elementi nel modello. Non è necessario analizzare il file o esplorare i nodi XML. Ad esempio:  
  
     `foreach (Book book in this.Library) { ... }`  
  
     Per ulteriori informazioni, vedere [Introduzione al linguaggio specifico di dominio](../modeling/getting-started-with-domain-specific-languages.md) e [la generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md).  
  
### <a name="get-data-from-includevsprvscode-qualityincludesvsprvsmdmd"></a>Ottenere i dati[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]  
 Per usare i servizi disponibili [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], dal set di `hostSpecific` attributo e carico il `EnvDTE` assembly. Ad esempio:  
  
```c#  
<#@ template hostspecific="true" language="C#" #>  
<#@ output extension=".txt" #>  
<#@ assembly name="EnvDTE" #>  
<#  
  IServiceProvider serviceProvider = (IServiceProvider)this.Host;  
  EnvDTE.DTE dte = (EnvDTE.DTE) serviceProvider.GetService(typeof(EnvDTE.DTE));  
#>  
  
Number of projects in this VS solution:  <#= dte.Solution.Projects.Count #>  
  
```  
  
### <a name="execute-text-templates-in-the-build-process"></a>Eseguire i modelli di testo nel processo di compilazione  
  
-   Per ulteriori informazioni, vedere [generazione di codice in un processo di compilazione](../modeling/code-generation-in-a-build-process.md).  
  
## <a name="more-general-questions"></a>Domande generali  
  
###  <a name="a-namestartinga-what-is-the-best-way-to-start-writing-a-text-template"></a><a name="starting"></a>Che cos'è il modo migliore per iniziare a scrivere un modello di testo?  
  
1.  Scrivere un esempio specifico del file generato.  
  
2.  Trasformarlo in un modello di testo inserendo il `<#@template #>` direttiva, le direttive e codice che sono necessari per caricare il file di input o il modello.  
  
3.  Sostituire progressivamente le parti del file con l'espressione e blocchi di codice.  
  
### <a name="what-is-a-model"></a>Che cos'è un "modello"?  
  
-   L'input letto dal modello. È possibile in un file o in un database. È possibile, XML o un disegno di Visio, o un linguaggio specifico di dominio (DSL) o un modello UML o può trattarsi di testo normale. Potrebbe essere distribuito in più file. In genere più di un modello legge un modello.  
  
     L'implicazione del termine "modello" è che rappresenta alcuni aspetti dell'azienda più direttamente il codice di programma generato o altri file. Ad esempio, potrebbe rappresentare il piano di rete di comunicazione che dichiara il software generato.  
  
### <a name="what-is-the-benefit-of-using-text-templates"></a>Qual è il vantaggio dell'utilizzo di modelli di testo?  
 In genere, si genera codice più o altri file da un modello. Il modello rappresenta i requisiti in modo più diretto rispetto al codice generato. Omette dettaglio di implementazione e viene scritto in termini di requisiti, anziché il codice. Quando i requisiti cambiano, come avviene in genere, è possibile aggiornare il modello più semplice e più affidabile rispetto alle diverse parti del codice programma.  
  
 Generazione di codice è uno strumento estremamente utile dal punto di vista della metodologia di sviluppo agile.  
  
### <a name="what-best-practices-are-there-for-text-templates"></a>Quali "procedure consigliate" sono disponibili per i modelli di testo?  
  
-   Per ulteriori informazioni, vedere [linee guida per i modelli di testo T4 scrittura](../modeling/guidelines-for-writing-t4-text-templates.md).  
  
### <a name="what-is-t4"></a>Che cos'è "T4"?  
  
-   Un altro nome per il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] funzionalità di modello di testo descritte di seguito. La versione precedente, non è stata pubblicata, è un'abbreviazione per "Trasformazione del modello di testo".

