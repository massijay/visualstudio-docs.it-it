---
title: Elemento CommandTable | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CommandTable
helpviewer_keywords:
- CommandTable element (VSCT XML schema)
- VSCT XML schema elements, CommandTable
ms.assetid: 15c38159-660a-4ef4-9643-aa6fcfca82a9
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 4a6abf25d0e3eff335c8a6fe62affc19d8037afa
ms.lasthandoff: 02/22/2017

---
# <a name="commandtable-element"></a>Elemento CommandTable
CommandTable è l'elemento radice del file vsct. Questo è il file che definisce il layout effettivo e il tipo di comandi che fornisce un VSPackage all'IDE. I comandi possono includere voci di menu, menu, barre degli strumenti e caselle combinate. Per ulteriori informazioni, vedere [tabella di comando Visual Studio (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
## <a name="syntax"></a>Sintassi  
  
```  
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema" >  
  <Extern>... </Extern>  
  <Include>... </Include>  
  <Define>... </Define>  
  <Commands>... </Commands>  
  <CommandPlacements>... </CommandPlacements>  
  <VisibilityConstraints>... </VisibilityConstraints>  
  <KeyBindings>... </KeyBindings>  
  <UsedCommands... </UsedCommands>  
  <Symbols>... </Symbols>  
</CommandTable>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|xmlns|Obbligatorio. Spazi dei nomi XML:<br /><br /> xmlns = "http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"<br /><br /> xmlns = "http://www.w3.org/2001/XMLSchema"|  
|language|Facoltativo. L'attributo language può essere utilizzato per specificare la lingua predefinita del tutto \<stringhe > elementi della tabella di comando.  Se la lingua non viene specificata, verrà utilizzata la lingua del processo corrente:<br /><br /> Language = "en-us"|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento extern](../extensibility/extern-element.md)|Facoltativo. Contiene le direttive del preprocessore del compilatore.|  
|[Elemento di inclusione](../extensibility/include-element.md)|Facoltativo. Contiene i percorsi di file da includere la compilazione.|  
|[Definire l'elemento](../extensibility/define-element.md)|Facoltativo. Definisce un simbolo dato il nome e valore.|  
|[Elemento Commands](../extensibility/commands-element.md)|Facoltativo. L'elemento padre che definisce tutti i comandi per il package VS che contiene tutti gli altri elementi.|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Facoltativo. Definisce sulla barra dei comandi i comandi devono essere inseriti.|  
|[Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Facoltativo. Determina la visibilità statica di comandi e barre degli strumenti.|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Facoltativo. Specifica le combinazioni di tasti di scelta rapida, se presente, per i comandi.|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Facoltativo. Consente un VSPackage se lo si desidera implementare la propria versione della funzionalità originariamente supportata da altri VSPackage.|  
|[Elemento di simboli](http://msdn.microsoft.com/en-us/f2ddd0aa-c3dd-439e-834d-28f136a27ffa)|Facoltativo. Contiene i dati di simbolo - GUID, ID e così via, per il compilatore.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|Nessuno||  
  
## <a name="see-also"></a>Vedere anche  
 [Tabella di comandi di Visual Studio (. File Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
