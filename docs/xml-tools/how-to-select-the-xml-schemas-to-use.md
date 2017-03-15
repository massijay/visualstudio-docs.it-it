---
title: "Procedura: selezionare gli schemi XML da utilizzare | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Procedura: selezionare gli schemi XML da utilizzare
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML fornisce una cache degli schemi situata nella directory %InstallDir%\\Xml\\Schemas.La cache degli schemi include schemi XML noti che vengono utilizzati per IntelliSense e per la convalida di documenti XML.  
  
 La proprietà **Schemas** del documento viene utilizzata per scegliere uno o più schemi XSD \(XML Schema Definition Language\) da utilizzare per la convalida.Consente di selezionare gli schemi dalla cache degli schemi o di specificare uno schema che non si trova nella cache.  
  
 Gli schemi specificati vengono salvati nel file nascosto SUO \(Solution User Options\) insieme a tutte le altre proprietà del documento XML.Di conseguenza non sarà necessario immettere nuovamente tali valori alla successiva apertura della soluzione.  
  
> [!NOTE]
>  L'editor può eseguire la convalida mediante uno schema inline o uno schema a cui fa riferimento l'attributo `xsd:schemaLocation`.Per ulteriori informazioni, vedere [Convalida di documenti XML](../xml-tools/xml-document-validation.md).  
  
### Per selezionare uno schema XML dalla cache degli schemi  
  
1.  Aprire un file nell'editor XML.  
  
2.  Fare clic sul pulsante nel campo **Schemi** della finestra delle proprietà del documento.  
  
     Viene visualizzata la finestra di dialogo **Schemi XML**.Nella finestra di dialogo sono elencati tutti gli schemi con estensione .xsd contenuti nella cache degli schemi \(inclusi gli schemi a cui viene fatto riferimento nel file catalog.xml\) nonché gli schemi che si trovano nella soluzione corrente, aperti in Visual Studio, a cui fa riferimento l'attributo `xsd:schemaLocation` o la proprietà **Schemas**.  
  
3.  Selezionare gli schemi da utilizzare per la convalida eseguendo una delle seguenti operazioni:  
  
    -   Selezionare uno schema elencato nella finestra di dialogo **Schemi XML**, fare clic sulla colonna **Utilizza**, quindi selezionare **Utilizza questo schema**.  
  
     In alternativa  
  
    -   Selezionare più schemi elencati nella finestra di dialogo **Schemi XML**, fare clic con il pulsante destro del mouse e selezionare **Utilizza questo schema**.  
  
4.  Fare clic su **OK**.  
  
     L'elenco degli schemi selezionati viene copiato nella proprietà **Schemas** del documento.  
  
### Per aggiungere uno schema XML alla cache degli schemi  
  
1.  Fare clic sul pulsante nel campo **Schemi** della finestra delle proprietà del documento.  
  
2.  Fare clic su **Aggiungi**.  
  
     Viene visualizzata la finestra di dialogo **Apri schema XSD**.  
  
3.  Individuare e selezionare gli schemi da aggiungere alla cache degli schemi.  
  
4.  Scegliere **Apri**.  
  
     Gli schemi vengono aggiunti alla cache degli schemi e il valore della colonna **Utilizza** viene impostato su **Utilizza questo schema**.  
  
### Per eliminare uno schema XML dalla cache degli schemi  
  
1.  Fare clic sul pulsante nel campo **Schemi** della finestra delle proprietà del documento.  
  
2.  Selezionare lo schema da rimuovere e fare clic su **Rimuovi**.  
  
     Lo schema viene rimosso dalla cache degli schemi in memoria, ma non dal file system.  
  
    > [!NOTE]
    >  Se è ancora presente un riferimento allo schema mediante un attributo `schemaLocation` o un `targetNamespace` corrispondente, l'opzione **Rimuovi** non può essere utilizzata a causa dell'associazione automatica.In questo caso si consiglia di selezionare **Non utilizzare gli schemi selezionati** nella colonna **Utilizza**.  
  
## Vedere anche  
 [Cache degli schemi](../xml-tools/schema-cache.md)   
 [Finestra di dialogo Schemi XML](../xml-tools/xml-schemas-dialog-box.md)   
 [Editor XML](../xml-tools/xml-editor.md)