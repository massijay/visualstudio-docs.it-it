---
title: "Creazione di un pacchetto di controllo di origine | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente [Visual Studio SDK], creazione di pacchetti di controllo di origine"
  - "pacchetti di controllo di origine"
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Creazione di un pacchetto di controllo di origine
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Questa documentazione sono inclusi collegamenti a informazioni generali sull'architettura di un pacchetto del controllo del codice sorgente integrato con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], l'API definito dalle interfacce da implementare e dai servizi da utilizzare e un esempio in cui viene illustrata un'implementazione semplice del pacchetto del controllo del codice sorgente.  
  
 Con un controllo del codice sorgente package VS, è possibile creare un percorso completo di integrazione per il controllo del codice sorgente integriate con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Consente al pacchetto per ignorare la UI predefinita del controllo del codice sorgente contenuto in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], per rispondere alle richieste del controllo del codice sorgente dal sistema del progetto e interagire con i componenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] come **Esplora soluzioni**.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] autorizza partner di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] con un meccanismo per creare un package VS che possa integrarsi con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando un modello di servizi.  
  
## In questa sezione  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Viene descritto il pacchetto del controllo del codice sorgente, che rappresenta un'alternativa più avanzata al plug\-in controllo del codice sorgente per implementare funzionalità di controllo del codice sorgente in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Architettura](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Viene fornito un diagramma e illustrati i componenti di un pacchetto del controllo del codice sorgente.  
  
 [Funzionalità](../../extensibility/internals/source-control-vspackage-features.md)  
 Vengono descritte le varie funzionalità di un pacchetto del controllo del codice sorgente.  
  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Viene descritta la struttura del package VS che un pacchetto del controllo del codice sorgente deve implementare per l'integrazione approfondita.  
  
## Sezioni correlate  
 [Creazione di plug\-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Viene illustrato come creare un plug\-in del controllo del codice sorgente che fornisce la funzionalità di controllo del codice sorgente dell'interfaccia utente del controllo del codice sorgente di \(UI\) [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  
  
 [Controllo del codice sorgente](../../extensibility/internals/source-control.md)  
 Vengono descritte le opzioni per implementare il controllo del codice sorgente come una funzionalità integrata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].