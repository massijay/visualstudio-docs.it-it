---
title: "Utilizzo della Casella degli strumenti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.chooseitems"
  - "vs.toolboxpages.activexcontrols"
  - "VS.CHOOSEITEMS.windowsuixamlcomponents"
  - "VS.chooseitems.silverlightcomponents"
  - "VC.EDITORS.RIBBON"
  - "vs.customizetoolbox"
  - "VS.chooseitems.System.Workflow_Components"
  - "vs.chooseitems.frameworkcomponents"
  - "VS.ToolboxPages..NET_Framework_Components"
  - "VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage"
  - "vs.chooseitems.comcomponents"
  - "vs.toolboxpages.NGWS_components"
helpviewer_keywords: 
  - "casella degli strumenti"
  - "casella degli strumenti, aggiunta di elementi"
  - "casella degli strumenti, schede"
  - "Visual Studio, casella degli strumenti"
ms.assetid: 82e7cb43-4d0b-4e17-b7b0-43f96c22c3c2
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Utilizzo della Casella degli strumenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile usare la casella degli strumenti per aggiungere controlli e altri elementi al progetto.  È possibile trascinare diversi controlli sulla superficie della finestra di progettazione in uso nonché ridimensionare e posizionare tali controlli.  
  
 La casella degli strumenti viene visualizzata insieme alle visualizzazioni delle finestre di progettazione, ad esempio la visualizzazione Progettazione di un file XAML.  La casella degli strumenti visualizza solo i controlli che possono essere usati nella finestra di progettazione corrente.  
  
 La versione di.NET Framework di destinazione del progetto influisce sul set di controlli visibili nella casella degli strumenti.  Per impostazione predefinita, i progetti [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] hanno come destinazione .NET Framework 4.5.1.  È possibile impostare il progetto per destinarlo a una versione diversa di.NET Framework selezionandone il nodo in **Esplora soluzioni** quindi passando a **Proprietà\/Applicazione\/Framework di destinazione**.  
  
## Gestione della casella degli strumenti e dei relativi controlli  
 Per impostazione predefinita, la casella degli strumenti viene compressa lungo la parte sinistra dell'IDE di Visual Studio e viene visualizzata quando il cursore viene spostato su di essa.  È possibile bloccare la casella degli strumenti facendo clic sull'icona **Blocca** sulla barra degli strumenti della casella degli strumenti, in modo che resti aperta quando il cursore viene spostato.  È anche possibile disancorare la finestra della casella degli strumenti e trascinarla in qualsiasi posizione sullo schermo.  È possibile ancorare, disancorare e nascondere la casella degli strumenti facendo clic con il pulsante destro del mouse sulla barra degli strumenti della casella degli strumenti e selezionando una delle opzioni.  
  
 È possibile riordinare gli elementi di una scheda della casella degli strumenti o aggiungere schede ed elementi personalizzati usando i seguenti comandi del menu di scelta rapida:  
  
-   **Rinomina elemento** \- Rinomina l'elemento selezionato.  
  
-   **Mostra tutti** \- Mostra tutti i controlli possibili, non solo quelli applicabili alla finestra di progettazione corrente.  
  
-   **Visualizzazione elenco** \-Mostra i controlli in un elenco verticale.  Se deselezionati, i controlli vengono visualizzati in orizzontale.  
  
-   **Scegli elementi** \- Apre la finestra di dialogo **Scegli elementi della Casella degli strumenti** per poter specificare gli elementi visualizzati nella **casella degli strumenti**.   È possibile visualizzare o nascondere un elemento selezionando o deselezionando la relativa casella di controllo.  
  
-   **Ordina elementi alfabeticamente** \- Ordina gli elementi per nome.  
  
-   **Reimposta barra degli strumenti** \- Ripristina le impostazioni e gli elementi predefiniti della casella degli strumenti.  
  
-   **Aggiungi scheda** \- Aggiunge una nuova scheda della casella degli strumenti.  
  
-   **Sposta su** \- Sposta l'elemento selezionato verso l'alto.  
  
-   **Sposta giù** \- Sposta l'elemento selezionato verso il basso.  
  
## Creare e distribuire controlli della casella degli strumenti personalizzati  
 È possibile creare un controllo della casella degli strumenti personalizzato in Visual Basic o in Visual C\#, iniziando con un modello di progetto basato su [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) o [Windows Form](../misc/how-to-create-a-toolbox-control-that-uses-windows-forms.md).  È quindi possibile distribuire il controllo ai colleghi del team o pubblicarlo nel sito Web usando il [programma di installazione dei controlli della casella degli strumenti](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).