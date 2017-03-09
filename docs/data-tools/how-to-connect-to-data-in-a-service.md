---
title: "Procedura: connettersi ai dati di un servizio | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], connessione a servizi Web"
  - "dati [Visual Studio], lettura da servizi Web"
  - "origini dati, creazione da servizi Web"
  - "lettura di dati, dai servizi Web"
  - "servizi Web, come origini dati"
  - "servizi Web, connessione"
  - "servizi Web, lettura di dati"
ms.assetid: a6b54353-05fe-4e5c-8631-90231fc95504
caps.latest.revision: 32
caps.handback.revision: 30
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: connettersi ai dati di un servizio
Per connettere l'applicazione ai dati restituiti da un servizio, eseguire la [Configurazione guidata origine dati](../data-tools/media/data-source-configuration-wizard.png) e selezionare **Servizio** nella pagina **Seleziona un tipo di origine dati**.  
  
 Dopo aver completato la procedura guidata, al progetto viene aggiunto un riferimento al servizio che diventa immediatamente disponibile nella [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md).  
  
> [!NOTE]
>  Gli elementi visualizzati nella finestra **Origini dati** dipendono dalle informazioni restituite dal servizio.  Alcuni servizi potrebbero non fornire informazioni sufficienti per consentire alla **Configurazione guidata origine dati** di creare oggetti associabili.  Se ad esempio il servizio restituisce un dataset non tipizzato, al termine dell'esecuzione della procedura guidata nella **finestra Origini dati** non verrà visualizzato alcun elemento.  I dataset non tipizzati, infatti, non forniscono alcuno schema, di conseguenza la procedura guidata non dispone di informazioni sufficienti per creare l'origine dati.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Per connettere l'applicazione a un servizio  
  
1.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
2.  Selezionare **Servizio** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
3.  Immettere l'indirizzo del servizio che si desidera utilizzare oppure fare clic su **Individua** per individuare i servizi nella soluzione corrente, quindi fare clic su **Vai**.  
  
4.  Facoltativamente, è possibile digitare un nuovo **Spazio dei nomi** in sostituzione del valore predefinito.  
  
    > [!NOTE]
    >  Fare clic su **Avanzate** per aprire la [Finestra di dialogo Configura riferimento a servizio](../data-tools/configure-service-reference-dialog-box.md).  
  
5.  Scegliere **OK** per aggiungere un riferimento al servizio al progetto.  
  
6.  Fare clic su **Fine**.  
  
     L'origine dati verrà aggiunta alla finestra **Origini dati**.  
  
## Passaggi successivi  
  
#### Per aggiungere funzionalità all'applicazione  
  
-   Selezionare un elemento nella finestra **Origini dati** e trascinarlo in un form per creare controlli associati.  Per ulteriori informazioni, vedere [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
## Vedere anche  
 [Procedura dettagliata: associazione di controlli WPF a un servizio dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)   
 [Procedura dettagliata: associazione di controlli Silverlight a un servizio dati WCF](../Topic/Walkthrough:%20Binding%20Silverlight%20Controls%20to%20a%20WCF%20Data%20Service.md)   
 [Windows Communication Foundation Services and WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)