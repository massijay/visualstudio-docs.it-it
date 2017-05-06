---
title: "Procedura: aggiungere e rimuovere dipendenze di funzionalit&#224;"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MICROSOFT.VISUALSTUDIO.SHAREPOINT.DESIGNERS.CUSTOMDEPENDENCYWINDOW"
  - "VS.SHAREPOINTTOOLS.RAD.FEATUREDESIGNERDEPENDENCY"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, funzionalità"
ms.assetid: 2b34c8d9-c975-4fe9-b8e0-52db4a6014ea
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Procedura: aggiungere e rimuovere dipendenze di funzionalit&#224;
  La funzionalità SharePoint in uso può dipendere da altre funzionalità per quanto concerne il funzionamento o i dati.  In questi casi, è possibile contrassegnare queste altre funzionalità come dipendenze della funzionalità in uso.  In questo modo, il server SharePoint assicura che le funzionalità dipendenti vengano attivate prima della funzionalità in uso.  
  
## Aggiunta di dipendenze  
 Nella soluzione è possibile aggiungere altre funzionalità come dipendenze.  In questo modo, è possibile assicurarsi che le funzionalità obbligatorie vengano installate e attivate prima dell'installazione della funzionalità in uso.  
  
#### Per aggiungere una dipendenza a una funzionalità nella soluzione  
  
1.  Aprire progettazione funzionalità, espandere il nodo **Dipendenze di attivazione funzionalità** quindi scegliere il pulsante di **Aggiungi**.  
  
2.  Nella finestra di dialogo **Aggiungi dipendenze di attivazione funzionalità**, scegliere il pulsante di opzione **Aggiungi una dipendenza a funzionalità nella soluzione**, scegliere il titolo della funzionalità che si desidera aggiungere come dipendenza quindi selezionare il pulsante di **Aggiungi**.  
  
     È possibile aggiungere più di una funzionalità scegliendo più titoli premendo il tasto CTRL.  
  
## Aggiunta di dipendenze personalizzate  
 È possibile aggiungere funzionalità che sono già state distribuite in un server SharePoint come dipendenza.  In questo modo, il processo di attivazione di SharePoint garantisce il controllo dell'attivazione di tutte le funzionalità dipendenti prima dell'installazione della funzionalità in uso.  
  
#### Per aggiungere una dipendenza mediante l'ID della funzionalità  
  
1.  Aprire progettazione funzionalità, espandere il nodo **Dipendenze di attivazione funzionalità** quindi scegliere il pulsante di **Aggiungi**.  
  
2.  Nella finestra di dialogo **Aggiungi dipendenze di attivazione funzionalità**, scegliere il pulsante di opzione **Aggiungi dipendenza personalizzata**.  
  
3.  Nella casella di testo **Feature ID** immettere il GUID per la funzionalità che si desidera contrassegnare come dipendenza di attivazione, e scegliere il pulsante **Aggiungi**.  
  
## Modifica di dipendenze personalizzate  
 Le dipendenze personalizzate aggiunte precedentemente possono essere modificate,  tuttavia le funzionalità dipendenti che si trovano nella soluzione possono solo essere rimosse e non modificate.  
  
#### Per modificare una dipendenza di una funzionalità nella soluzione  
  
1.  Aprire progettazione funzionalità quindi espandere il nodo **Dipendenze di attivazione funzionalità**.  
  
2.  Scegliere il nome della funzionalità che si desidera modificare e quindi scegliere il pulsante **Modifica**.  
  
3.  Nella finestra di dialogo **Modifica dipendenza di attivazione funzionalità personalizzata**, modificare il titolo, l'id della funzionalità, o la descrizione e quindi scegliere il pulsante **Invia**.  
  
## Rimozione di dipendenze  
  
#### Per rimuovere una dipendenza da una funzionalità nella soluzione  
  
1.  Nella finestra di progettazione della funzionalità, espandere il nodo **Dipendenze di attivazione funzionalità**, scegliere il nome della funzionalità che si desidera rimuovere e quindi scegliere il pulsante **Rimuovi**.  
  
## Vedere anche  
 [Creazione di funzionalità SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  