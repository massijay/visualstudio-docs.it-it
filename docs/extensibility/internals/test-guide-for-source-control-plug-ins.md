---
title: "Guida per i test per il Plug-in di controllo codice sorgente | Microsoft Docs"
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
  - "plug-in controllo del codice sorgente"
  - "controllo del codice sorgente [Visual Studio SDK], plug-in di test"
  - "test, plug-in del controllo codice sorgente"
  - "test, plug-in controllo codice sorgente"
  - "origine plug-in del controllo, Guida per i test"
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 26
caps.handback.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
---
# Guida per i test per il Plug-in di controllo codice sorgente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questa sezione vengono fornite istruzioni per testare il plug\-in controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Gli estesi cenni preliminari sulle aree il test più comuni nonché alcune delle aree più complesse che possono essere problematiche vengono forniti.  Questi cenni preliminari non deve essere un elenco completo dei test case.  
  
> [!NOTE]
>  Alcuni correzione dei bug e miglioramenti all'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono verificare problemi con i collegamenti esistenti del controllo del codice sorgente che non sono stati rilevati utilizzando le versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  È consigliabile testato il plug\-in controllo del codice sorgente esistente per le aree enumerate in questa sezione, anche se non sono state apportate modifiche al plug\-nella versione precedente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## preparazione comune  
 Un computer con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e il plug\-in controllo del codice sorgente di destinazione installato, è obbligatori.  Un secondo computer analogamente configurato può essere utilizzato per qualsiasi oggetto aperto da test del controllo del codice sorgente.  
  
## Definizione dei termini  
 In questa guida di test, utilizzare le seguenti definizioni di termine:  
  
 progetto client  
 Qualsiasi tipo di progetto disponibile in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che supporta l'integrazione del controllo del codice sorgente \(ad esempio, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]\).  
  
 Progetto Web  
 Esistono quattro tipi di progetti Web: File system, IIS locale, siti remoti e FTP.  
  
-   I progetti di file system vengono creati in un percorso locale, ma non richiedono Internet Information Services \(IIS\) siano installati mentre si accede internamente da percorso UNC e possono essere inseriti nel controllo del codice sorgente dall'IDE, come i progetti client.  
  
-   Di progetti di lavoro locale di IIS con IIS installato nello stesso computer e si accede con un URL che punta al computer locale.  
  
-   I progetti di siti remoti vengono creati nei servizi di un IIS, ma vengono inseriti nel controllo del codice sorgente nel computer del server IIS e non dall'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
-   I progetti FTP si accede tramite un server FTP remoto ma non possono essere inseriti nel controllo del codice sorgente.  
  
 integrazione  
 Un altro termine della soluzione o il progetto nel controllo del codice sorgente.  
  
 Archivio della versione  
 Il database di controllo del codice sorgente che accede al plug\-in controllo del codice sorgente API.  
  
## Aree di illustrate in questa sezione  
  
-   [Area di test 1: Aggiungere a \/ Apri dal controllo del codice sorgente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   caso 1a: Aggiungere la soluzione al controllo del codice sorgente  
  
    -   caso 1b: Aprire la soluzione dal controllo del codice sorgente  
  
    -   caso 1c: Aggiungere la soluzione dal controllo del codice sorgente  
  
-   [Area di test 2: Ottenere dal controllo del codice sorgente](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Area test 3: Estrazione \/ Annulla estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   caso 3: Estrarre\/l'estrazione ripristina  
  
    -   caso 3a: Estrai  
  
    -   caso 3b: L'estrazione disconnesso  
  
    -   caso 3c: Modifica della query\/salvataggio di query \(QEQS\)  
  
    -   caso 3d: L'estrazione silent  
  
    -   caso 3e: L'estrazione di annullamento  
  
-   [Test Area 4: Check\-](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   caso 4a: elementi modificati  
  
    -   caso 4b: Aggiunta di file  
  
    -   caso 4c: Aggiunta di progetti  
  
-   [Area test 5: Modifica controllo del codice sorgente](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   caso 5a: associazione  
  
    -   caso 5b: separare  
  
    -   caso 5c: riassociare  
  
-   [Test Area 6: eliminare](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Test Area 7: condivisione](../../extensibility/internals/test-area-7-share.md)  
  
-   [Test Area 8: Cambio del plug\-](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   caso 8a: modifica automatica  
  
    -   caso 8b: La modifica basata su soluzione  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../../extensibility/source-control-plug-ins.md)