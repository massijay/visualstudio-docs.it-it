---
title: "How to: Add, Update, or Remove a WCF Data Service Reference | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "service references [Visual Studio]"
  - "WCF Data Service reference"
  - "WCF data service references"
  - "ADO.NET service references"
  - "ADO.NET Data Service reference"
ms.assetid: 892ebf37-3af4-472e-8744-92837677d611
caps.latest.revision: 11
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Add, Update, or Remove a WCF Data Service Reference
Un *riferimento al servizio* consente a un progetto di accedere a uno o più servizi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)].  Utilizzare la finestra di dialogo **Aggiungi riferimento al servizio** per ricercare servizi [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] nella soluzione corrente, localmente, in una rete LAN o in Internet.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Aggiunta di un riferimento a un servizio  
  
#### Per aggiungere un riferimento a un servizio esterno  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto a cui si desidera aggiungere il servizio, quindi scegliere **Aggiungi riferimento a servizio**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi riferimento a servizio**.  
  
2.  Nella casella **Indirizzo** immettere l’URL del servizio e quindi fare clic su **Vai** per cercare il servizio.  Se il servizio implementa la sicurezza del nome utente e della password, è possibile che vengano richiesti nome utente e password.  
  
    > [!NOTE]
    >  Fare riferimento solo ai servizi forniti da una fonte attendibile.  L'aggiunta di riferimenti da una fonte non attendibile può compromettere la sicurezza.  
  
     È anche possibile selezionare l'URL dall'elenco **Indirizzo** in cui sono archiviati i 15 URL precedenti in corrispondenza dei quali sono stati trovati metadati del servizio validi.  
  
     Durante la ricerca verrà visualizzato un indicatore di stato.  È possibile interrompere la ricerca in qualsiasi momento facendo clic su **Interrompi**.  
  
3.  Nell'elenco **Servizi**, espandere il nodo relativo al servizio che si desidera utilizzare e selezionare un set di entità.  
  
4.  Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si desidera utilizzare per il riferimento.  
  
5.  Scegliere **OK** per aggiungere il riferimento al progetto.  
  
     Verrà generato un client del servizio \(proxy\) e i metadati che descrivono il servizio verranno aggiunti al file app.config.  
  
#### Per aggiungere un riferimento a un servizio nella soluzione corrente  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nome del progetto a cui si desidera aggiungere il servizio, quindi scegliere **Aggiungi riferimento a servizio**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi riferimento a servizio**.  
  
2.  Fare clic su **Individua**.  
  
     Tutti i servizi \(sia [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] che WCF\) presenti nella soluzione corrente vengono aggiunti all'elenco **Servizi**.  
  
3.  Nell'elenco **Servizi**, espandere il nodo relativo al servizio che si desidera utilizzare e selezionare un set di entità.  
  
4.  Nella casella **Spazio dei nomi** immettere lo spazio dei nomi che si desidera utilizzare per il riferimento.  
  
5.  Scegliere **OK** per aggiungere il riferimento al progetto.  
  
     Verrà generato un client del servizio \(proxy\) e i metadati che descrivono il servizio verranno aggiunti al file app.config.  
  
## Aggiornamento di un riferimento al servizio  
 Il modello Entity Data Model per un servizio [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] può talvolta variare.  In tal caso, il riferimento al servizio deve essere aggiornato.  
  
#### Per aggiornare un riferimento al servizio  
  
-   In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul riferimento al servizio, quindi scegliere **Aggiorna riferimento a servizio**.  
  
     Durante l’aggiornamento del riferimento dal percorso originale verrà visualizzata una finestra di dialogo di stato e il client del servizio verrà rigenerato per riflettere le modifiche apportate nei metadati.  
  
## Rimozione di un riferimento a un servizio  
 Se un riferimento a un servizio non viene più utilizzato, è possibile rimuoverlo dalla soluzione.  
  
#### Per rimuovere un riferimento a un servizio  
  
-   In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul riferimento al servizio, quindi scegliere **Elimina**.  
  
     Il client del servizio verrà rimosso dalla soluzione e i metadati che descrivono il servizio verranno rimossi dal file app.config.  
  
    > [!NOTE]
    >  Qualsiasi codice al quale fa riferimento il servizio dovrà essere rimosso manualmente.  
  
## Vedere anche  
 [Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)