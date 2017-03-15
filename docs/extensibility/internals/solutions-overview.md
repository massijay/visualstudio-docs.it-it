---
title: Panoramica delle soluzioni | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions, about solutions
ms.assetid: 3b21e3a1-170a-4485-941e-6b04b7b27886
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
ms.openlocfilehash: 06ca562112b8b6feb711219502e3d10b1cb6f462
ms.lasthandoff: 02/22/2017

---
# <a name="solutions-overview"></a>Panoramica delle soluzioni
Una soluzione è un raggruppamento di uno o più progetti che interagiscono per creare un'applicazione. Le informazioni di progetto e lo stato relativo alla soluzione vengono archiviati in due file di soluzione diversa. Il file di soluzione (sln) è basato su testo e possono essere sottoposti a controllo del codice sorgente e condivisi tra gli utenti. Il file della soluzione utente opzione (con estensione suo) è binario. Di conseguenza, il file con estensione suo non può essere inserito nel controllo del codice sorgente e contiene informazioni specifiche dell'utente.  
  
 Qualsiasi VSPackage è possibile scrivere su dei tipi di file della soluzione. A causa della natura dei file, esistono due diverse interfacce implementate per scrivere in esse. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>interfaccia scrive le informazioni di testo per il file con estensione sln e <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>interfaccia scrive flussi binari per il file con estensione suo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>  
  
> [!NOTE]
>  Un progetto non è necessario scrivere in modo esplicito una voce per se stesso nel file di soluzione; l'ambiente gestito che per il progetto. Pertanto, a meno che non si desidera aggiungere contenuto aggiuntivo in modo specifico per il file della soluzione, non è necessario registrare il pacchetto Visual Studio in questo modo.  
  
 Ogni pacchetto Visual Studio che supporta la persistenza soluzione utilizza tre interfacce, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>interfaccia, che viene implementata dall'ambiente e chiamato dal VSPackage, e `IVsPersistSolutionProps` e `IVsPersistSolutionOpts`, che sono entrambi implementati dal VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> Il `IVsPersistSolutionOpts` interfaccia deve solo essere implementata nel caso in cui scrivere il file con estensione suo dal VSPackage informazioni private.  
  
 Quando viene aperta una soluzione, il processo seguente viene eseguita.  
  
1.  L'ambiente legge la soluzione.  
  
2.  Se l'ambiente rileva un `CLSID`, carica il VSPackage corrispondente.  
  
3.  Se viene caricato un package VS, l'ambiente chiama `QueryInterface` per <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>interfaccia, per l'interfaccia che richiede il VSPackage.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>  
  
    1.  Durante la lettura da un file con estensione sln, l'ambiente chiama `QueryInterface` per `IVsPersistSolutionProps`.  
  
    2.  Durante la lettura da un file con estensione suo, l'ambiente chiama `QueryInterface` per `IVsPersistSolutionOpts`.  
  
 Informazioni specifiche relative all'utilizzo di questi file sono reperibile nella [soluzione (. File sln)](../../extensibility/internals/solution-dot-sln-file.md) e [opzioni utente della soluzione (. File suo)](../../extensibility/internals/solution-user-options-dot-suo-file.md).  
  
> [!NOTE]
>  Se si desidera creare una nuova configurazione di soluzione composta da configurazioni due progetti e l'esclusione di un terzo dalla compilazione, è necessario utilizzare l'interfaccia utente di pagine di proprietà o l'automazione. Non è possibile modificare direttamente le configurazioni di manager di compilazione di soluzioni e le relative proprietà, ma è possibile modificare il gestore di compilazione della soluzione utilizzando la `SolutionBuild` classe da DTE nel modello di automazione. Per ulteriori informazioni sulla configurazione di soluzioni, vedere [configurazione di soluzione](../../extensibility/internals/solution-configuration.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage></xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>
