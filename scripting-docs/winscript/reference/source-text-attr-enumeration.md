---
title: "Enumerazione SOURCE_TEXT_ATTR | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Costanti SOURCE_TEXT_ATTR"
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Enumerazione SOURCE_TEXT_ATTR
Descrivere gli attributi di un singolo carattere di testo originale.  
  
## Sintassi  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR  
{  
    SOURCETEXT_ATTR_KEYWORD    = 0x0001,  
    SOURCETEXT_ATTR_COMMENT    = 0x0002,  
    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,  
    SOURCETEXT_ATTR_OPERATOR   = 0x0008,  
    SOURCETEXT_ATTR_NUMBER    = 0x0010,  
    SOURCETEXT_ATTR_STRING    = 0x0020,  
    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040  
};  
  
```  
  
## Membri  
  
|Membro|Valore|Descrizione|  
|------------|------------|-----------------|  
|SOURCETEXT\_ATTR\_KEYWORD|0x0001|Il carattere fa parte di una parola chiave del linguaggio, ad esempio, la parola chiave `While`VBScript.|  
|SOURCETEXT\_ATTR\_COMMENT|0x0002|Il carattere fa parte di un blocco di commenti.|  
|SOURCETEXT\_ATTR\_NONSOURCE|0x0004|Il carattere non fa parte del testo originale del linguaggio compilato.  Ad esempio, HTML che racchiude un blocco di script.|  
|SOURCETEXT\_ATTR\_OPERATOR|0x0008|Il carattere fa parte di un operatore di linguaggio.  Ad esempio: , l'operatore aritmetico **\+**.|  
|SOURCETEXT\_ATTR\_NUMBER|0x0010|Il carattere fa parte di una costante numerica del linguaggio.  Ad esempio, i 3,14159 costanti.|  
|SOURCETEXT\_ATTR\_STRING|0x0020|Il carattere fa parte di una costante di stringa del linguaggio.  Ad esempio, la stringa "Hello World".|  
|SOURCETEXT\_ATTR\_FUNCTION\_START|0x0040|Il carattere indica l'inizio di un blocco funzione|  
  
## Note  
 In genere, `IDebugDocumentHost::GetScriptTextAttributes`, `IActiveScriptDebug::GetScriptletTextAttributes`e i metodi `IActiveScriptDebug::GetScriptTextAttributes` restituiscono un attributo di testo per carattere, a meno che:  
  
-   Il flag di GETATTRTYPE\_DEPSCAN è impostato, nel qual caso il metodo restituisce i flag di SOURCETEXT\_ATTR\_MEMBERLOOKUP e di SOURCETEXT\_ATTR\_IDENTIFIER,  
  
-   Il flag di GETATTRFLAG\_THIS è impostato, nel qual caso il metodo può restituire il flag di SOURCETEXT\_ATTR\_THIS,  
  
-   Il flag di GETATTRFLAG\_HUMANTEXT è impostato, nel qual caso il metodo può restituire il flag di SOURCETEXT\_ATTR\_HUMANTEXT.  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)