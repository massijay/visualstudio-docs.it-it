---
title: "I GUID e ID dei comandi di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandi"
  - "ID"
  - "posizionamento di comando"
  - "comandi di Visual studio"
  - "GUID"
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# I GUID e ID dei comandi di Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

I valori ID e di GUID dei controlli inclusi nell'ambiente di sviluppo integrato di \(IDE\) Visual Studio sono definiti in file di .vsct installati come parte di Visual Studio SDK.  Per ulteriori informazioni, vedere [Gruppi, menu e comandi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Per ulteriori informazioni su come utilizzare gli oggetti dell'IDE definiti in file di .vsct, vedere [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
## Ricerca di una definizione di comando  
 Poiché Visual Studio definisce più di milli controlli, è opportuno che tutti di seguito.  invece, seguire questi passaggi per individuare la definizione di un comando.  
  
#### Per individuare una definizione di comando  
  
1.  In Visual Studio, aprire i file seguenti in *percorso di installazione di Visual Studio SDK*\\VisualStudioIntegration\\Common\\Inc\\ folder: SharedCmdDef.vsct, ShellCmdDef.vsct, VsDbgCmdUsed.vsct, Venusmenu .vsct.  
  
     La maggior parte dei comandi di Visual Studio sono definiti in SharedCmdDef.vsct e in ShellCmdDef.vsct.  VsDbgCmdUsed.vsct definisce i relativi controlli il debugger e Venusmenu.vsct definisce i controlli specifici di sviluppo Web.  
  
2.  Se il comando è una voce di menu, trascrivere il testo esatto della voce di menu.  Se il comando è un pulsante di una barra degli strumenti, trascrivere il testo di descrizione comando che viene visualizzato quando si posiziona il mouse su.  
  
3.  Premere CTRL\+F per aprire la finestra di dialogo di **Ricerca** .  
  
4.  Nella casella di **Ricerca cosa** , digitare il testo che è stato indicato nel passaggio 2.  
  
5.  Verificare che **tutti i documenti aperti** visualizzato nella casella di **Analizzare l'interno di** .  
  
6.  Fare clic sul pulsante di **Trova successivo** fino a selezionare il testo nella sezione di `<Strings>` di un oggetto. [Elemento Button](../../extensibility/button-element.md)  
  
     L'elemento di `<Button>` che il comando viene visualizzato in è la definizione di comando.  
  
 Dopo avere trovato la definizione di comando, è possibile inserire una copia del comando in un altro menu o la barra degli strumenti creando [Elemento CommandPlacement](../../extensibility/commandplacement-element.md) che ha lo stesso `guid` e valori di `id` del comando.  Per ulteriori informazioni, vedere [Creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### casi speciali  
 Nei seguenti casi, il testo del menu o il testo della descrizione comandi non può corrispondere esattamente a quello nella definizione di comando.  
  
-   Voci di menu che includono un carattere sottolineato, ad esempio il comando di **stampa** il menu File, dove P è sottolineata.  
  
     I caratteri che sono preceduti “&„ di carattere nei nomi delle voci di menu vengono visualizzate come sottolineati.  Tuttavia, i file .vsct sono scritti in XML, che utilizza il carattere "&" per indicare i caratteri speciali e richiede che la e commerciale da visualizzare sia scritta come "&amp;".  Therefore, in a .vsct file, the **P**rint command appears as '&amp;Print'.  
  
-   Controlli che includono il testo dinamico, come **Salvare** *nome file corrente*e voci di menu generare dinamicamente, ad esempio gli elementi nell'elenco di **file recenti** .  
  
     Non esiste un modo affidabile per trovare in testo dinamico.  Invece, trovare un gruppo che ospita il comando desiderato consultandosi [GUID e ID del menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)e la ricerca sull'ID di tale gruppo.  Se la definizione di comando dispone del gruppo della [Elemento padre](../../extensibility/parent-element.md), trovare SharedCmdPlace.vsct e ShellCmdPlace.vsct \(o VsDbgCmdPlace.vsct per i comandi del debugger\) un elemento di `<CommandPlacement>` che imposta il padre del comando.  SharedCmdPlace.vsct, ShellCmdPlace.vsct, andVsDbgCmdPlace.vsct sono in *percorso di installazione di Visual Studio SDK*\\VisualStudioIntegration\\Common\\Inc \\.  
  
## Vedere anche  
 [Confronto tra oggetti MenuCommand e OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)