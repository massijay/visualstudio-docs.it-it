---
title: "Procedura: creare un pacchetto della soluzione SharePoint tramite le attivit&#224; MSBuild"
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
ms.assetid: c3880bdd-f0a1-4d53-9a97-5767cb3f7b8e
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: creare un pacchetto della soluzione SharePoint tramite le attivit&#224; MSBuild
  Un pacchetto di SharePoint \(con estensione wsp\) può essere compilato, pulito e convalidato tramite le attività MSBuild della riga di comando di un computer di sviluppo.  Questi comandi possono essere utilizzati anche per automatizzare il processo di compilazione tramite Team Foundation Server su un computer di compilazione.  
  
## Compilazione di un pacchetto di SharePoint  
  
#### Per compilare un pacchetto di SharePoint  
  
1.  Dal menu Windows **Avvia**, scegliere **Tutti i programmi**, **Accessori**, **Prompt dei comandi**.  
  
2.  Passare alla directory nella quale si trova il progetto SharePoint.  
  
3.  Inserire il seguente comando per creare un pacchetto per il progetto.  Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```  
    msbuild /t:Package ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei comandi seguenti per creare un pacchetto di un progetto SharePoint denominato ListDefinition1.  
  
    ```  
    msbuild /t:Package ListDefinition1.vbproj  
    msbuild /t:Package ListDefinition1.csproj  
    ```  
  
## Pulizia di un pacchetto di SharePoint  
  
#### Per pulire un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory nella quale si trova il progetto SharePoint.  
  
3.  Inserire il seguente comando per eseguire la pulizia di un pacchetto per il progetto.  Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```  
    msbuild /t:CleanPackage ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei comandi seguenti per pulire un progetto SharePoint denominato ListDefinition1.  
  
    ```  
    msbuild /t:CleanPackage ListDefinition1.vbproj  
    msbuild /t:CleanPackage ListDefinition1.csproj  
    ```  
  
## Convalida di un pacchetto di SharePoint  
  
#### Per convalidare un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory nella quale si trova il progetto SharePoint.  
  
3.  Inserire il seguente comando per convalidare un pacchetto per il progetto.  Sostituire *ProjectFileName* con il nome del progetto.  
  
    ```  
    msbuild /t:ValidatePackage ProjectFileName  
    ```  
  
     Ad esempio, è possibile eseguire uno dei comandi seguenti per convalidare un progetto SharePoint denominato ListDefinition1.  
  
    ```  
    msbuild /t:ValidatePackage ListDefinition1.vbproj  
    msbuild /t:ValidatePackage ListDefinition1.csproj  
    ```  
  
## Impostazione delle proprietà in un pacchetto di SharePoint  
  
#### Per impostare una proprietà in un pacchetto di SharePoint  
  
1.  Aprire una finestra del prompt dei comandi.  
  
2.  Passare alla directory nella quale si trova il progetto SharePoint.  
  
3.  Inserire il seguente comando per impostare una proprietà in un pacchetto per il progetto.  Sostituire *PropertyName* con la proprietà che si desidera impostare.  
  
    ```  
    msbuild /property:PropertyName=Value  
    ```  
  
     Ad esempio è possibile eseguire il comando seguente per impostare il livello di avviso.  
  
    ```  
    msbuild /property:WarningLevel = 2  
    ```  
  
## Vedere anche  
 [Creazione di funzionalità SharePoint](../sharepoint/creating-sharepoint-features.md)   
 [Procedura: personalizzare una funzionalità SharePoint](../sharepoint/how-to-customize-a-sharepoint-feature.md)   
 [Procedura: aggiungere e rimuovere elementi alle funzionalità SharePoint](../sharepoint/how-to-add-and-remove-items-to-sharepoint-features.md)  
  
  