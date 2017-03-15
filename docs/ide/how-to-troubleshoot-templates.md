---
title: "Procedura: risolvere i problemi relativi ai modelli | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli di Visual Studio, risoluzione dei problemi"
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# Procedura: risolvere i problemi relativi ai modelli
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se nell'ambiente di sviluppo il caricamento di un modello non ha esito positivo, esistono vari modi per individuare il problema.  
  
## Convalida del file .vstemplate  
 Se il file .vstemplate di un modello non corrisponde allo schema dei modelli di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], il modello potrebbe non essere visualizzato nella finestra di dialogo **Nuovo progetto**.  
  
#### Per convalidare il file .vstemplate  
  
1.  Individuare il file .zip che contiene il modello.  
  
2.  Estrarre il file con estensione zip.  
  
3.  Nel menu **File** di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], scegliere **Apri**, quindi scegliere **File**.  
  
4.  Selezionare il file .vstemplate relativo al modello e fare clic su **Apri**.  
  
5.  Controllare che il codice XML del file .vstemplate sia conforme allo schema dei modelli di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni sullo schema dei modelli per .vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
    > [!NOTE]
    >  Per il supporto IntelliSense durante la creazione del file .vstemplate, aggiungere un attributo `xmlns` all'elemento `VSTemplate` e assegnargli il valore http:\/\/schemas.microsoft.com\/developer\/vstemplate\/2005.  
  
6.  Salvare e chiudere il file .vstemplate.  
  
7.  Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse, scegliere **Invia a**, quindi fare clic su **Cartella compressa**.  I file selezionati verranno compressi in un file .zip.  
  
8.  Inserire il nuovo file .zip nella stessa directory del vecchio file .zip.  
  
9. Eliminare i file di modello estratti e il vecchio file di modello .zip.  
  
## Monitoraggio del log eventi  
 Gli errori rilevati durante l'elaborazione dei file di modello .zip vengono registrati in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Se un modello non viene visualizzato nella finestra di dialogo **Nuovo progetto** come previsto, è possibile utilizzare il **Visualizzatore eventi** per risolvere il problema.  
  
#### Per individuare gli errori del modello nel Visualizzatore eventi  
  
1.  In Windows fare clic su **Start**, selezionare **Pannello di controllo**, fare doppio clic su **Strumenti di amministrazione**, quindi doppio clic su **Visualizzatore eventi**.  
  
2.  Nel riquadro di sinistra fare clic su **Applicazione**.  
  
3.  Cercare gli eventi con un valore **Origine** di `Visual Studio - VsTemplate`.  
  
4.  Fare doppio clic su un evento del modello per visualizzare l'errore.  
  
## Vedere anche  
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)