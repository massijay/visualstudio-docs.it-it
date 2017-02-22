---
title: "Estensione menu e comandi | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "menu, le attività comuni"
  - "Package VS, attività di menu"
  - "file. vsct, attività comuni di menu"
ms.assetid: 7b2be4b9-e3fe-4412-874f-ae72ebc84c4b
caps.latest.revision: 49
caps.handback.revision: 49
ms.author: "gregvanl"
manager: "ghogen"
---
# Estensione menu e comandi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I comandi sono la procedura per aggiungere azioni e i processi a Visual Studio. Nella maggior parte dei casi i comandi vengono visualizzati nei menu o barre degli strumenti. Il modello di progetto VSPackage viene illustrato come implementare un comando di base. Per un'implementazione di base comunque ma leggermente più lunga, vedere [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
 Per ulteriori informazioni sui comandi, menu e barre degli strumenti di Visual Studio, vedere [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 I comandi, menu e barre degli strumenti sono definiti nel file vsct che fa parte di progetti VSPackage. È possibile trovare informazioni sull'IDE di Visual Studio e il file vsct in [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Gli argomenti seguenti viene illustrato come aggiungere diversi tipi di comandi, menu e barre degli strumenti.  
  
## In questa sezione  
 [Aggiunta di un Menu alla barra dei Menu di Visual Studio](../extensibility/adding-a-menu-to-the-visual-studio-menu-bar.md)  
 Viene illustrato come aggiungere un menu nella parte superiore della barra di menu di Visual Studio.  
  
 [Scelte rapide da tastiera di associazione di voci di Menu](../extensibility/binding-keyboard-shortcuts-to-menu-items.md)  
 Viene illustrato come aggiungere un tasto di scelta rapida \(ad esempio CTRL \+ 3\) per una voce di menu.  
  
 [Aggiunta di un sottomenu a un Menu](../extensibility/adding-a-submenu-to-a-menu.md)  
 Viene illustrato come aggiungere un sottomenu al menu principale.  
  
 [Aggiunta di una più recente di elenco a un sottomenu usati](../extensibility/adding-a-most-recently-used-list-to-a-submenu.md)  
 Viene illustrato come aggiungere un elenco usati di recente.  
  
 [Creazione di gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md)  
 Viene descritto come raggruppare gli elementi di comando in modo che possono essere inclusi in più menu.  
  
 [Aggiunta di icone ai comandi di Menu](../extensibility/adding-icons-to-menu-commands.md)  
 Viene descritto come aggiungere un'icona per un comando su una barra degli strumenti sia un menu.  
  
 [Modifica del testo di un comando di Menu](../extensibility/changing-the-text-of-a-menu-command.md)  
 Viene descritto come utilizzare il `TextChanges` flag per abilitare una voce di menu da modificare in modo dinamico.  
  
 [Modifica dell'aspetto di un comando](../extensibility/changing-the-appearance-of-a-command.md)  
 Viene descritto come abilitare o disabilitare un comando in modo dinamico.  
  
 [Aggiornamento dell'interfaccia utente](../extensibility/updating-the-user-interface.md)  
 Viene descritto come forzare un aggiornamento dell'interfaccia utente in modo da riflettere le modifiche più recenti.  
  
 [Localizzazione di comandi di Menu](../extensibility/localizing-menu-commands.md)  
 Viene illustrato come localizzare i comandi di menu.  
  
## Sezioni correlate