---
title: "Procedura: creare modelli di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ExportTemplateWizard"
helpviewer_keywords: 
  - "modelli di progetto, creazione"
  - "modelli di progetto, posizioni di modelli personalizzati"
  - "modelli di progetto, file di metadati"
  - "modelli di Visual Studio, creazione di modelli di progetto"
  - "modelli di Visual Studio, modelli di progetto"
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura: creare modelli di progetto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa procedura consente di creare un modello utilizzando l'**Esportazione guidata modelli** che consente di creare pacchetti del modello in un file zip.  È anche possibile creare modelli nel formato di file VSIX per una migliore distribuzione utilizzando l'estensione dell' esportazione guidata, o con i modelli inclusi in [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]alternativa, è possibile creare i modelli manualmente.  
  
### Per creare un modello di progetto personalizzato utilizzando l'Esportazione guidata modelli standard  
  
1.  Creare un progetto.  
  
    > [!NOTE]
    >  Utilizzare solo caratteri validi per un identificatore quando si assegna un nome a un progetto che sarà utilizzato come origine per un modello.  Un modello esportato da un progetto denominato con caratteri non validi può provocare errori di compilazione nei progetti futuri basati sul modello.  Per ulteriori informazioni sui caratteri validi per un identificatore, vedere [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Modificare il progetto e renderlo idoneo ad essere esportato come modello.  
  
3.  Modificare nel modo appropriato i file di codice per indicare dove verrà applicata la sostituzione dei parametri.  Per ulteriori informazioni sulla sostituzione dei parametri, vedere [Procedura: sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Nel menu **File** scegliere **Esporta modello**.  Viene aperta l'**Esportazione guidata modelli**.  
  
5.  Fare clic su **Modelli di progetto**.  
  
6.  Se la soluzione corrente contiene più progetti, selezionare i progetti che si desidera esportare in un modello.  
  
7.  Scegliere **Avanti**.  
  
8.  Selezionare un'icona e un'immagine di anteprima per il modello.  Queste ultime verranno visualizzate nella finestra di dialogo **Nuovo progetto**.  
  
9. Immettere un nome e una descrizione per il modello.  
  
10. Fare clic su **Fine**.  Il progetto verrà esportato in un file con estensione zip e inserito nel percorso di output specificato e, se selezionato, verrà importato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Con [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installato, è possibile eseguire il wrapping del modello finito in un file con estensione vsix per la distribuzione tramite il modello **Progetto VSIX**.  Per ulteriori informazioni, vedere [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## Vedere anche  
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Procedura: creare modelli di elementi](../ide/how-to-create-item-templates.md)