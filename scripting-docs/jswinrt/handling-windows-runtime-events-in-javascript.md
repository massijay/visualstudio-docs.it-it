---
title: "Gestione di eventi di Windows Runtime in JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "JavaScript, eventi Windows Runtime"
  - "eventi Windows Runtime [JavaScript]"
ms.assetid: d9436aff-2c30-4846-b8df-eaa3e63fd75c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Gestione di eventi di Windows Runtime in JavaScript
Gli eventi di Windows Runtime non sono rappresentati nello stesso modo in JavaScript rispetto a C\+\+ o .NET Framework.  Non sono proprietà di classi, ma sono piuttosto rappresentati come identificatori di stringa passati ai metodi `addEventListener` e `removeEventListener` della classe.  È ad esempio possibile aggiungere un gestore eventi per l'evento [Geolocator.PositionChanged](http://msdn.microsoft.com/library/windows/apps/xaml/windows.devices.geolocation.geolocator.positionchanged.aspx) passando la stringa "positionchanged" al metodo `Geolocator.addEventListener`:  
  
```javascript  
var locator =  new Windows.Devices.Geolocation.Geolocator();  
locator.addEventListener(  
    "positionchanged",   
     function (ev) {  
        console.log("Got event");  
    });  
```  
  
 È anche possibile impostare la proprietà `locator.onpositionchanged`.  
  
```  
locator.onpositionchanged =    
    function (ev) {  
        console.log("Got event");  
    };  
```  
  
 In JavaScript gli argomenti degli eventi di Windows Runtime sono rappresentati come singolo oggetto evento.  Nell'esempio seguente, relativo a un metodo di gestore eventi, il parametro `ev` è un oggetto che contiene il mittente \(proprietà di destinazione\) e gli altri argomenti dell'evento.  Gli argomenti dell'evento sono documentati per ogni evento.  
  
```javascript  
function (ev) {  
    console.log("Target: " + ev.target);  
    console.log("Position: " +  
        ev.position.latitude + "," +  
        ev.position.longitude);  
};  
  
```  
  
> [!IMPORTANT]
>  Le funzionalità di Windows Runtime non sono disponibili per app eseguite in Internet Explorer.  
  
## Vedere anche  
 [Utilizzo di Windows Runtime in JavaScript](../jswinrt/using-the-windows-runtime-in-javascript.md)