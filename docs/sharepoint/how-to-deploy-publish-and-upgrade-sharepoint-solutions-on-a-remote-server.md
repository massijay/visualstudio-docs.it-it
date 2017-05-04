---
title: "Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto | Microsoft Docs"
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
  - "distribuzione [sviluppo per SharePoint in Visual Studio]"
  - "distribuzione remota [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, distribuzione"
  - "sviluppo per SharePoint in Visual Studio, distribuzione remota"
ms.assetid: d9c67fae-d097-4e26-a2b9-0f72ff800987
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto
  Oltre alla distribuzione di soluzioni SharePoint nel sistema locale, è possibile pubblicare le soluzioni SharePoint in modalità sandbox per i siti remoti e per i siti locali SharePoint.  Il processo di pubblicazione remoto copia il file .wsp nel server SharePoint, installa la soluzione e quindi consente di attivare la soluzione.  È inoltre possibile aggiornare un'installazione remota di una soluzione SharePoint dopo aver apportato delle modifiche alla soluzione.  
  
## Per pubblicare una soluzione creata mediante sandbox di SharePoint in un server SharePoint remoto  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto sandbox di SharePoint che si vuole pubblicare, quindi scegliere **Pubblica**.  
  
2.  Nella finestra di dialogo **Pubblica**, scegliere il pulsante di opzione **Pubblica in sito SharePoint** quindi immettere un URL per un sito di pubblicazione online, come illustrato nel seguente esempio: https:\/\/mytestsite.sharepoint.microsoftonline.com.  
  
3.  Selezionare il pulsante di opzione **Apri la pagina raccolta di soluzioni nel browser dopo la pubblicazione** per visualizzare l'elenco delle soluzioni, dopo avere effettuato la pubblicazione, nella pagina **Raccolta soluzioni**.  
  
4.  Selezionare il pulsante **Pubblica**.  
  
5.  Accedere al server remoto se è necessaria l'autenticazione utente.  
  
     Lo stato di avanzamento della pubblicazione viene visualizzato nella finestra di Visual Studio **Output**.  Al termine del processo, il file di soluzione \(.wsp\) viene installato nel server SharePoint remoto.  Tuttavia, deve comunque essere attivato prima che possa essere utilizzato in SharePoint.  
  
6.  Nella pagina **Raccolta soluzioni**, selezionare l'applicazione di SharePoint e quindi sulla barra multifunzione, selezionare il pulsante **Attiva**.  
  
7.  Nella finestra di dialogo **Attiva soluzione**, sulla barra multifunzione, scegliere nuovamente il pulsante **Attiva**.  
  
     La colonna **Stato** nella pagina **Raccolta soluzioni** indica che l'applicazione è attiva.  
  
## Per aggiornare una soluzione creata mediante sandbox di SharePoint in un server SharePoint remoto  
 Se una soluzione creata mediante sandbox di SharePoint è già pubblicata su un server remoto, il seguente processo consente di aggiornarla dopo avere apportato le modifiche all'applicazione in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
1.  Rinominare il pacchetto di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Per effettuare questa operazione, in **Esplora soluzioni** aprire il pacchetto.  Verrà visualizzato in **Esplora pacchetti**.  
  
2.  In **Esplora pacchetti**, nella casella **Nome**, modificare il nome del pacchetto con un nome univoco.  
  
3.  Salvare il progetto.  
  
4.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e scegliere **Pubblica**.  
  
5.  Nella finestra di dialogo **Pubblica**, scegliere il pulsante di opzione **Pubblica in sito SharePoint** quindi, inserire l'URL per il server remoto in cui la soluzione viene salvata se non definito.  
  
6.  Selezionare il pulsante di opzione **Apri la pagina raccolta di soluzioni nel browser dopo la pubblicazione** per visualizzare l'elenco delle soluzioni, dopo avere effettuato la pubblicazione, nella pagina **Raccolta soluzioni**.  
  
7.  Selezionare il pulsante **Pubblica**.  
  
8.  Accedere al server remoto se è necessaria l'autenticazione utente.  
  
     Se di recente si è effettuato un accesso al server remoto, l'autenticazione può non essere necessaria  
  
     Se esiste una versione precedente dell'applicazione con lo stesso nome sul server SharePoint, si verificherà un errore a causa di un pacchetto che con lo stesso nome già esiste nel server SharePoint.  È necessario rinominare il pacchetto con un nome univoco prima di effettuare la pubblicazione.  
  
9. Selezionare una nuova applicazione in SharePoint, quindi sulla barra multifunzione, scegliere il pulsante **Aggiorna**.  
  
10. Nella finestra di dialogo **Aggiorna soluzione**, sulla barra multifunzione, scegliere nuovamente il pulsante **Aggiorna**.  La colonna **Stato** nella pagina **Raccolta soluzioni** ora dovrebbe indicare che l'applicazione è attiva.  
  
     La versione precedente della soluzione viene disattivata, la nuova versione della soluzione viene aggiornata con i dati precedentemente gestiti dalla soluzione e la nuova soluzione è attivata in SharePoint.  
  
## Vedere anche  
 [Procedura: distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md)   
 [Creazione di pacchetti delle soluzioni SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto tramite Progettazione pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  