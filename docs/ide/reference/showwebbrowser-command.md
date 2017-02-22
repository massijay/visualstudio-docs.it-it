---
title: "Comando ShowWebBrowser | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "view.showwebbrowser"
helpviewer_keywords: 
  - "ShowWebBrowser (comando)"
  - "View.ShowWebBrowser (comando)"
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando ShowWebBrowser
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visualizza l'URL specificato in una finestra del browser all'interno o all'esterno dell'ambiente di sviluppo integrato \(IDE\).  
  
## Sintassi  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## Argomenti  
 `URL`  
 Obbligatorio.  L'URL \(Uniform Resource Locator\) del sito Web.  
  
## Opzioni  
 \/new  
 Parametro facoltativo.  Specifica che la pagina viene visualizzata in una nuova istanza del browser.  
  
 \/ext  
 Parametro facoltativo.  Specifica che la pagina viene visualizzata nel browser predefinito all'esterno dell'IDE.  
  
## Note  
 L'alias per il comando **ShowWebBrowser** è **navigate** o **nav**.  
  
## Esempio  
 Nell'esempio riportato di seguito, la home page di MSDN Online viene visualizzata in un browser all'esterno dell'IDE.  Se è già aperta un'istanza del browser, viene utilizzata tale istanza, altrimenti ne viene avviata una nuova.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## Vedere anche  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Finestra di comando](../../ide/reference/command-window.md)   
 [Casella Trova\/Comando](../../ide/find-command-box.md)   
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)