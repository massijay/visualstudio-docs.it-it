---
title: "Origine controllo integrazione Essentials | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integrazione del controllo codice sorgente, essentials"
  - "Integrazione del controllo codice sorgente, cenni preliminari"
  - "Essentials, integrazione del controllo codice sorgente"
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Origine controllo integrazione Essentials
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta due tipi di elenchi di controllo del codice sorgente: un plug\-in controllo del codice sorgente che fornisce la funzionalità di base e compilato utilizzando il plug\-in controllo del codice sorgente API \(precedentemente noto come il MSSCCI API\) e a una soluzione basata VSPackage di integrazione del controllo del codice sorgente che fornisce le funzionalità più affidabile.  
  
## Plug\-in controllo del codice sorgente  
 Un plug\-in controllo del codice sorgente viene scritto come DLL che implementa il plug\-in controllo del codice sorgente API.  La funzionalità di integrazione del controllo del codice sorgente e di registrazione viene fornita tramite l'API.  Questo approccio è più facile l'implementazione di un controllo del codice sorgente VSPackage e utilizza l'interfaccia utente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(UI\) per la maggior parte delle operazioni di controllo del codice sorgente.  
  
 Per implementare un plug\-in controllo del codice sorgente utilizzando il plug\-in controllo del codice sorgente API, attenersi alla seguente procedura:  
  
1.  Creazione di una DLL che implementa le funzioni specificate in [Plug\-in del controllo codice sorgente](../../extensibility/source-control-plug-ins.md).  
  
2.  Registrare la DLL utilizzando le voci del Registro di sistema appropriate, come descritto [Procedura: installare un plug\-in del controllo del codice sorgente](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)in.  
  
3.  Creare un'interfaccia utente di supporto e visualizzare una volta richiesta dal pacchetto dell'adattatore di controllo del codice sorgente \(la parte di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che gestisce la funzionalità di controllo del codice sorgente tramite collegamenti del controllo del codice sorgente.  
  
 Per ulteriori informazioni, vedere [Creazione di plug\-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## Controllo del codice sorgente VSPackage  
 Un'implementazione di package VS del controllo del codice sorgente consente di compilare una sostituzione personalizzata per l'interfaccia utente del controllo del codice sorgente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Questo approccio fornisce il controllo completo di integrazione del controllo del codice sorgente, ma è necessario specificare gli elementi dell'interfaccia utente e di implementare le interfacce del controllo del codice sorgente che sarebbero altrimenti fornite sotto vantaggi dell'utilizzo del plug\-in.  
  
 Per implementare un controllo del codice sorgente package VS, è necessario:  
  
1.  Creare e registrare possiedono il controllo del codice sorgente package VS, come descritto [Registrazione e la selezione](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)in.  
  
2.  Sostituire la UI predefinita del controllo del codice sorgente con l'interfaccia utente personalizzata.  Vedere [Interfaccia utente personalizzata](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Specificare i glifi di utilizzo e gestione degli eventi del glifo di **Esplora soluzioni** .  Vedere [Icona controllo](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  La modifica di query di handle e la query salvano gli eventi, [Query modifica Query Salva](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)come illustrato in.  
  
 Per ulteriori informazioni, vedere [Creazione di un pacchetto di controllo di origine](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## Vedere anche  
 [Panoramica](../../extensibility/internals/source-control-integration-overview.md)   
 [Creazione di plug\-in un controllo del codice sorgente](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Creazione di un pacchetto di controllo di origine](../../extensibility/internals/creating-a-source-control-vspackage.md)