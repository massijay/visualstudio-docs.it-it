---
title: "How to: Define the Type Descriptor of a Parameter | Microsoft Docs"
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
  - "Business Data Connectivity service [SharePoint development in Visual Studio], type descriptor"
  - "BDC [SharePoint development in Visual Studio], parameter types"
  - "BDC [SharePoint development in Visual Studio], type descriptor"
  - "Business Data Connectivity service [SharePoint development in Visual Studio], parameter types"
ms.assetid: 7494559f-1567-4cbd-bde0-05a2ed288c3a
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# How to: Define the Type Descriptor of a Parameter
  Un descrittore di tipo contiene proprietà che descrivono il tipo di dati di un parametro.  Può definire un campo, un'entità o una raccolta di entità.  Per altre informazioni, vedere [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### Definire il descrittore di tipo di un parametro  
  
1.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati**, scegliere il descrittore di tipo del parametro.  
  
2.  Nella barra dei menu scegliere **Visualizza**, **Finestra Proprietà**.  
  
3.  Nella finestra **Proprietà** impostare le proprietà del descrittore di tipo.  
  
     Le procedure seguenti descrivono come definire un descrittore di tipo come un campo, un'entità o una raccolta di entità.  
  
### Per definire un campo  
  
1.  Nella finestra **Proprietà**, impostare la proprietà **Nome** del descrittore del tipo con il nome di un campo nel tipo che rappresenta l'entità \(ad esempio: FirstName\).  
  
2.  Nell'elenco accanto alla proprietà **TypeName**, scegliere il tipo di dati appropriato \(ad esempio, **Int32**\).  
  
     Per informazioni sugli altri parametri facoltativi, vedere [TypeDescriptor](http://msdn.microsoft.com/library/ms543392%28v=office.12%29.aspx).  
  
### Per definire un'entità  
  
1.  Nella finestra **Proprietà** impostare la proprietà **Nome** su un nome che descriva l'entità \(ad esempio: Contact\).  
  
2.  Impostare la proprietà **TypeName** sul nome completo del tipo che rappresenta l'entità.  Questo tipo può essere una classe nel progetto, un tipo definito in un assembly cui viene fatto riferimento nella soluzione o un tipo definito nel modello a oggetti di integrazione applicativa dei dati.  
  
    -   Per una classe nel progetto, scegliere la freccia giù accanto alla proprietà **TypeName**, scegliere la scheda **Progetto corrente** della finestra di dialogo visualizzata e quindi scegliere la classe nel progetto.  
  
         Il nome completo include lo spazio dei nomi e il nome della classe seguiti dal nome del sistema LOB.  Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su una classe nel progetto.  
  
         `MyBDCNamespace.BdcModel1.Contact, BdcModel1`  
  
    -   Per un tipo che si trova in un assembly della soluzione, il nome completo include il nome del tipo, il nome dell'assembly, il numero di versione, le impostazioni cultura e il token di chiave pubblica.  
  
         Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su un tipo definito in un assembly cui si fa riferimento nella soluzione.  
  
         `MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
    -   Per un tipo definito nel modello a oggetti di integrazione applicativa dei dati, il nome completo include lo spazio dei nomi e il nome del tipo.  
  
         Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su un tipo nel modello a oggetti di integrazione applicativa dei dati.  
  
         `Microsoft.BusinessData.Runtime.DynamicType`  
  
3.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati** aprire l'elenco visualizzato per il descrittore di tipo, quindi scegliere **Modifica**.  
  
     Verrà aperta la finestra **Esplora integrazione applicativa dei dati**.  
  
4.  In **Esplora integrazione applicativa dei dati** aprire il menu di scelta rapida del descrittore del tipo, quindi scegliere **Aggiungi descrittore tipo**.  
  
     Un nuovo descrittore di tipo viene aggiunto come elemento figlio per il descrittore del tipo di entità.  Configurare il descrittore di tipo come un campo.  
  
5.  Ripetere il passaggio 4 per aggiungere un descrittore di tipo figlio per ogni campo dell'entità.  
  
### Per definire una raccolta di entità  
  
1.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati**, scegliere il descrittore di tipo del parametro desiderato.  
  
2.  Nella barra dei menu scegliere **Visualizza**, **Finestra Proprietà**.  
  
3.  Nella finestra **Proprietà** impostare la proprietà **Nome** su un nome che descriva l'entità \(ad esempio: Contacts\).  
  
4.  Impostare la proprietà **IsCollection** su **True**.  Ciò indica che il descrittore di tipo è una raccolta di entità.  
  
5.  Impostare la proprietà **TypeName** su una stringa che contiene un riferimento all'interfaccia di <xref:System.Collections.Generic.IEnumerable%601> e sul nome completo del tipo che rappresenta l'entità.  Questo tipo può essere una classe nel progetto, un tipo definito in un assembly cui viene fatto riferimento nella soluzione o un tipo definito nel modello a oggetti di integrazione applicativa dei dati.  
  
    -   Per una classe nel progetto, scegliere la freccia giù accanto alla proprietà **TypeName**, scegliere la scheda **Progetto corrente** della finestra di dialogo visualizzata e quindi scegliere la classe nel progetto.  
  
         Il nome completo include lo spazio dei nomi e il nome della classe seguiti dal nome del sistema LOB.  
  
         Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su una raccolta di classi nel progetto.  
  
         `System.Collections.Generic.IEnumerable`1 [MyBDCNamespace.` `BdcModel1.Contact, BdcModel1]`  
  
    -   Per un tipo che si trova in un assembly della soluzione, il nome completo include il nome del tipo, il nome dell'assembly, il numero di versione, le impostazioni cultura e il token di chiave pubblica.  
  
         Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su una raccolta di tipo in un assembly cui si fa riferimento nella soluzione.  
  
         `System.Collections.Generic.IEnumerable`1 [MyNamespace.Contact, myAssemblyName, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089]`  
  
    -   Per un tipo definito nel modello a oggetti di integrazione applicativa dei dati, il nome completo include solo lo spazio dei nomi e il nome del tipo.  
  
         Nell'esempio seguente il valore della proprietà **TypeName** viene impostato su una raccolta di tipi definita nel modello a oggetti di integrazione applicativa dei dati.  
  
         `System.Collections.Generic.IEnumerable`1 [Microsoft.BusinessData.Runtime.DynamicType]`  
  
6.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati** aprire l'elenco visualizzato per il descrittore di tipo, quindi scegliere **Modifica**.  
  
     Verrà aperta la finestra **Esplora integrazione applicativa dei dati**.  
  
7.  In **Esplora integrazione applicativa dei dati** aprire il menu di scelta rapida del descrittore del tipo, quindi scegliere **Aggiungi descrittore tipo**.  
  
     Un nuovo descrittore di tipo viene aggiunto come elemento figlio per il descrittore del tipo di raccolta.  Configurare il descrittore di tipo come un'entità.  
  
## Vedere anche  
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  