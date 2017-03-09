---
title: "Procedura: associare controlli alle immagini di un database | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "associazione dati [Windows Form], immagini"
  - "Origini dati (finestra), impostazione di controlli per la visualizzazione di immagini"
  - "immagini [Visual Basic], associazione dati"
  - "immagini [Visual Basic], visualizzazione su Windows Form"
  - "immagini [Visual Basic], trascinamento dalla finestra Origini dati"
  - "PictureBox (controllo) [Windows Form], associazione dati"
  - "immagini, associazione dati"
  - "immagini, trascinamento dalla finestra Origini dati"
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
caps.latest.revision: 15
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: associare controlli alle immagini di un database
È possibile utilizzare la finestra **Origini dati** per associare un'immagine in un database a un controllo nell'applicazione.  È ad esempio possibile associare un'immagine a un controllo <xref:System.Windows.Controls.Image> in un'applicazione WPF o a un controllo <xref:System.Windows.Forms.PictureBox> in un'applicazione Windows Form.  
  
 Le immagini di un database vengono generalmente archiviate come matrici di byte.  I tipi di controllo degli elementi della finestra **Origini dati** archiviati come matrici di byte sono impostati su **Nessuno** per impostazione predefinita, in quanto le matrici di byte possono contenere qualsiasi tipo di elemento, da una matrice di byte semplice al file eseguibile di un'applicazione di grandi dimensioni.  Per creare un controllo associato a dati per un elemento della matrice di byte nella finestra **Origini dati** che rappresenta un'immagine, è necessario selezionare il controllo da creare.  
  
 Nella procedura riportata di seguito si suppone che la finestra **Origini dati** sia stata già compilata con un elemento associato all'immagine in uso.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
### Per associare un'immagine di un database a un controllo  
  
1.  Verificare che l'area di progettazione alla quale si desidera aggiungere il controllo sia aperta in Progettazione WPF o in Progettazione Windows Form.  
  
2.  Nella finestra **Origini dati** espandere la tabella o l'oggetto desiderato per visualizzare le rispettive colonne o proprietà.  
  
3.  Selezionare la colonna o la proprietà che include i dati di immagine e selezionare uno dei controlli seguenti dal relativo elenco:  
  
    -   Se Progettazione WPF è aperto, selezionare **Immagine**.  
  
    -   Se Progettazione di Windows Form è aperto, selezionare **PictureBox**.  
  
    -   In alternativa, è possibile selezionare un controllo diverso che supporta l'associazione a dati ed è in grado di visualizzare immagini.  Se il controllo che si desidera utilizzare non è presente nell'elenco dei controlli disponibili, è necessario aggiungerlo all'elenco e selezionarlo.  Per ulteriori informazioni, vedere [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## Vedere anche  
 [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md)   
 [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)   
 [Aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md)   
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Cenni preliminari sulle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)