---
title: "Procedura: aggiornare modelli esistenti | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli di elementi, aggiornamento di modelli esistenti"
  - "modelli di progetto, aggiornamento di modelli esistenti"
  - "modelli di Visual Studio, aggiornamento di modelli esistenti"
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: aggiornare modelli esistenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dopo aver creato un modello e compresso i file in un file ZIP, può essere necessario modificare il modello.  L'operazione può essere eseguita manualmente cambiando i file nel modello oppure esportando un nuovo modello da un progetto basato sul modello.  
  
## Uso dell'Esportazione guidata modelli per aggiornare un modello esistente  
 L'**Esportazione guidata modelli** disponibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] può essere usata per aggiornare un modello esistente.  
  
#### Per usare l'Esportazione guidata modelli per aggiornare un modello esistente  
  
1.  Scegliere **Nuovo** dal menu **File**, quindi **Nuovo progetto**.  
  
2.  Selezionare il modello da aggiornare, specificare un nome e un percorso per il progetto temporaneo, quindi fare clic su **OK**.  
  
3.  Modificare il progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Scegliere **Esporta modello** dal menu **File** e usare l' **Esportazione guidata modelli** per creare un nuovo modello.  
  
5.  Dopo aver compresso il modello aggiornato in un file con estensione zip, eliminare il file ZIP del modello precedente.  
  
## Aggiornamento manuale di un modello esistente  
 È possibile aggiornare un modello esistente al di fuori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modificando i file inclusi nel file compresso con estensione zip.  
  
#### Per aggiornare manualmente un modello esistente  
  
1.  Individuare il file ZIP che contiene il modello.  Per impostazione predefinita, questo file si trova in Documenti\\Visual Studio *Versione*\\My Exported Templates\\.  
  
2.  Estrarre il file ZIP.  
  
3.  Modificare o eliminare i file del modello corrente o aggiungere nuovi file al modello.  
  
4.  Aprire, modificare e salvare il file XML con estensione vstemplate per gestire il nuovo comportamento o i nuovi file.  Per altre informazioni sullo schema vstemplate, vedere [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  Per altre informazioni sugli elementi che è possibile parametrizzare nei file di origine, vedere [Parametri di modelli](../ide/template-parameters.md)  
  
5.  Selezionare i file inclusi nel modello, fare clic con il pulsante destro del mouse, scegliere **Invia a**, quindi **Cartella compressa**.  I file selezionati verranno compressi in un file ZIP.  
  
6.  Inserire il nuovo file ZIP nella stessa directory del vecchio file ZIP.  
  
7.  Eliminare i file di modello estratti e il vecchio file di modello ZIP.  
  
8.  Avviare come amministratore un'istanza del prompt dei comandi di sviluppo \(nel menu Start, in **Visual Studio 2010\/Strumenti di Visual Studio\/Prompt dei comandi per gli sviluppatori**\).  
  
9. Eseguire il comando seguente: `devenv /installvstemplates`.  
  
## Vedere anche  
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Parametri di modelli](../ide/template-parameters.md)   
 [Procedura: creare starter kit](../ide/how-to-create-starter-kits.md)