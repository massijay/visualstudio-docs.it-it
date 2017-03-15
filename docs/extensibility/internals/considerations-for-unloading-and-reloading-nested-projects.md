---
title: "Considerazioni per scaricare e ricaricare progetti annidati | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti annidati, scaricare e ricaricare"
  - "progetti [Visual Studio SDK], scaricare e ricaricare nidificati"
ms.assetid: 06c3427e-c874-45b1-b9af-f68610ed016c
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Considerazioni per scaricare e ricaricare progetti annidati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si distribuiscono i tipi di progetto annidati, è necessario eseguire passaggi aggiuntivi quando si scaricano e si ricarica i progetti.  Per poter aggiornare i listener agli eventi della soluzione, è necessario correttamente generare eventi di `OnAfterLoadProject` e di `OnBeforeUnloadProject` .  
  
 Un motivo che è necessario generare questi eventi in questo modo è che non si desidera che il \(SCC\) controllo del codice sorgente per rimuovere elementi da server e quindi aggiungerli nuovamente come qualcosa di nuovo se c " è un'operazione di `Get` da SCC.  In tal caso, un nuovo file verrebbe caricata da SCC ed è necessario scaricare e ricaricare tutti i file nel caso siano diversi.  Lo SCC chiama `ReloadItem`.  L'implementazione della chiamata è di eliminare il progetto e di ricrearlo ancora implementando `IVsFireSolutionEvents` per chiamare `OnBeforeUnloadProject` e `OnAfterLoadProject`.  Quando si esegue questa implementazione, lo SCC è presente che il progetto temporaneamente è stato eliminato e aggiunto nuovamente.  Di conseguenza, lo SCC non funziona nel progetto come se il progetto è effettivamente in sia stato eliminato dal server e quindi sia stato aggiunto nuovamente.  
  
## ricaricare i progetti  
 Per supportare ricaricare i progetti annidati, si implementa il metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.ReloadItem%2A> .  Nell'implementazione di `ReloadItem`, chiudere i progetti annidati e li si ricrea.  
  
 In genere, quando un progetto è ricaricato, l'IDE genera gli eventi <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnBeforeUnloadProject%2A> e `M:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3.OnAfterLoadProject(Microsoft.VisualStudio.Shell.Interop.IVsHierarchy,Microsoft.VisualStudio.Shell.Interop.IVsHierarchy)`.  Tuttavia, per i progetti annidati che verranno eliminate e ricaricati, il progetto padre avvia il processo, non l'ide.  Poiché il progetto padre non genera eventi della soluzione e l'ide non dispone di informazioni relative all'inizializzazione del processo, gli eventi non vengono generati.  
  
 Per gestire questo processo, le chiamate `QueryInterface` di progetto padre sull'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFireSolutionEvents> fuori dall'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> .  `IVsFireSolutionEvents` dispone di funzioni che comunicano all'IDE di generare l'evento di `OnBeforeUnloadProject` per scaricare il progetto annidato e quindi genera l'evento di `OnAfterLoadProject` per ricaricare lo stesso progetto.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents3>   
 [Progetti di annidamento](../../extensibility/internals/nesting-projects.md)