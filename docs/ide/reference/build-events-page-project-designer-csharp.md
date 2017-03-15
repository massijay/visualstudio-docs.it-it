---
title: "Pagina Eventi di compilazione, Progettazione progetti (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "eventi di compilazione"
  - "Creazione progetti, pagina Eventi di compilazione"
  - "eventi pre-compilazione"
  - "eventi post-compilazione"
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Pagina Eventi di compilazione, Progettazione progetti (C#)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La pagina **Eventi di compilazione** di **Progettazione progetti** consente di specificare le istruzioni di configurazione della build.  È anche possibile specificare le condizioni in base alle quali devono essere eseguiti gli eventi post\-compilazione.  Per ulteriori informazioni, vedere [Procedura: specificare eventi di compilazione \(C\#\)](../../ide/how-to-specify-build-events-csharp.md) e [Procedura: specificare gli eventi di compilazione \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md).  
  
## Elenco UIElement  
 **Configurazione**  
 Questo controllo non è modificabile in questa pagina.  Per una descrizione di questo controllo, vedere [Pagina Compilazione, Progettazione progetti \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Piattaforma**  
 Questo controllo non è modificabile in questa pagina.  Per una descrizione di questo controllo, vedere [Pagina Compilazione, Progettazione progetti \(C\#\)](../../ide/reference/build-page-project-designer-csharp.md).  
  
 **Riga di comando eventi pre\-compilazione**  
 Specifica i comandi da eseguire prima dell'inizio della compilazione.  Per digitare comandi lunghi, fare clic su **Modifica pre\-compilazione** per visualizzare la [Finestra di dialogo Riga di comando eventi pre\-compilazione\/post\-compilazione](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Gli eventi pre\-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata la compilazione.  
  
 **Riga di comando eventi post\-compilazione**  
 Specifica i comandi da eseguire al termine della compilazione.  Per digitare comandi lunghi, fare clic su **Modifica post\-compilazione** per visualizzare la **casella di dialogo Riga di comando eventi pre\-compilazione\/post\-compilazione**.  
  
> [!NOTE]
>  Aggiungere un'istruzione `call` prima di tutti i comandi di post\-compilazione che eseguono file BAT.  Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Esegui evento post\-compilazione**  
 Consente di specificare le condizioni riportate di seguito per l'evento di post\-compilazione da eseguire, come illustrato nella tabella che segue.  
  
|Opzione|Risultato|  
|-------------|---------------|  
|**Sempre**|L'evento di post\-compilazione verrà eseguito indipendentemente dall'esito della compilazione.|  
|**A compilazione completata**|L'evento di post\-compilazione verrà eseguito se la compilazione ha esito positivo.  L'evento verrà quindi eseguito anche per un progetto aggiornato, purché la compilazione venga completata.|  
|**Quando la compilazione aggiorna l'output del progetto**|L'evento di post\-compilazione viene eseguito solo quando il file di output del compilatore \(EXE o DLL\) è diverso da quello del compilatore precedente.  Un evento di post\-compilazione non viene quindi eseguito se un progetto è aggiornato.|  
  
## Vedere anche  
 [Procedura: specificare gli eventi di compilazione \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Procedura: specificare eventi di compilazione \(C\#\)](../../ide/how-to-specify-build-events-csharp.md)   
 [Riferimenti alle proprietà di progetto](../../ide/reference/project-properties-reference.md)   
 [Compilazione di applicazioni in Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)