---
title: Soluzione (. File sln) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 13
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
ms.openlocfilehash: d9b2d052f86cf76dcd9e2f97f2ee03eaf07dcf5b
ms.lasthandoff: 02/22/2017

---
# <a name="solution-sln-file"></a>Soluzione (. File sln)
Una soluzione è una struttura per organizzare i progetti in Visual Studio. La soluzione gestisce le informazioni sullo stato per i progetti in sln (basata su testo, condivisa) e i file con estensione suo (opzioni di soluzione binari specifici dell'utente). Per ulteriori informazioni sui file. suo, vedere [opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
 Se il pacchetto Visual Studio viene caricato in seguito a cui viene fatto riferimento nel file con estensione sln, l'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>per leggere il file con estensione sln.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>  
  
 Il file con estensione sln contiene informazioni basate su testo che nell'ambiente viene utilizzato per individuare e caricare i parametri nome-valore per i dati persistenti e il progetto VS fa riferimento. Quando un utente apre una soluzione, l'ambiente consente di scorrere il `preSolution`, `Project`, e `postSolution` informazioni nel file con estensione sln per caricare la soluzione, progetti all'interno della soluzione e qualsiasi informazione persistente associata alla soluzione.  
  
 File di ogni progetto contiene informazioni aggiuntive di lettura da parte dell'ambiente per popolare la gerarchia con gli elementi del progetto. Persistenza dei dati la gerarchia è controllata dal progetto. i dati non è in genere archiviati in file con estensione sln, sebbene sia possibile scrivere le informazioni sul progetto nel file con estensione sln intenzionalmente se si sceglie di eseguire questa operazione. Per ulteriori informazioni relative alla persistenza, vedere [persistenza del progetto](../../extensibility/internals/project-persistence.md) e [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="solution-file-contents"></a>Contenuto del File di soluzione  
 Il file con estensione sln è costituito da diverse sezioni come illustrato nel codice seguente.  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 Per caricare una soluzione, l'ambiente esegue la seguente sequenza di attività.  
  
1.  L'ambiente legge la sezione del file con estensione sln globale ed elabora tutte le sezioni contrassegnate `preSolution`. In questo caso, esiste un'istruzione di questo tipo:  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     Quando l'ambiente legge il `GlobalSection('name')` tag, viene eseguito il mapping il nome a un pacchetto utilizzando il Registro di sistema. Il nome della chiave deve essere disponibile nel Registro di sistema [HKLM\\<Application id="" registry=""></Application>\>\SolutionPersistence\AggregateGUIDs]. Valore predefinito delle chiavi è il GUID di pacchetto (REG_SZ) del VSPackage che ha scritto le voci.  
  
2.  L'ambiente carica VSPackage, chiamate `QueryInterface` su VSPackage per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>interfaccia e chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>metodo con i dati nella sezione VSPackage possibile archiviare i dati.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> L'ambiente di questo processo viene ripetuto per ogni `preSolution` sezione.  
  
3.  L'ambiente scorre tutti i blocchi di persistenza del progetto. In questo caso, è un progetto.  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     Questa istruzione contiene il GUID univoco del progetto e il GUID del tipo di progetto. Queste informazioni vengono utilizzate per l'ambiente per individuare il file di progetto o file appartenenti alla soluzione e VSPackage necessari per ogni progetto. Il progetto al GUID <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>per caricare il VSPackage specifici correlati al progetto, quindi il progetto viene caricato dal VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> In questo caso, il package VS che viene caricato per questo progetto è Visual Basic.  
  
     Ogni progetto può rendere persistente un ID di istanza univoco del progetto in modo che siano accessibili in base alle esigenze da altri progetti nella soluzione. In teoria, i progetti e soluzioni nel controllo del codice sorgente, il percorso del progetto deve essere relativo al percorso per la soluzione. Quando viene caricata la soluzione, i file di progetto non possono essere sul computer dell'utente. Se il file di progetto memorizzato sul server relativo al file di soluzione, è relativamente semplice per il file di progetto per trovare e copiato nel computer dell'utente. Viene quindi copiata e carica il resto dei file necessari per il progetto.  
  
4.  In base alle informazioni contenute nella sezione del file con estensione sln di progetto, l'ambiente carica ogni file di progetto. Il progetto è quindi responsabile della compilazione della gerarchia del progetto e il caricamento di tutti i progetti nidificati.  
  
5.  Dopo l'elaborano di tutte le sezioni del file con estensione sln, la soluzione viene visualizzata in Esplora soluzioni ed è pronta per la modifica dall'utente.  
  
 Se qualsiasi package VS che implementa un progetto nella soluzione non viene caricato, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>viene chiamato il metodo e ogni altro progetto nella soluzione abbia la possibilità di ignorare le modifiche possono essere apportate durante il caricamento.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> Se si verificano errori di analisi, viene mantenute quante più informazioni possibili con i file della soluzione e l'ambiente consente di visualizzare una finestra di dialogo che avvisa l'utente che la soluzione è danneggiata.  
  
 Quando viene salvata o chiuso, la soluzione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>metodo viene chiamato e passato alla gerarchia per vedere se sono state apportate modifiche alla soluzione che devono essere immesse nel file con estensione sln.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Un valore null, passato per `QuerySaveSolutionProps` in <xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>, indica che le informazioni vengano resa persistente per la soluzione.</xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> Se il valore non è null, le informazioni persistenti sono per un progetto specifico, determinato dal puntatore per il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
 Se non esistono informazioni da salvare, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>chiamata con un puntatore a interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>(metodo).</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>viene quindi chiamato il metodo da parte dell'ambiente per recuperare le coppie nome-valore da `IPropertyBag` l'interfaccia e scrivere le informazioni nel file con estensione sln.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>  
  
 `SaveSolutionProps`e `WriteSolutionProps` gli oggetti vengono denominati in modo ricorsivo dall'ambiente di recuperare le informazioni viene salvata la `IPropertyBag` interfaccia fino a quando tutte le modifiche sono stati immessi nel file con estensione sln. In questo modo, è possibile garantire che le informazioni vengono rese persistenti con la soluzione e disponibile successiva apertura della soluzione.  
  
 Ogni VSPackage caricato viene enumerato per vedere se dispone di alcuna azione per salvare in file con estensione sln. È solo in fase di caricamento che le chiavi del Registro di sistema vengono eseguita una query. L'ambiente conosce tutti i pacchetti caricati perché sono in memoria al momento che si salva la soluzione.  
  
 Solo i file con estensione sln contiene voci di `preSolution` e `postSolution` sezioni. Vi sono sezioni simile nel file con estensione suo poiché questa informazione per caricare correttamente la soluzione è necessaria. Il file con estensione suo contiene opzioni specifiche dell'utente, ad esempio note, che non sono progettate per essere condivisi o sottoposti a controllo del codice sorgente.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [Opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [Soluzioni](../../extensibility/internals/solutions.md)
