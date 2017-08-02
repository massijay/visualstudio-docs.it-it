---
title: "Supporto di strumenti di esplorazione di simbolo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "simboli, strumenti di esplorazione di simbolo"
  - "browser, il browser di simbolo"
  - "strumenti di esplorazione di simbolo"
  - "libraries"
  - "Interfaccia IVsLibrary2, strumenti di esplorazione di simbolo"
  - "Interfaccia IVsSimpleLibrary2, strumenti di esplorazione di simbolo"
  - "strumenti di esplorazione di simboli, Gestione librerie"
  - "simboli"
  - "librerie, strumenti di esplorazione di simbolo"
ms.assetid: 70d8c9e5-4b0b-4a69-b3b3-90f36debe880
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# Supporto di strumenti di esplorazione di simbolo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Gli strumenti di**Visualizzatore oggetti**, di **Visualizzazione classi**, di **Visualizzatore chiamate** e di **Risultati del simbolo di ricerca** forniscono le funzionalità di esplorazione del simbolo in Visual Studio.  Questi strumenti vengono visualizzate le visualizzazioni struttura ad albero gerarchico di simboli e mostrano le relazioni tra simboli nella struttura ad albero.  I simboli possono rappresentare gli spazi dei nomi, gli oggetti, le classi, i membri della classe e altri elementi del linguaggio contenuti in vari componenti.  I componenti includono i progetti di Visual Studio, i componenti esterni di [!INCLUDE[dnprdnshort](../../code-quality/includes/dnprdnshort_md.md)] e le librerie dei tipi \(TLB\).  Per ulteriori informazioni, vedere [Visualizzazione della struttura del codice](../../ide/viewing-the-structure-of-code.md).  
  
## Librerie di Simbolo\-Esplorazione  
 Come responsabile implementatori di linguaggio, è possibile estendere le funzionalità di simbolo\-esplorazione di Visual Studio creando le raccolte che tiene traccia dei simboli nei componenti e forniscono elenchi dei simboli gestione dell'oggetto di Visual Studio tramite un set di interfacce.  Una raccolta è descritta dall'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2> .  L'amministratore dell'oggetto di Visual Studio risponde alle richieste di nuovi dati dagli strumenti di simbolo\-esplorazione ottenere i dati dalle librerie e organizzandolo.  Successivamente inserisce o aggiorna gli strumenti con i dati richiesti.  Per ottenere un riferimento all'amministratore dell'oggetto di Visual Studio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>, passa il servizio ID di <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> al metodo di `GetService` .  
  
 Ogni raccolta necessario registrare con l'amministratore dell'oggetto di Visual Studio, che raccoglie informazioni su tutte le raccolte.  Per registrare una libreria, chiamare il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  Secondo lo strumento inizia la richiesta, i trova gestione dell'oggetto di Visual Studio la raccolta appropriato e richiede i dati.  I round trip a di dati tra le raccolte e gestione dell'oggetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gli elenchi dei simboli descritti da <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> collegamento.  
  
 L'amministratore dell'oggetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]è responsabile periodicamente di aggiornamento degli strumenti di simbolo\-esplorazione per riflettere i dati più recenti contenuti nelle librerie.  
  
 Nel diagramma riportato di seguito contiene un esempio degli elementi principali delle richieste\/processo di scambio di dati tra una raccolta e gestione dell'oggetto di Visual Studio.  Le interfacce nel diagramma fa parte di un'applicazione di codice gestito.  
  
 ![Flusso dei dati tra una libreria e il gestore oggetti](~/extensibility/internals/media/callbrowserdiagram.gif "CallBrowserDiagram")  
  
 Per fornire gli elenchi dei simboli in Visual Studio l'oggetto amministratore, è necessario innanzitutto registrare la raccolta con l'amministratore dell'oggetto di Visual Studio chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .  Dopo la raccolta è registrata, l'amministratore dell'oggetto di Visual Studio richiede alcune informazioni sulle funzionalità della raccolta.  Ad esempio, richiede i flag della libreria e le categorie supportate chiamando i metodi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetSupportedCategoryFields2%2A> e di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetLibFlags2%2A> .  A un certo punto, quando uno degli strumenti richiede i dati da questa raccolta, l'amministratore dell'oggetto richiede un elenco di primo livello dei simboli chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleLibrary2.GetList2%2A> .  Nella risposta, la raccolta fabbrica un elenco di simboli e lo espone gestione dell'oggetto di Visual Studio tramite l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2> .  L'amministratore dell'oggetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]determina il numero di elementi presenti nell'elenco chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetItemCount%2A> .  Tutte le seguenti condizioni sono correlati a un elemento specificato nell'elenco e forniscono il numero di indice dell'elemento in ogni richiesta.  L'amministratore dell'oggetto di Visual Studio continua a raccogliere informazioni sul tipo, sull'accessibilità e altre proprietà dell'elemento chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetCategoryField2%2A> .  
  
 Determina il nome dell'elemento chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetTextWithOwnership%2A> e richiede informazioni sull'icona chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetDisplayData%2A> .  L'icona viene visualizzata a sinistra del nome dell'elemento e raffigura il tipo di elemento, l'accessibilità e altre proprietà.  
  
 L'amministratore dell'oggetto di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiama il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetExpandable3%2A> per determinare se un elemento dell'elenco specificato è espandibile e ha voci figlio.  Se l'interfaccia utente invia una richiesta di espandere un elemento, l'amministratore dell'oggetto richiede un elenco figlio di simboli chiamando il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSimpleObjectList2.GetList2%2A> .  Il processo continua con diverse parti della struttura ad albero che si trova su richiesta compilato.  
  
> [!NOTE]
>  Per implementare un provider del simbolo di codice nativo, utilizzare le interfacce di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectList2> e di <xref:Microsoft.VisualStudio.Shell.Interop.IVsLibrary2> .  
  
## Vedere anche  
 [Procedura: registrare una libreria con il gestore oggetti](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)   
 [Procedura: esporre elenchi dei simboli forniti dalla libreria di gestione degli oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)   
 [Procedura: identificare i simboli in una libreria](../../extensibility/internals/how-to-identify-symbols-in-a-library.md)