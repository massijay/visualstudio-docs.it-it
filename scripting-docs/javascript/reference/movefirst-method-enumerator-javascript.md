---
title: "Metodo moveFirst (Enumerator) (JavaScript) | Microsoft Docs"
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
  - "moveFirst"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "MoveFirst (metodo)"
ms.assetid: 96eedc66-7974-443c-b0cd-55373a7c0e59
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Metodo moveFirst (Enumerator) (JavaScript)
Reimposta l'elemento corrente nella raccolta sul primo elemento.  
  
> [!WARNING]
>  Questo oggetto è supportato solo in Internet Explorer.  
  
## Sintassi  
  
```  
  
enumObj.moveFirst( )  
```  
  
## Note  
 Il riferimento *enumObj* obbligatorio è qualsiasi oggetto `Enumerator`.  
  
 Se la raccolta non contiene elementi, l'elemento corrente viene impostato su non definito.  
  
## Esempio  
 Nell'esempio seguente il metodo `moveFirst` viene usato per valutare i membri della raccolta `Drives` a partire dall'inizio dell'elenco:  
  
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
 [Metodo atEnd \(Enumerator\)](../../javascript/reference/atend-method-enumerator-javascript.md)   
 [Metodo item \(Enumerator\)](../../javascript/reference/item-method-enumerator-javascript.md)   
 [Metodo moveNext \(Enumerator\)](../../javascript/reference/movenext-method-enumerator-javascript.md)