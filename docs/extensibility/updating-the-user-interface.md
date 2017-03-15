---
title: "Aggiornamento dell&#39;interfaccia utente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfacce utente, l'aggiornamento"
  - "comandi, l'aggiornamento dell'interfaccia utente"
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
caps.latest.revision: 41
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 41
---
# Aggiornamento dell&#39;interfaccia utente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dopo aver implementato un comando, è possibile aggiungere codice per aggiornare l'interfaccia utente con lo stato dei comandi della nuovi.  
  
 In una tipica applicazione Win32, il set di comandi può essere continuamente sottoposto a polling e lo stato dei singoli comandi può essere modificato come le visualizza all'utente. Tuttavia, poiché il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell può ospitare un numero illimitato di package VS, polling esteso può diminuire la velocità di risposta, in particolare il polling tra gli assembly di interoperabilità tra codice gestito e COM.  
  
### Per aggiornare l'interfaccia utente  
  
1.  Effettuare uno dei passaggi indicati di seguito.  
  
    -   Chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A>.  
  
         Un <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia può essere ottenuto dal <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio, come indicato di seguito.  
  
        ```c#  
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)  
        {  
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));  
            if (vsShell != null)  
            {  
                int hr = vsShell.UpdateCommandUI(0);  
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);  
            }  
        }  
  
        ```  
  
         Se il parametro del <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> è diverso da zero \(`TRUE`\), quindi l'aggiornamento viene eseguito in modo sincrono e immediatamente. È consigliabile passare zero \(`FALSE`\) per questo parametro garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file vsct. Tuttavia, utilizzare il flag con cautela o può ridurre le prestazioni. Per ulteriori informazioni sui flag di comando, vedere il [Elemento di Flag di comando](../extensibility/command-flag-element.md) documentazione.  
  
    -   In package VS che ospitano un controllo ActiveX utilizzando il modello di attivazione sul posto in una finestra, potrebbe essere più opportuno utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodo. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia e il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaccia sono funzionalmente equivalenti. Sia che l'ambiente ripetere la query lo stato di tutti i comandi. In genere, un aggiornamento non viene eseguito immediatamente. Al contrario, un aggiornamento viene ritardato fino al tempo di inattività. La shell memorizza nella cache lo stato del comando per aiutare a garantire prestazioni ottimali. Se si desidera evitare la memorizzazione nella cache, applicare il `DontCache` flag quando si crea il comando nel file vsct. Tuttavia, utilizzare il flag con cautela in quanto può ridurre le prestazioni.  
  
         Si noti che è possibile ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> interfaccia chiamando il `QueryInterface` metodo su un <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> dell'oggetto o per ottenere l'interfaccia dal <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> servizio.  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementazione](../extensibility/internals/command-implementation.md)