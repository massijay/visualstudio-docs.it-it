---
title: "Servizi forniti (origine controllo VSPackage) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi, i pacchetti di controllo di origine"
  - "pacchetti di controllo di origine, i servizi"
ms.assetid: 9db07d70-87d2-4401-bc88-e3a49d81e9a2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Servizi forniti (origine controllo VSPackage)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

I servizi sono il meccanismo principale tra cui la funzionalità è condivisa tra Vspackage e tra l'ambiente di sviluppo integrato di Visual \(IDE\) Studio e il relativo Vspackage installato.  Per una descrizione dettagliata di servizi e in ordine di importanza nell'IDE di Visual Studio, vedere[Utilizzo e servizi](../../extensibility/using-and-providing-services.md).  
  
## Il servizio di controllo del codice sorgente  
 Visual Studio fornisce due livelli di servizi, di servizi a livello dell'IDE e di servizi a livello del pacchetto.  L'IDE di Visual Studio a livello nativo fornisce ai servizi a livello dell'IDE.  Il pacchetto del controllo del codice sorgente utilizza alcuni di questi servizi.  Il pacchetto del controllo del codice sorgente come package VS condivide la funzionalità di controllo del codice sorgente fornendo un servizio di controllo del codice sorgente privato dei propri.  Il pacchetto del controllo del codice sorgente incapsula il set di interfacce controllo\-correlate database di origine implementate da sotto forma di contratto che può essere utilizzato dall'IDE di Visual Studio.  
  
## Vedere anche  
 [Elementi di progettazione](../../extensibility/internals/source-control-vspackage-design-elements.md)