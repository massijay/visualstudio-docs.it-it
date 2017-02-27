---
title: "Introduzione al Plug-in del controllo codice sorgente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origine plug-in del controllo, introduzione"
  - "Getting started, origine controllo plug-in"
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 21
---
# Introduzione al Plug-in del controllo codice sorgente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Per creare un plug\-in del controllo del codice sorgente, è necessario creare una DLL che implementa le funzioni definite nel plug\-in controllo del codice sorgente API e quindi registrare la DLL con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per renderla disponibile disponibile per l'utilizzo nel controllo della versione del codice sorgente.  
  
 Tre versioni del plug\-in controllo del codice sorgente l'API \(versioni 1,1, 1,2 e 1,3\) sono disponibili per i collegamenti del controllo del codice sorgente.  Il plug\-in controllo del codice sorgente API documentato di seguito è 1,3.  È stato progettato per essere completamente compatibili con collegamenti del controllo del codice sorgente che supportano le versioni 1,1 e 1,2.  [Novità di origine controllo plug\-in API versione 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) La sezione vengono illustrate le nuove funzionalità supportate nella versione più recente del plug\-in controllo del codice sorgente API.  
  
## In questa sezione  
 [Procedura: installare un plug\-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Viene descritto come rendere le voci del Registro di sistema che sono necessarie inserire una DLL del controllo del codice sorgente.  
  
 [Novità di origine controllo plug\-in API versione 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Viene fornita una breve panoramica delle modifiche apportate al plug\-in controllo del codice sorgente API nella versione 1,3.  
  
 [Novità di origine controllo plug\-in API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Viene fornita una breve panoramica delle modifiche apportate al plug\-in controllo del codice sorgente API nella versione 1,2.  
  
## Sezioni correlate  
 [Plug\-in del controllo codice sorgente](../../extensibility/source-control-plug-ins.md)  
 Viene fornito un elenco completo di tutti gli elementi nel plug\-in controllo del codice sorgente API.  
  
 [Creazione di plug\-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definisce il plug\-in controllo del codice sorgente SDK e descritte le risorse incluse.