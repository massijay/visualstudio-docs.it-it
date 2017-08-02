---
title: "Architettura di plug-in controllo di origine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origine plug-in del controllo, architettura"
ms.assetid: 35351d4c-9414-409b-98fc-f2023e2426b7
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Architettura di plug-in controllo di origine
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile aggiungere il supporto del controllo del codice sorgente all'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] distribuzione e associando un plug\-in controllo del codice sorgente.  L'ide si connette al plug\-in controllo del codice sorgente tramite il plug\-in controllo del codice sorgente ben definito API.  L'ide espone le funzionalità di controllo della versione del sistema di controllo del codice sorgente di un'interfaccia \(UI\) utente costituita dalle barre degli strumenti e i comandi di menu.  Il plug\-in controllo del codice sorgente implementa la funzionalità di controllo del codice sorgente.  
  
## Risorse di plug\-in controllo del codice sorgente  
 Il plug\-in controllo del codice sorgente fornisce risorse per la creazione e connettere l'applicazione di controllo delle versioni all'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Il plug\-in controllo del codice sorgente contiene la specifica di API che deve essere implementata da un plug\-in controllo del codice sorgente in modo che sia possibile integrare nell'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Contiene anche un esempio di codice \(scritto in C\+\+\) che implementa un plug\-in controllo del codice sorgente di base in cui venga illustrata l'implementazione delle funzioni principali conformi al plug\-in controllo del codice sorgente API.  
  
 La specifica di plug\-in controllo del codice sorgente l'api consente di sfruttare il sistema di controllo del codice sorgente di scelta se si crea una DLL del controllo del codice sorgente con la raccolta di funzioni obbligatorio distribuito in base al plug\-in controllo del codice sorgente API.  
  
## Componenti  
 Il pacchetto di adattatori di controllo del codice sorgente nel diagramma è la parte dell'IDE che converte la richiesta dell'utente per operazioni di controllo del codice sorgente in una chiamata di funzione supportata dal plug\-in controllo del codice sorgente.  Affinché ciò si verifica, l'ide e il plug\-in controllo del codice sorgente devono avere un efficace finestra di dialogo che comunica informazioni avanti e indietro tra IDE e del plug\-in.  Affinché questa finestra di dialogo hanno luogo, entrambi devono presentare lo stesso linguaggio.  Il plug\-in controllo del codice sorgente API descrivere in questa documentazione è il vocabolario comune per questo scambio.  
  
 ![Diagramma dell'architettura di controllo del codice sorgente](~/extensibility/internals/media/vs_sccsdk_plug_in_arch.gif "vs\_sccsdk\_plug\_in\_arch")  
Interazione di rappresentazione del diagramma di architettura tra VS e plug\-in controllo del codice sorgente  
  
 Come illustrato nel diagramma dell'architettura, la shell di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , contrassegnati come VS la shell nel diagramma, ospita i progetti di lavoro e componenti associate dell'utente, ad esempio gli editor e Esplora soluzioni.  Il pacchetto di adattatori di controllo del codice sorgente gestisce l'interazione tra l'ide e il plug\-in controllo del codice sorgente.  Il pacchetto di adattatori di controllo del codice sorgente fornisce la propria interfaccia utente del controllo del codice sorgente.  È l'interfaccia utente di livello superiore che l'utente interagisce per avviare e definire l'ambito di un'operazione di controllo del codice sorgente.  
  
 Il plug\-in controllo del codice sorgente può avere la propria interfaccia utente, che possono essere costituiti da due parti come illustrato nella figura.  La casella relativa interfaccia utente del fornitore„ rappresenta gli elementi dell'interfaccia utente personalizzati che, come autore di plug\-in controllo del codice sorgente, fornire.  Questi verranno visualizzati direttamente dal plug\-in controllo del codice sorgente quando l'utente richiama un'operazione di controllo del codice sorgente avanzata.  La casella relativa interfaccia utente supportato„ è un set di funzionalità dell'interfaccia utente di plug\-in controllo del codice sorgente che vengono richiamate indirettamente tramite l'ide di.  I messaggi Interfaccia utente\-correlati sessioni di plug\-in controllo del codice sorgente dell'IDE con le funzioni di callback speciale fornite dall'IDE.  L'interfaccia utente di supporto facilita un'integrazione più senza con l'ide \(spesso con l'utilizzo di un pulsante di **Avanzate** \) e così fornisce un'esperienza unificata dell'utente finale.  
  
 Un plug\-in controllo del codice sorgente non è possibile apportare modifiche a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sgusciare e, di conseguenza, al pacchetto di adattatori di controllo del codice sorgente o all'interfaccia utente del controllo del codice sorgente fornita dall'IDE.  Deve fare massimo utilizzo della flessibilità offerta dall'implementazione delle diverse funzioni API di plug\-in controllo del codice sorgente che consentono di offrire un'esperienza integrata per l'utente finale.  La sezione di riferimento della documentazione di plug\-in controllo del codice sorgente l'api include informazioni per alcune funzionalità avanzate di plug\-in controllo del codice sorgente.  Per sfruttare queste funzionalità, il plug\-in controllo del codice sorgente necessario dichiarare le relative funzionalità avanzate IDE durante l'inizializzazione e deve implementare le funzioni avanzate specifiche per ogni funzionalità.  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../../extensibility/source-control-plug-ins.md)   
 [Glossario](../../extensibility/source-control-plug-in-glossary.md)   
 [Creazione di plug\-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)