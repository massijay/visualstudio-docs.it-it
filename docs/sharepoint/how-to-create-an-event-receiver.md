---
title: "Procedura: creare un ricevitore di eventi"
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
  - "VS.SharePointTools.SPE.EventReceiver"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ricevitori di eventi [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, ricevitori di eventi"
ms.assetid: 6f90cb48-eb8f-43c2-a3f7-ed4ce81aedf2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura: creare un ricevitore di eventi
  Creando dei *ricevitori di eventi*, è possibile rispondere quando un utente interagisce con gli elementi di SharePoint come elenchi o voci di elenco.  Per esempio, quando un utente modifica il calendario o elimina un nome dall'elenco dei contatti, viene attivato il codice del ricevitore di eventi.  Seguendo questo argomento, si può imparare come aggiungere un ricevitore di eventi a un'istanza di elenco.  
  
 Per completare questa procedura, è necessario installare [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e supportare le versioni di windows e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  Poiché per questo esempio è necessario un progetto SharePoint, è necessario completare anche la procedura dell'argomento [Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
## Aggiunta di un ricevitore di eventi  
 Il progetto creato in [Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md) include le colonne personalizzate del sito, un elenco personalizzato e un tipo di contenuto.  Nella procedura riportata di seguito, questo progetto verrà ampliato aggiungendo un semplice gestore eventi \(un ricevitore di eventi\) a un'istanza di elenco per mostrare come gestire gli eventi che si verificano in elementi di SharePoint come elenchi.  
  
#### Per aggiungere un ricevitore di eventi all'istanza di elenco  
  
1.  Aprire il progetto creato in [Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md).  
  
2.  In **Esplora soluzioni**, scegliere il nodo di progetto SharePoint, denominato **Clinico**.  
  
3.  Sulla barra dei menu scegliere **Progetto**,  **Aggiungi nuovo elemento**.  
  
4.  Sotto **Visual C\#** o **Visual Basic**, espandere il nodo **SharePoint**, quindi scegliere l'elemento **2010**.  
  
5.  Nel riquadro **Modelli**, scegliere **Ricevitore di eventi**, denominarlo TestEventReceiver1 quindi scegliere il pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
6.  Nell'elenco **Selezionare il tipo di ricevitore di eventi desiderato** selezionare **Eventi elementi elenco**.  
  
7.  Nell'elenco **Selezionare l'elemento da utilizzare come origine eventi.**, scegliere **Pazienti \(Clinica\/Pazienti\)**.  
  
8.  Nell'elenco **Gestisci gli eventi successivi**, selezionare la casella di controllo accanto a **È stato aggiunto un elemento**quindi scegliere il pulsante **Fine**.  
  
     Il file di codice del nuovo ricevitore di eventi contiene un solo metodo denominato `ItemAdded`.  Nel prossimo passaggio, verrà aggiunto codice al metodo in modo che ogni contatto sia denominato Scott Brown per impostazione predefinita.  
  
9. Sostituire il metodo esistente `ItemAdded` con il codice seguente, e premere F5:  
  
     [!code-csharp[SP_EventReceiver#1](../snippets/csharp/VS_Snippets_OfficeSP/sp_eventreceiver/CS/CustomField1/TestEventReceiver1/TestEventReceiver1.cs#1)]
     [!code-vb[SP_EventReceiver#1](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_eventreceiver/VB/CustomField1_VB/EventReceiver1/EventReceiver1.vb#1)]  
  
     Il codice viene eseguito e appare il sito di SharePoint nel browser.  
  
10. Nella barra Avvio Veloce, scegliere il collegamento **Pazienti** quindi scegliere il collegamento **Aggiungi nuovo elemento**.  
  
     Il form per l'immissione di nuovi elementi viene aperto.  
  
11. Immettere i dati nei campi e quindi scegliere il pulsante **Salva**.  
  
     Dopo avere scelto il pulsante di **Salva**, la colonna **Nome paziente** viene aggiornata automaticamente al nome Scott Brown.  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  