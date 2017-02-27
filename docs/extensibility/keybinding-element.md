---
title: "Elemento dell&#39;oggetto KeyBinding | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, KeyBindings"
  - "Elemento dell'oggetto KeyBinding (VSCT XML schema)"
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Elemento dell&#39;oggetto KeyBinding
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento dell'oggetto KeyBinding specifica tasti di scelta rapida per i comandi.  
  
 Comandi possono avere una o due tasti di scelta rapida associati. Un esempio di una singola combinazione di tasti è CTRL \+ S per il **salvare** comando. Due tasti di scelta rapida richiedono due combinazioni di tasti successive per attivare un comando. Un esempio di un'associazione chiave duale è CTRL \+ K,CTRL \+ K per impostare un segnalibro.  
  
## Sintassi  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Obbligatorio.|  
|ID|Obbligatorio.|  
|Editor|Obbligatorio. L'editor GUID indica il contesto di modifica per il quale sarà attivo il tasto di scelta rapida. Il valore di ambito globale di associazione è "guidVSStd97".|  
|Key1|Obbligatorio. I valori validi includono tutti possibile digitare caratteri alfanumerici e inoltre valori esadecimali a due cifre preceduti da 0x e VK\_constants.|  
|MOD1|Facoltativo. Qualsiasi combinazione di CTRL, ALT e MAIUSC separati da spazi.|  
|Key2|Facoltativo. I valori validi includono tutti possibile digitare caratteri alfanumerici e inoltre valori esadecimali a due cifre preceduti da 0x e VK\_constants.|  
|MOD2|Facoltativo. Qualsiasi combinazione di CTRL, ALT e MAIUSC separati da spazi.|  
|emulatore|Facoltativo.|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Padre||  
|Annotazione||  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento KeyBindings](../extensibility/keybindings-element.md)|Raggruppa gli elementi dell'oggetto KeyBinding e altri raggruppamenti KeyBindings.|  
  
## Esempio  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## Vedere anche  
 [Elemento KeyBindings](../extensibility/keybindings-element.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)