---
title: "Riferimento allo Schema XML VSCT | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio comando tabella file di configurazione (VSCT), XML schema"
  - "Elementi dello schema XML VSCT"
ms.assetid: 49e7efae-e713-4762-a824-96fdaf92cdc9
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Riferimento allo Schema XML VSCT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Fornisce una tabella di elementi dello schema di comando del compilatore di tabella, con figlio consentito elementi e attributi per ognuno.  
  
 Un file di configurazione \(vsct\) tabella comando basato su XML definisce gli elementi di comando che fornisce un VSPackage all'ambiente di sviluppo integrato \(IDE\). Questi elementi includono voci di menu, menu, barre degli strumenti e caselle combinate.  
  
> [!NOTE]
>  Il compilatore VSCT può eseguire un preprocessore nel file vsct. Poiché si tratta in genere include il preprocessore, che è possibile definire C\+\+ e macro che hanno la stessa sintassi utilizzata nel file di C\+\+. Nel vsct vengono forniti esempi di questo file di **Nuovo progetto** verrà creato un progetto VSPackage.  
  
## Elementi facoltativi  
 Alcuni elementi VSCT sono facoltativi. Se un `Parent` viene omesso, verrà implicita Group\_Undefined:0. Se un `Icon` viene omesso, verrà implicita guidOfficeIcon:msotcidNoIcon. Quando viene definito un tasto di scelta rapida, l'emulazione, che non viene utilizzato in genere, è facoltativo.  
  
 Elementi bitmap possono essere incorporati in fase di compilazione, specificando la posizione della striscia nella bitmap di `href` argomento. La striscia bitmap viene copiata durante l'unione anziché estratti dalle risorse della DLL. Quando un `href` argomento viene fornito, il `usedList` argomento diventa facoltativo e vengono considerati tutti gli slot nella striscia di bitmap utilizzata.  
  
 Tutti i valori GUID e ID devono essere definiti utilizzando i nomi simbolici. Questi nomi possono essere definiti nei file di intestazione o nelle sezioni VSCT \< simboli \>. I nomi simbolici devono essere locali, inclusi tra gli elementi \< Include \>, o a cui fanno riferimento gli elementi \< Extern \>. Un nome simbolico viene importato da un file di intestazione specificato in un elemento \< Extern \> se segue il modello semplice di \#define valore di simbolo. Il valore può essere un altro simbolo, purché tale simbolo è stato definito in precedenza. Definizioni GUID devono rispettare OLE o C\+\+. I valori di ID possono essere cifre decimali o cifre esadecimali preceduti da 0x, come illustrato nelle righe seguenti:  
  
-   {6D484634\-E53D\-4a2c\-ADCB\-55145C9362C8}  
  
-   {0x6d484634, 0xe53d, 0x4a2c, {0xad, 0xcb, 0x55, 0x14, 0x5c, 0x93, 0x62, 0xc8}}  
  
 I commenti XML possono essere utilizzati, ma potrebbero ignorarle strumenti di interfaccia utente grafica round trip. Il contenuto di elementi \< Annotation \> è garantito a essere gestito indipendentemente dal formato.  
  
## Gerarchia dello schema  
 Un file. vsct ha i seguenti elementi principali.  
  
 [Elemento CommandTable](../extensibility/commandtable-element.md)  
  
 [Elemento extern](../extensibility/extern-element.md)  
  
 [Elemento di inclusione](../extensibility/include-element.md)  
  
 [Definire l'elemento](../extensibility/define-element.md)  
  
 [Elemento Commands](../extensibility/commands-element.md)  
  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)  
  
 [Elemento VisibilityConstraints](../extensibility/visibilityconstraints-element.md)  
  
 [Elemento KeyBindings](../extensibility/keybindings-element.md)  
  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)  
  
 [Elemento padre](../extensibility/parent-element.md)  
  
 [Icona elemento](../extensibility/icon-element.md)  
  
 [Elemento di stringhe](../extensibility/strings-element.md)  
  
 [Elemento di Flag di comando](../extensibility/command-flag-element.md)  
  
 [Elemento di simboli](../extensibility/symbols-element.md)  
  
 [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md)  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing dei comandi in VS](../extensibility/internals/command-routing-in-vspackages.md)