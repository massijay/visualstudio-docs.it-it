---
title: "Configurazione del progetto per l&#39;Output | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "le configurazioni di progetto, di output"
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Configurazione del progetto per l&#39;Output
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ogni configurazione può supportare un set di processi di compilazione che generano gli elementi di output come file eseguibile o una risorsa. Questi elementi di output sono privati per l'utente e possono essere inseriti in gruppi che si collegano i tipi correlati di output come file eseguibili \(.exe,. dll,. lib\) e i file di origine \(con estensione idl, file con estensione h\).  
  
 Gli elementi di output possono essere resi disponibili tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> metodi ed enumerato con il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> metodi. Quando si desidera raggruppare gli elementi di output, il progetto deve inoltre implementare la <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> interfaccia.  
  
 Il costrutto sviluppato implementando `IVsOutputGroup` consente ai progetti di gruppo di output in base all'utilizzo. Ad esempio, una DLL potrebbe essere raggruppata con il database di programma \(PDB\).  
  
> [!NOTE]
>  Un file PDB contiene informazioni di debug e viene creata quando l'opzione 'Genera informazioni di Debug' è specificata quando si compila il file DLL o .exe. Il file con estensione PDB in genere viene generato per la configurazione di progetto di Debug solo.  
  
 Il progetto deve restituire lo stesso numero di gruppi per ogni configurazione che supporta, anche se il numero di output contenuti all'interno di un gruppo può variare da una configurazione alla configurazione. Ad esempio, Matt del progetto DLL potrebbe includano mattd.dll e mattd.pdb nella configurazione Debug, ma solo matt.dll nella configurazione di vendita al dettaglio.  
  
 I gruppi dispongono inoltre le informazioni sull'identificatore stesso, ad esempio nome canonico, nome visualizzato e informazioni di gruppo, dalla configurazione alla configurazione all'interno di un progetto. Questa coerenza consente e distribuzione dei pacchetti per continuare a funzionare anche se modificare le configurazioni.  
  
 Gruppi possono anche avere un output chiave che consente di scelta rapida creazione di pacchetti in modo che punti a un nome significativo. Qualsiasi gruppo potrebbe essere vuoto in una determinata configurazione, pertanto non devono essere fatte supposizioni sulle dimensioni di un gruppo. La dimensione \(numero di output\) di ogni gruppo in qualsiasi configurazione può essere diversa dalla dimensione di un altro gruppo nella stessa configurazione. Può inoltre essere diversa da quelle dello stesso gruppo in un'altra configurazione.  
  
 ![Rappresentazione grafica dei gruppi di output](~/extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups")  
Gruppi di output  
  
 L'utilizzo principale della <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> interfaccia consiste nel fornire l'accesso per compilare, distribuire e il debug di oggetti di gestione e consentire la libertà di output gruppo di progetti. Per ulteriori informazioni sull'utilizzo di questa interfaccia, vedere [Oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md).  
  
 Nel diagramma precedente, compilato gruppo dispone di una chiave output tra le configurazioni \(bD.exe o b.exe\), pertanto l'utente può creare un collegamento a incorporati e sapere che il collegamento funziona indipendentemente dalla configurazione distribuita. Origine del gruppo non dispone di una chiave di output, pertanto l'utente non può creare un collegamento. Se il gruppo di eseguire il Debug compilata è una chiave di output, ma il gruppo di vendita al dettaglio compilato non, che potrebbe essere l'implementazione non corretta. Di conseguenza, quindi, se tutte le configurazioni dispone di un gruppo che non contiene alcun output, e, di conseguenza, nessun file di chiave, quindi altre configurazioni con il gruppo che contengono gli output non possono avere i file di chiave. Gli editor di programma di installazione si presuppongono che i nomi canonici e nomi visualizzati dei gruppi, nonché l'esistenza di un file di chiave, non modificare in configurazioni di base.  
  
 Si noti che se un progetto ha un `IVsOutputGroup` che non desidera pacchetti o la distribuzione, è sufficiente per non inserire l'output in un gruppo. L'output può comunque essere enumerato in genere implementando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> metodo che restituisce tutti gli output della configurazione indipendentemente dal raggruppamento.  
  
 Per ulteriori informazioni, vedere l'implementazione di `IVsOutputGroup` nell'esempio di progetto personalizzato alla [MPF per i progetti](http://mpfproj12.codeplex.com).  
  
## Vedere anche  
 [Gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md)   
 [Configurazione del progetto per la compilazione](../../extensibility/internals/project-configuration-for-building.md)   
 [Oggetto di configurazione di progetto](../../extensibility/internals/project-configuration-object.md)   
 [Configurazione di soluzione](../../extensibility/internals/solution-configuration.md)