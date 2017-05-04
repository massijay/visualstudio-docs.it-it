---
title: "Procedura: personalizzare un pacchetto della soluzione SharePoint tramite le destinazioni di MSBuild | Microsoft Docs"
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
  - "sviluppo per SharePoint in Visual Studio, pacchetti"
ms.assetid: 7fa6a276-04c8-463e-be95-57c2c6240d76
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: personalizzare un pacchetto della soluzione SharePoint tramite le destinazioni di MSBuild
  È possibile personalizzare la modalità di creazione dei file di pacchetto \(con estensione wsp\) di Visual Studio tramite le destinazioni di MSBuild del prompt di comandi.  Ad esempio è possibile personalizzare le proprietà di MSBuild che cambiano la directory intermedia di assemblaggio e i gruppi di elementi di MSBuild che specificano i file enumerati.  
  
## Personalizzazione ed esecuzione delle destinazioni di MSBuild  
 Se si personalizzano le destinazioni BeforeLayout e AfterLayout, è possibile eseguire le attività prima del layout del pacchetto, ad esempio aggiungendo, rimuovendo, o modificando i file che verranno compressi.  
  
#### Per personalizzare la destinazione BeforeLayout  
  
1.  Aprire un editor, ad esempio Blocco Note e aggiungere il seguente codice.  
  
    ```  
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
      <Target Name="BeforeLayout">  
        <Message Importance="high" Text="In the BeforeLayout Target"></Message>  
      </Target>  
    </Project>  
    ```  
  
     In questo esempio viene visualizzato un messaggio prima della compressione di questa destinazione.  
  
2.  Denominare il file **CustomLayout.SharePoint.targets**quindi salvarlo nella cartella del progetto SharePoint.  
  
3.  Aprire il progetto, aprire il menu di scelta rapida e quindi scegliere **Scarica progetto**.  
  
4.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e scegliere **Modifica** *ProjectName***.vbproj** o **Modifica** *ProjectName***.csproj**.  
  
5.  Dopo la riga di `Import` verso la fine del file di progetto, aggiungere la seguente riga.  
  
    ```  
    <Import Project="CustomLayout.SharePoint.targets" />  
    ```  
  
6.  Salvare e chiudere il file di progetto.  
  
7.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto e scegliere **Ricarica progetto**.  
  
 Quando si pubblica il progetto, il messaggio viene visualizzato nell'output prima di iniziare la compressione degli elementi.  
  
#### Per personalizzare la destinazione AfterLayout  
  
1.  Sulla barra dei menu selezionare **File**, **Apri**, **File**.  
  
2.  Nella finestra di dialogo **Apri file**, passare alla cartella del progetto, selezionare il file CustomLayout.target quindi scegliere il pulsante **Apri**.  
  
3.  Prima dell'istruzione `</Project>` aggiungere il seguente codice:  
  
    ```  
    <Target Name="AfterLayout">  
      <Message Importance="high" Text="In the AfterLayout Target"></Message>  
    </Target>  
    ```  
  
     In questo esempio viene visualizzato un messaggio dopo che questa destinazione è stata compressa.  
  
4.  Salvare e chiudere il file di destinazione.  
  
5.  Riavviare Visual Studio e aprire il progetto.  
  
 Quando si pubblica il progetto, il messaggio BeforeLayout appare prima dell'inizio della creazione del pacchetto, e il messaggio AfterLayout appare dopo che la compressione è finita.  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  