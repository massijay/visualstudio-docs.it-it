---
title: "Oggetto Enumerator (JavaScript) | Microsoft Docs"
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
  - "Enumerator"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Enumerator (oggetto)"
ms.assetid: 63f03c21-d58c-47db-a728-4d8d88b0a422
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Oggetto Enumerator (JavaScript)
Abilita l'enumerazione di elementi di una raccolta.  
  
> [!WARNING]
>  Questo oggetto è supportato solo in Internet Explorer e non nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Sintassi  
  
```  
  
enumObj = new Enumerator([collection])   
```  
  
## Parametri  
 `enumObj`  
 Obbligatorio. Nome della variabile a cui l'oggetto `Enumerator` è assegnato.  
  
 `collection`  
 Facoltativo. Qualsiasi oggetto Collection.  
  
## Note  
 Le raccolte differiscono dalle matrici in quanto i membri di una raccolta non sono direttamente accessibili. Invece di usare indici, come si farebbe con le matrici, è possibile spostare il puntatore dell'elemento corrente solo sul primo elemento o sull'elemento successivo all'interno della raccolta.  
  
 L'oggetto `Enumerator` fornisce un modo per accedere a qualsiasi membro di una raccolta e si comporta in modo analogo all'istruzione `For...Each` in VBScript.  
  
## Esempio  
 Il codice seguente mostra l'uso dell'oggetto `Enumerator`:  
  
```javascript  
var bytesPerGB = 1024 * 1024 * 1024;  
  
var fso = new ActiveXObject("Scripting.FileSystemObject");  
  
document.write(fso.Drives);  
var e = new Enumerator(fso.Drives);  
  
var driveString = "";  
  
e.moveFirst();  
while (e.atEnd() == false)  
{  
    var drv = e.item();  
  
    driveString += drv.Path + " - ";  
  
    if (drv.IsReady){  
        var freeGB = drv.FreeSpace / bytesPerGB;  
        var totalGB = drv.TotalSize / bytesPerGB;  
  
        driveString += freeGB.toFixed(3) + " GB free of ";  
        driveString += totalGB.toFixed(3) + " GB";  
    }  
    else{  
        driveString += "Not Ready";  
    }  
  
    driveString += "<br />";;  
  
    e.moveNext();  
}  
document.write(driveString);  
  
// Output: <drive information  
  
```  
  
## Proprietà  
 L'oggetto `Enumerator` non ha alcuna proprietà.  
  
## Metodi  
 [Metodo atEnd](../../javascript/reference/atend-method-enumerator-javascript.md) &#124; [Metodo item](../../javascript/reference/item-method-enumerator-javascript.md) &#124; [Metodo moveFirst](../../javascript/reference/movefirst-method-enumerator-javascript.md) &#124; [Metodo moveNext](../../javascript/reference/movenext-method-enumerator-javascript.md)  
  
## Requisiti  
 Supportato nelle modalità documento seguenti: Quirks, standard di Internet Explorer 6, standard di Internet Explorer 7, standard di Internet Explorer 8, standard di Internet Explorer 9 e standard di Internet Explorer 10. Non supportato in applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
## Vedere anche  
 [Oggetto Boolean](../../javascript/reference/boolean-object-javascript.md)