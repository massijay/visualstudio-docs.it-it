---
title: "Procedura: definire le informazioni di configurazione per una soluzione Office"
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
  - "file di configurazione [sviluppo per Office in Visual Studio]"
  - "soluzioni [sviluppo per Office in Visual Studio], file di configurazione"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Procedura: definire le informazioni di configurazione per una soluzione Office
  È possibile utilizzare i file di configurazione per configurare impostazioni specifiche delle soluzioni Office,  quali criteri di associazione di assembly, oggetti remoti, debug e impostazioni di traccia.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Per aggiungere un file di configurazione al progetto Office  
  
1.  Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.  
  
2.  Nel riquadro **Categorie**, fare clic su **Generale**.  
  
3.  Nel riquadro **Modelli**  selezionare **File di configurazione dell'applicazione**.  
  
4.  Nella casella **Nome** digitare lo stesso nome dell'assembly con l'estensione CONFIG.  Ad esempio, il file di configurazione per l'assembly di un progetto di Excerl denominato ExcelWorkbook1.dll verrebbe denominato ExcelWorkbook1.dll.config.  
  
5.  Scegliere **Aggiungi**.  
  
6.  Creare il file di configurazione in base allo schema del file di configurazione dell'applicazione.  Per ulteriori informazioni, vedere [Schema dei file di configurazione per .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38).  
  
 Non vi sono considerazioni particolari da tenere presente per l'utilizzo dei file di configurazione con i progetti Office.  
  
## Vedere anche  
 [Schema dei file di configurazione per .NET Framework](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  