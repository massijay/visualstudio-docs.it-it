---
title: "Oggetto WinRTError (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "JavaScript, WinRTError (oggetto)"
  - "WinRTError (oggetto) [JavaScript]"
ms.assetid: d75ab8e5-e729-4d86-90fd-ea228c30dd66
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Oggetto WinRTError (JavaScript)
Quando una chiamata di Windows Runtime ritorna un HRESULT che indica un errore, JavaScript lo converte in un errore speciale di Windows Runtime.  È disponibile solo nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], quando Windows Runtime è disponibile, come parte dello spazio dei nomi globale di JavaScript.  
  
## Sintassi  
  
```  
  
errorObj = new WinRTError();   
```  
  
## Note  
 Il tipo di errore di WinRTError viene usato solo per errori generati dalle API di Windows Runtime.  
  
## Esempio  
 L'esempio seguente mostra come viene generato e intercettato un oggetto WinRTError.  
  
```javascript  
try {  
            Windows.Storage.ApplicationData.localFolder.createFileAsync("sample.txt");  
        } catch (err) {  
            var n = err;  
        }  
  
```  
  
## Metodi  
 L'oggetto WinRTError non ha metodi.  
  
## Proprietà  
 L'oggetto WinRTError ha le stesse proprietà dell'oggetto [Oggetto Error](../../javascript/reference/error-object-javascript.md).  
  
## Requisiti  
 È supportato solo nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] e non in Internet Explorer.  
  
## Vedere anche  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)