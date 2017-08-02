---
title: Panoramica sulle opzioni di configurazione | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project configurations
- configuration options, about configuration options
ms.assetid: f4ad4dd3-b39e-42df-ad89-d403cdf24a2b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 2c188af385d75fed49f6e9aca6703365c3b63ca5
ms.lasthandoff: 02/22/2017

---
# <a name="configuration-options-overview"></a>Cenni preliminari sulle opzioni di configurazione
Proietta in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] può supportare più configurazioni che possono essere compilate in fase di debug, esecuzione e/o distribuiti. Una configurazione è un tipo di compilazione descritto, con un set denominato di proprietà, in genere le opzioni del compilatore e percorsi dei file. Per impostazione predefinita, le nuove soluzioni contengono le due configurazioni Debug e rilascio. Queste configurazioni possono essere applicate utilizzando le impostazioni predefinite o modificare per soddisfare i requisiti specifici di soluzione e/o progetto. Alcuni pacchetti possono essere compilati in due modi: come un editor di ActiveX o un componente sul posto. Non è necessario supportare più configurazioni, tuttavia progetti. Se è disponibile solo una configurazione, tale configurazione viene eseguito il mapping in tutte le configurazioni di soluzione.  
  
 Le configurazioni sono costituite in genere da due parti, ovvero il nome di configurazione (ad esempio Debug o Release) e le impostazioni di piattaforma. Nome della piattaforma della configurazione identifica l'ambiente che impostare gli obiettivi di configurazione, ad esempio un'API o la piattaforma del sistema operativo. Gli utenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non può creare una piattaforma; devono scegliere le selezioni un progetto VSPackage consente. Quando un utente installa un VSPackage, la piattaforma di distribuzione creata durante lo sviluppo del pacchetto è possibile che un nome di piattaforma desiderato in base a qualsiasi criteri impostati dall'autore del pacchetto. L'utente può quindi selezionare dall'elenco di piattaforme rese disponibili tramite VSPackage quando le pagine delle proprietà vengono create istanze.  
  
 I nomi di piattaforma sono facoltativi, poiché non tutti i progetti supportano il concetto di piattaforme. Quando una configurazione non dispone di un nome di piattaforma, la stringa "n/d" viene visualizzato nell'interfaccia utente.  
  
 Ogni soluzione ha un proprio set di configurazioni, solo uno dei quali può essere attivo alla volta. Una configurazione di soluzione è un set di configurazione non più di uno ogni progetto. Il criterio "non maggiore di" fa è dovuto all'opzione per escludere un progetto da una configurazione di soluzione. Gli utenti possono creare le proprie configurazioni di soluzione personalizzata.  
  
 Nella tabella seguente viene illustrata l'impostazione di configurazioni tipiche per un progetto. Le righe sono contrassegnate con nomi di configurazione e le colonne con nomi di piattaforma.  
  
|Nome configurazione|Piattaforma, Win32|Piattaforma: Win64|  
|------------------------|----------------------|----------------------|  
|Debug|\<Eseguire il debug Win32 impostazioni >|\<Eseguire il debug Win64 impostazioni >|  
|Versione|\<Versione Win32 impostazioni >|\<Versione Win64 impostazioni >|  
|MyConfig|N/D|\<Impostazioni MyConfig Win64 >|  
  
