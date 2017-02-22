---
title: "Per determinare se implementare un VSPackage di controllo di origine | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "pacchetti di controllo di origine, sui pacchetti di controllo di origine"
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Per determinare se implementare un VSPackage di controllo di origine
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questa sezione elabora le scelte dei collegamenti del controllo del codice sorgente e del controllo del codice sorgente Vspackage per le soluzioni per l'estensione del controllo del codice sorgente e vengono fornite indicazioni di massima su scegliere un percorso appropriato di integrazione.  
  
## Small Source Control Solution with Limited Resources  
 Se si dispone di risorse limitate e non può essere caricati con il sovraccarico di scrittura del pacchetto del controllo del codice sorgente, è possibile creare i collegamenti in base all'API di plug\-in controllo del codice sorgente.  In questo modo che l'esecuzione side\-by\-side con pacchetti del controllo del codice sorgente e passare dai plug\-in controllo del codice sorgente e compresso su richiesta.  Per ulteriori informazioni, vedere [Registrazione e la selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
## Grande soluzione del controllo del codice sorgente con un'ampia gamma di funzionalità  
 Se si desidera distribuire una soluzione del controllo del codice sorgente che fornisce un modello di controllo del codice sorgente completo che non venga acquisito adeguatamente tramite il plug\-in controllo del codice sorgente API, è possibile considerare un pacchetto del controllo del codice sorgente come percorso di integrazione.  Questo vale specialmente se invece si è sostituito il pacchetto dell'adattatore di controllo del codice sorgente \(che comunica con collegamenti del controllo del codice sorgente e fornisce un'interfaccia utente del controllo del codice sorgente di base\) con diventi proprietaria in modo da poter gestire automaticamente gli eventi del controllo del codice sorgente in modo personalizzato.  Se già si dispone di un'interfaccia utente soddisfacente del controllo del codice sorgente e si desidera mantenere tale esperienza di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'opzione del pacchetto del controllo del codice sorgente consente di fare semplicemente la.  Il pacchetto del controllo del codice sorgente non è generico ed è progettato esclusivamente per l'utilizzo con l'ide di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
 Se si desidera distribuire una soluzione del controllo del codice sorgente che offre flessibilità e controllo più dettagliato sulla logica e l'interfaccia utente del controllo del codice sorgente, è possibile utilizzare le route di integrazione del pacchetto del controllo del codice sorgente.  È possibile:  
  
1.  Registrare il provider dell'attività con il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>,  che restituisce un valore del cookie che deve essere utilizzato per identificare in modo univoco il provider di attività in tutte le transazioni successive.  
  
2.  Sostituire la UI predefinita del controllo del codice sorgente con l'interfaccia utente personalizzata \(vedere [Interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)\).  
  
3.  Specificare i glifi di utilizzo e gestione degli eventi del glifo di Esplora soluzioni \(vedere [Icona controllo](../../extensibility/internals/glyph-control-source-control-vspackage.md)\).  
  
4.  Modifica di query e gestire eventi di salvataggio di query \(vedere [Query modifica Query Salva](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)\).  
  
## Vedere anche  
 [Creazione di plug\-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)