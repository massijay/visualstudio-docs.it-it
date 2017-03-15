---
title: "Finestra di dialogo Eventi di compilazione (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesBuildEvents"
helpviewer_keywords: 
  - "eventi di compilazione"
  - "eventi di compilazione, specifica"
  - "eventi pre-compilazione"
  - "Finestra di dialogo Eventi di compilazione"
  - "eventi post-compilazione"
ms.assetid: 3a81a7c7-39f9-47a8-ba5a-b351227f380e
caps.latest.revision: 4
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 4
---
# Finestra di dialogo Eventi di compilazione (Visual Basic)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzare la finestra di dialogo **Eventi di compilazione** per specificare istruzioni di configurazione della build.  È anche possibile specificare le condizioni in cui vengono eseguiti eventi pre\-compilazione o post\-compilazione.  Per ulteriori informazioni, vedere [Procedura: specificare gli eventi di compilazione \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md).  
  
 **Riga di comando eventi pre\-compilazione**  
 Specifica i comandi da eseguire prima dell'inizio della compilazione.  Per digitare comandi lunghi, fare clic su **Modifica pre\-compilazione** per visualizzare la [Finestra di dialogo Riga di comando eventi pre\-compilazione\/post\-compilazione](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md).  
  
> [!NOTE]
>  Gli eventi pre\-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata la compilazione.  
  
 **Riga di comando eventi post\-compilazione**  
 Specifica i comandi da eseguire al termine della compilazione.  Per digitare comandi lunghi, fare clic su **Modifica post\-compilazione** per visualizzare la finestra di dialogo **Riga di comando eventi pre\-compilazione\/post\-compilazione**.  
  
> [!NOTE]
>  Aggiungere un'istruzione `call` prima di tutti i comandi di post\-compilazione che eseguono file BAT.  Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
 **Esegui evento post\-compilazione**  
 Specifica le condizioni per l'evento di post\-compilazione da eseguire, come illustrato nella tabella che segue.  
  
|Opzione|Risultato|  
|-------------|---------------|  
|**Sempre**|L'evento di post\-compilazione verrà eseguito indipendentemente dall'esito della compilazione.|  
|**A compilazione completata**|L'evento di post\-compilazione verrà eseguito se la compilazione ha esito positivo.  L'evento verrà quindi eseguito anche per un progetto aggiornato, purché la compilazione venga completata.  Rappresenta l'impostazione predefinita.|  
|**Quando la compilazione aggiorna l'output del progetto**|L'evento di post\-compilazione verrà eseguito solo quando il file di output del compilatore \(EXE o DLL\) è diverso dal file di output del compilatore precedente.  Un evento di post\-compilazione non viene quindi eseguito se un progetto è aggiornato.|  
  
## Vedere anche  
 [Compilazione \(pagina\), Creazione progetti \(Visual Basic\)](../../ide/reference/compile-page-project-designer-visual-basic.md)   
 [Procedura: specificare gli eventi di compilazione \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Finestra di dialogo Riga di comando eventi pre\-compilazione\/post\-compilazione](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)