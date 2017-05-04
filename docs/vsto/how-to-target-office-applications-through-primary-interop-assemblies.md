---
title: "Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilit&#224; primari | Microsoft Docs"
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
  - "sviluppo di applicazioni [sviluppo per Office in Visual Studio], automazione"
  - "assembly [sviluppo per Office in Visual Studio], riferimenti agli assembly di interoperabilità primari"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], automazione"
  - "Office (assembly di interoperabilità primari in Visual Studio), aggiunta di riferimenti"
  - "assembly di interoperabilità primari [sviluppo per Office in Visual Studio], aggiunta di riferimenti"
ms.assetid: 9bedae85-32b6-4df6-82b2-9d124fb49636
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilit&#224; primari
  Quando si crea un nuovo progetto di Office, in Visual Studio vengono aggiunti automaticamente riferimenti agli assembly di interoperabilità primari \(PIA\) di Microsoft Office necessari per la compilazione del progetto.  È necessario aggiungere riferimenti agli altri assembly di interoperabilità primari \(PIA\) negli scenari seguenti:  
  
-   Si vuole usare funzionalità di altre applicazioni di Microsoft Office nel progetto,  ad esempio, funzionalità di Microsoft Office Excel in un progetto per Microsoft Office Word.  
  
-   Si vuole automatizzare applicazioni di Microsoft Office prive di progetti dedicati in Visual Studio, ad esempio Microsoft Office Access.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### Per aggiungere un riferimento a un assembly di interoperabilità primario  
  
1.  Aprire il progetto di Office e selezionarne il nome in **Esplora soluzioni**.  
  
2.  Nel menu **Progetto** fare clic su **Aggiungi riferimento**.  
  
3.  Nella scheda **Framework** selezionare l'assembly di interoperabilità primario \(PIA\) desiderato nell'elenco **Nome componente**.  Per altre informazioni sugli assembly di interoperabilità primari di Microsoft Office disponibili, vedere [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
     Se il progetto è destinato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versione successiva, la proprietà **Incorpora tipi di interoperabilità** per il riferimento dell'assembly viene impostata su **True** per impostazione predefinita.  Usando questa impostazione, la soluzione non richiede l'assembly di interoperabilità primario \(PIA\) sui computer degli utenti finali.  Per altre informazioni, vedere [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md).  
  
    > [!NOTE]  
    >  Nei progetti di Office, aggiungere sempre riferimenti agli assembly di interoperabilità primari \(PIA\) di Office mediante la scheda **.NET** della finestra di dialogo **Aggiungi riferimento** invece che mediante la scheda **COM**.  Per altre informazioni, vedere [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md).  
  
4.  Fare clic su **OK**.  
  
     Il nome dell'assembly viene visualizzato nella cartella **Riferimenti** in **Esplora soluzioni**.  
  
## Vedere anche  
 [Assembly di interoperabilità primari di Office](../vsto/office-primary-interop-assemblies.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Sviluppo di soluzioni Office](../vsto/developing-office-solutions.md)   
 [Procedura: installare assembly di interoperabilità primari di Office](../vsto/how-to-install-office-primary-interop-assemblies.md)  
  
  