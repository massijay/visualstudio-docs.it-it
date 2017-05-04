---
title: "Metodo atEnd (Enumerator) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "atEnd"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "atEnd (metodo)"
ms.assetid: 326808fb-9a0f-428e-aff1-b11b237913f1
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Metodo atEnd (Enumerator) (JavaScript)
Restituisce un valore booleano che indica se l'enumeratore si trova alla fine della raccolta.  
  
> [!WARNING]
>  Questo oggetto è supportato solo in Internet Explorer.  
  
## Sintassi  
  
```  
  
myEnum.atEnd()  
```  
  
## Note  
 Il riferimento *myEnum* obbligatorio è qualsiasi oggetto `Enumerator`.  
  
 Il metodo `atEnd` restituisce **true** se l'elemento corrente è l'ultimo nella raccolta, se la raccolta è vuota o se l'elemento corrente è non definito. Negli altri casi, viene restituito **false**.  
  
## Esempio  
 Nel codice seguente il metodo `atEnd` viene usato per stabilire se è stata raggiunta la fine di un elenco di unità:  
  
```javascript  
function ShowDrives()  
{  
    var s = "";  
    var bytesPerGB = 1024 * 1024 * 1024;  
  
    var fso = new ActiveXObject("Scripting.FileSystemObject");  
    var e = new Enumerator(fso.Drives);  
  
    e.moveFirst();  
    while (e.atEnd() == false)  
    {  
        var drv = e.item();  
  
        s += drv.Path + " - ";  
  
        if (drv.IsReady)  
        {  
            var freeGB = drv.FreeSpace / bytesPerGB;  
            var totalGB = drv.TotalSize / bytesPerGB;  
  
            s += freeGB.toFixed(3) + " GB free of ";  
            s += totalGB.toFixed(3) + " GB";  
        }  
        else  
        {  
            s += "Not Ready";  
        }  
  
        s += "<br />";  
  
        e.moveNext();  
    }  
    return(s);  
}  
```  
  
## Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
 **Si applica a**: [Oggetto Enumerator](../../javascript/reference/enumerator-object-javascript.md)  
  
## Vedere anche  
 [Metodo item \(Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [Metodo moveFirst \(Enumerator\)](../../javascript/reference/movefirst-method-enumerator-javascript.md)   
 [Metodo moveNext \(Enumerator\)](../../javascript/reference/movenext-method-enumerator-javascript.md)   
 [Oggetto Enumerator](../../javascript/reference/enumerator-object-javascript.md)