> [!NOTE]
>  È possibile creare una configurazione di soluzione "MyConfig" che esclude una piattaforma "Win32", a meno che il progetto di destinazione non supporta Win32.  
  
 Modifica della configurazione attiva per una soluzione consente di selezionare il set di configurazioni di progetto che vengono compilate, esecuzione, eseguire il debug o distribuito all'interno della soluzione. Ad esempio, se si modifica la configurazione di soluzione attiva dalla versione di Debug, tutti i progetti contenuti nella soluzione vengono compilati automaticamente con la configurazione del progetto indicato nella configurazione di Debug della soluzione. Le configurazioni del progetto sono in genere denominata Debug, a meno che l'utente ha apportato modifiche manuali dell'ambiente di Configuration Manager.  
  
 Le proprietà di configurazione di soluzione archiviate per ogni progetto includono il nome del progetto, nome configurazione progetto, i flag per indicare se per compilare o distribuire e il nome della piattaforma. Per ulteriori informazioni, vedere [configurazione di soluzione](../../extensibility/internals/solution-configuration.md).  
  
 L'utente può visualizzare e impostare parametri di configurazione di soluzione, selezionare la soluzione nella gerarchia (Esplora soluzioni) e aprire le pagine delle proprietà. Analogamente, è possibile visualizzare e impostare i parametri di configurazione di progetto selezionando un progetto in Esplora soluzioni e aprire le pagine delle proprietà per il progetto.  
  
 L'utente è anche possibile compilare un progetto con impostazioni di configurazione Release e tutte le altre impostazioni di configurazione Debug se necessario. Per ulteriori informazioni, vedere [configurazione del progetto per la creazione di](../../extensibility/internals/project-configuration-for-building.md).  
  
 Nel diagramma seguente viene illustrato come vengono implementate le interfacce che supportano le configurazioni di soluzione e progetto:  
  
 ![Rappresentazione grafica delle interfacce di configurazione](~/docs/extensibility/internals/media/vsconfiginterfaces.gif "vsConfigInterfaces")  
Interfacce di configurazione  
  
 Alcune note relative al diagramma precedente:  
  
-   `IDispatch`è contrassegnato come facoltativo nell'oggetto di configurazione. In particolare, è facoltativo per le interfacce di configurazione per l'oggetto visualizzazione.  
  
-   `IVsDebuggableProjectCfg`è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per il supporto del debug.  
  
-   `IVsProjectCfg2`è contrassegnato come facoltativo nell'oggetto di configurazione, ma è necessario per l'output del supporto di raggruppamento.  
  
-   Il `Config Provider` oggetto è contrassegnato come un oggetto facoltativo, ma l'opzione è la posizione in cui implementarla. È possibile implementare l'oggetto sull'oggetto progetto o in un oggetto separato.  
  
-   `IVsCfgProvider2`è necessario per il supporto di piattaforma e la modifica della configurazione. `IVsCfgProvider`è sufficiente se non si implementa questa funzionalità.  
  
-   Alcuni di questi oggetti illustrati nel diagramma come oggetti distinti possono essere combinati nella stessa classe se fattibile in base alle esigenze specifiche di progettazione. In altri argomenti di questa sezione, tuttavia, gli oggetti e interfacce associate a tali oggetti verranno analizzate in base allo scenario presentato nel diagramma.  
  
-   Alcuni oggetti vengono implementate separatamente. Ad esempio, progetto e alla creazione di soluzioni si verificano su un thread separato e l'oggetto per gestire la vita compilazione separatamente dall'oggetto che descrive la configurazione per la compilazione.  
  
 Per ulteriori informazioni sulle interfacce dell'oggetto di configurazione e interfacce dell'oggetto Provider di configurazione nel diagramma precedente, vedere [oggetto di configurazione progetto](../../extensibility/internals/project-configuration-object.md). Inoltre, [configurazione del progetto per la creazione di](../../extensibility/internals/project-configuration-for-building.md) fornisce ulteriori informazioni sulle interfacce di configurazione generatore e oggetto di dipendenza di compilazione, e [configurazione del progetto per la Gestione distribuzione](../../extensibility/internals/project-configuration-for-managing-deployment.md) ulteriormente descrive le interfacce associate agli oggetti di dipendenza distributore e distribuzione di configurazione. Infine, [configurazione del progetto per l'Output](../../extensibility/internals/project-configuration-for-output.md) descrive le interfacce di gruppo di Output e l'oggetto di Output e l'utilizzo delle pagine delle proprietà per visualizzare e impostare le proprietà dipendenti dalla configurazione.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2></xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Configurazione di soluzione](../../extensibility/internals/solution-configuration.md)
