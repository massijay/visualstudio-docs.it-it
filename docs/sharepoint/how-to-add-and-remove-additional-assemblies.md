---
title: "Procedura: Aggiungere e rimuovere assembly aggiuntivi"
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
  - "VS.SharePointTools.RAD.CustomAssembly"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, pacchetti"
ms.assetid: d9d1e8db-9df2-4e07-ac8d-59ef05d24090
caps.latest.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 21
---
# Procedura: Aggiungere e rimuovere assembly aggiuntivi
  Se un pacchetto di SharePoint dipende da altri assembly per la funzionalità o i dati, è possibile aggiungere tali assembly al pacchetto della soluzione \(con estensione wsp\).  Tramite il server SharePoint verrà quindi verificato che gli assembly personalizzati vengano installati con un pacchetto.  
  
 È inoltre possibile aggiungere e modificare i controlli sicuri e i file di risorse di classe associati agli assembly.  
  
## Aggiunta di altri assembly, controlli sicuri e risorse di classe  
 È possibile aggiungere ulteriori assembly nel pacchetto della soluzione SharePoint.  In una soluzione creata mediante sandbox gli assembly aggiuntivi vengono distribuiti nella Global Assembly Cache, mentre gli elementi del progetto SharePoint vengono aggiunti al database del contenuto.  È inoltre possibile aggiungere controlli sicuri e risorse di classe a questi assembly aggiuntivi.  Per ulteriori informazioni sui controlli sicuri, vedere [Specifica delle informazioni sui pacchetti e sulla distribuzione negli elementi di progetto](../sharepoint/providing-packaging-and-deployment-information-in-project-items.md) o "creare una voce SafeControl" in [Distribuire le Web part in SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=245505).  
  
#### Per aggiungere un assembly esistente  
  
1.  Aprire **Progettazione pacchetti**.  Per ulteriori informazioni, vedere [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere la scheda **Avanzate**.  
  
3.  Scegliere il pulsante **Aggiungi**, quindi scegliere dall'elenco **Aggiungi assembly esistente**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi assembly esistente**.  
  
4.  Fare clic sui puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](~/docs/sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")\) e selezionare l'assembly da aggiungere.  È consigliabile utilizzare un percorso relativo dell'assembly selezionato per motivi di portabilità.  
  
5.  Per **Destinazione Distribuzione** fare clic sul pulsante di opzione **GlobalAssemblyCache** per distribuire l'assembly in Global Assembly Cache o scegliere il pulsante di opzione **WebApplication** per distribuire l'assembly nella cartella WebApplication sul server su cui è avviato SharePoint.  
  
#### Per aggiungere un assembly dall'output del progetto  
  
1.  Aprire **Progettazione pacchetti**.  
  
     Per ulteriori informazioni, vedere [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere la scheda **Avanzate**.  
  
3.  Scegliere il pulsante **Aggiungi**, quindi scegliere dall'elenco **Aggiungi Assembly da Output del Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi assembly da output del progetto**.  
  
4.  Nell'elenco **Progetto di origine** e scegliere il progetto di origine da aggiungere.  
  
5.  Per **Destinazione distribuzione** fare clic sul pulsante di opzione **GlobalAssemblyCache** per distribuire l'assembly in Global Assembly Cache o scegliere il pulsante di opzione **WebApplication** per distribuire l'assembly nella cartella WebApplication sul server su cui è avviato SharePoint.  
  
#### Per aggiungere un controllo sicuro  
  
1.  Aprire la finestra di dialogo **Modifica assembly esistente**.  A tal fine, aprire la finestra di progettazione del pacchetto, fare clic sulla scheda **Avanzate**, selezionare un assembly, quindi fare clic sul pulsante **Modifica**.  
  
2.  Nel riquadro **Controlli sicuri** fare clic sul pulsante **Fare clic qui per aggiungere un nuovo elemento**.  
  
3.  Nella colonna **Nome assembly** inserire il nome dell'assembly.  
  
4.  Nella colonna **Spazio dei nomi** inserire il nome dello spazio dei nomi per il controllo sicuro.  
  
5.  Nella colonna **Nome tipo** inserire il nome del tipo.  
  
#### Per aggiungere una risorsa di classe  
  
1.  Aprire la finestra di dialogo **Modifica assembly esistente**.  A tal fine, aprire la finestra di progettazione del pacchetto, fare clic sulla scheda **Avanzate**, selezionare un assembly, quindi fare clic sul pulsante **Modifica**.  
  
2.  Dal riquadro **Risorse classe** scegliere il pulsante **Fare clic qui per aggiungere un nuovo elemento**.  
  
3.  Nella colonna **Nome file** fare clic sui puntini di sospensione \(![Ellisse di ASP.NET Mobile Designer](~/docs/sharepoint/media/mwellipsis.gif "Ellisse di ASP.NET Mobile Designer")\) e selezionare la risorsa di classe da aggiungere.  
  
## Eliminazione di assembly personalizzati  
 È possibile eliminare gli assembly da un pacchetto di SharePoint o i controlli sicuri e le risorse di classe dagli assembly esistenti.  
  
#### Per eliminare un assembly esistente  
  
1.  Aprire **Progettazione pacchetti**.  Per ulteriori informazioni, vedere [Procedura: personalizzare un pacchetto della soluzione SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
2.  Scegliere la scheda **Avanzate**.  
  
3.  Nel riquadro **Assembly aggiuntivi** fare clic sull'assembly personalizzato da eliminare.  
  
4.  Fare clic sul pulsante **Elimina**.  
  
#### Per eliminare un controllo sicuro per un assembly  
  
1.  Aprire la finestra di dialogo **Modifica assembly esistente**.  A tal fine, aprire la finestra di progettazione del pacchetto, fare clic sulla scheda **Avanzate**, selezionare un assembly, quindi fare clic sul pulsante **Modifica**.  
  
2.  Scegliere il controllo sicuro che si desidera eliminare.  
  
3.  Premere il tasto CANC.  
  
#### Per eliminare una risorsa di classe per un assembly  
  
1.  Aprire la finestra di dialogo **Modifica assembly esistente**.  A tal fine, aprire la finestra di progettazione del pacchetto, fare clic sulla scheda **Avanzate**, selezionare un assembly, quindi fare clic sul pulsante **Modifica**.  
  
2.  Scegliere la risorsa di classe che si desidera eliminare.  
  
3.  Premere il tasto CANC.  
  
## Vedere anche  
 [Creazione di funzionalità SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)   
 [NIB: Building SharePoint Solutions with Team Foundation Server](http://msdn.microsoft.com/it-it/700a570a-e98e-4425-aadd-34c014868d43)  
  
  