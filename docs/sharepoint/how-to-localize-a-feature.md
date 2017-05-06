---
title: "Procedura: localizzare una funzionalit&#224;"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "funzionalità [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, localizzazione"
ms.assetid: 66a0b389-1f71-421f-9817-a19840765d83
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: localizzare una funzionalit&#224;
  Per impostazione predefinita, per i titoli e le descrizioni delle funzionalità vengono utilizzati valori stringa hardcoded.  Per localizzare il titolo e la descrizione di una funzionalità, sostituire le stringhe con espressioni che fanno riferimento alle risorse localizzate.  
  
## Localizzazione di una funzionalità  
  
#### Per localizzare una funzionalità  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **Feature1**, quindi scegliere **Aggiungi risorsa di funzionalità**.  
  
2.  Nella finestra di dialogo **Aggiungi risorsa**, scegliere **Lingua invariante** dall'elenco come impostazioni cultura per il file di risorse di funzionalità di linguaggio predefinito.  
  
3.  Ripetere questo passaggio per ogni lingua localizzata, selezionando le lingue desiderate per i file di risorse della funzionalità localizzati.  
  
     Sono stati creati file di risorse di funzionalità separati: uno per la lingua predefinita e uno per ogni lingua localizzata da supportare.  
  
4.  Aprire ogni file di risorse nell'Editor risorse e immettere tutti gli ID di stringa e i relativi valori.  
  
     Nel file di risorse della funzionalità predefinito immettere, ad esempio, un ID di stringa Title con il valore My Feature Title e un secondo ID di stringa Description con il valore My Feature Description.  Per ogni file di risorse localizzato, utilizzare lo stesso ID di stringa utilizzato nella risorsa della funzionalità predefinita, ma immettere stringhe localizzate per i valori.  
  
5.  Dopo l'immissione dei valori delle risorse, aprire il menu di scelta rapida per la funzionalità \(ad esempio Feature1.feature\) e quindi scegliere **Progettazione viste** per aprire la funzionalità in progettazione funzionalità.  
  
6.  Per localizzare i campi **Title** e **Description** nella funzionalità, immettere i valori desiderati nelle rispettive caselle utilizzando il formato seguente:  
  
     `$Resources:` *String ID*  
  
     Immettere, ad esempio, $Resources:Title nella casella **Feature Title** e $Resources:Description nella casella **Feature Description**.  
  
     L'ID di stringa deve corrispondere a quelli utilizzati nei file di risorse.  
  
7.  Premere il tasto F5 per compilare ed eseguire l'applicazione.  
  
8.  In SharePoint aprire il menu **Azioni sito**, scegliere **Azioni sito**, quindi, nella sezione **Azioni sito** scegliere il link **Gestisci caratteristiche sito**.  
  
9. In SharePoint modificare la lingua di visualizzazione predefinita.  
  
     Nell'applicazione verranno visualizzati il titolo e la descrizione della funzionalità localizzata.  Per la visualizzazione delle risorse localizzate, è necessario che nel server SharePoint sia installato un Language Pack corrispondente alle impostazioni cultura del file di risorse.  
  
## Vedere anche  
 [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)   
 [Procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Procedura: localizzare il codice](../sharepoint/how-to-localize-code.md)  
  
  