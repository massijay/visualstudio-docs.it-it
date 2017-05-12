---
title: "Procedura: creare un ricevitore di eventi per un&#39;istanza di elenco specifica"
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
helpviewer_keywords: 
  - "ricevitori di eventi [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, ricevitori di eventi"
ms.assetid: 4b4b3564-161a-4327-8963-50896c084ac2
caps.latest.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedura: creare un ricevitore di eventi per un&#39;istanza di elenco specifica
  Agli eventi che si verificano in qualsiasi istanza di una definizione di elenco viene risposto tramite un ricevitore di eventi dell'istanza di elenco.  Anche se tramite il modello del ricevitore di eventi non viene abilitata la destinazione di un'istanza di elenco specifica, è possibile modificare l'ambito di un ricevitore di eventi in una definizione di elenco affinché possa rispondere agli eventi in un'istanza di elenco specifica.  
  
 Per definire come destinazione un'istanza di elenco specifica, nel file Elements.xml per il ricevitore di eventi sostituire `ListTemplateId` con `ListUrl` e aggiungere l'URL dell'istanza di elenco.  
  
## Creazione di un ricevitore di eventi dell'istanza di elenco  
 Nei passaggi seguenti viene mostrato come modificare un ricevitore di eventi dell'elemento dell'elenco per rispondere solo a eventi che si verificano in un'istanza di elenco degli annunci personalizzato.  
  
#### Per modificare un ricevitore di eventi in modo che risponda a un'istanza di elenco specifica  
  
1.  Aprire il sito di SharePoint in un browser.  
  
2.  Nel riquadro di navigazione, collegamento **Elenchi**.  
  
3.  Nella pagina **Tutti i contenuti del sito**, scegliere il collegamento **Crea**.  
  
4.  Nella finestra di dialogo **Crea** scegliere il tipo **Annunci**, denominare l'annuncio TestAnnouncements, quindi scegliere **Crea**.  
  
5.  In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] creare un progetto Ricevitore di eventi.  
  
6.  Nell'elenco **Selezionare il tipo di ricevitore di eventi desiderato** selezionare **Eventi elementi elenco**.  
  
    > [!NOTE]  
    >  È possibile selezionare anche qualsiasi altro tipo di ricevitore di eventi il cui ambito è definito in una definizione di elenco, ad esempio, **Eventi di posta elettronica elenco** o **Eventi di flusso di lavoro elenco**.  
  
7.  Nell'elenco di **Selezionare l'elemento da utilizzare come origine eventi**, scegliere **Annunci**.  
  
8.  Nell'elenco **Gestisci gli eventi successivi**, selezionare la casella di controllo **Sta per essere aggiunto un elemento** quindi scegliere il pulsante **Fine**.  
  
9. In **Esplora soluzioni**, sotto EventReceiver1 aprire Elements.xml.  
  
     Il ricevitore di eventi fa riferimento attualmente alla definizione di elenco degli annunci tramite la riga seguente:  
  
    ```  
    <Receivers ListTemplateId="104">  
    ```  
  
     Modificare questa riga nel testo seguente:  
  
    ```  
    <Receivers ListUrl="Lists/TestAnnouncements">  
    ```  
  
     In questo modo solo gli eventi generati nel nuovo elenco degli annunci **TestAnnouncements** appena creato vengono risposti dal ricevitore di eventi.  È possibile modificare l'attributo `ListURL` per fare riferimento a qualsiasi istanza di elenco sul server SharePoint.  
  
10. Aprire il file di codice per il ricevitore di eventi e inserire un punto di interruzione nel metodo ItemAdding.  
  
11. Premere il tasto F5 per compilare ed eseguire la soluzione.  
  
12. Nel riquadro di navigazione di SharePoint scegliere il link **TestAnnouncements**.  
  
13. Scegliere il collegamento **Aggiungi nuovo annuncio**.  
  
14. Immettere un titolo per l'annuncio e quindi scegliere il pulsante di **Salva**.  
  
     Si noti che il punto di interruzione viene rilevato quando il nuovo elemento viene aggiunto all'elenco degli annunci personalizzato.  
  
15. Scegliere il tasto F5 per continuare.  
  
16. Nel riquadro di navigazione, scegliere il collegamento **Elenchi** quindi scegliere il collegamento **Annunci**.  
  
17. Aggiungere un nuovo annuncio.  
  
     Si noti che il ricevitore di eventi non viene attivato sul nuovo annuncio perché il ricevitore è configurato per rispondere solo agli eventi nell'istanza di elenco degli annunci personalizzato, **TestAnnouncements**.  
  
## Vedere anche  
 [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  