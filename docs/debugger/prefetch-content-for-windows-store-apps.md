---
title: "Prelettura del contenuto per le applicazioni Windows Store | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: b4481fef-3ebf-4f7d-9748-d43821a0ebac
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Prelettura del contenuto per le applicazioni Windows Store
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per migliorare la velocità di risposta della tua app di Windows Store, puoi richiedere il precaricamento da parte di Windows di parte del contenuto Web, ad esempio immagini o pagine Web, nella cache [WinINet](http://msdn.microsoft.com/it-it/0a06f2af-957a-4dff-a8cc-187370181b5c) [WinINet](http://msdn.microsoft.com/library/aa383630.aspx) dell'app. Questa funzionalità, nota come "caricamento di contenuto in background", è particolarmente utile per il contenuto usato all'avvio, anche se puoi caricare in background altro contenuto usato di frequente. I metodi della classe [Windows.Networking.BackgroundTransfer.ContentPrefetcher](http://msdn.microsoft.com/library/windows/apps/windows.networking.backgroundtransfer.contentprefetcher.aspx) consentono di specificare gli URI del contenuto da caricare in background. Per esempi relativi all'aggiunta della funzionalità ContentPrefetcher, vedi il Windows SDK [Esempio di prelettura di contenuto](http://code.msdn.microsoft.com/windowsapps/ContentPrefetcher-Sample-432c8309).  
  
 Windows usa le regole euristiche per determinare quando e se eseguire la prelettura e quali risorse verranno scaricate. Le regole euristiche tengono conto delle condizioni di alimentazione e rete del sistema, della cronologia di utilizzo delle app utente e dei risultati dei precedenti tentativi di caricamento in background. In Visual Studio puoi usare il comando **Trigger prelettura applicazioni Windows Store** per forzare Windows a ignorare le regole euristiche ContentPrefetcher e a precaricare tutto il contenuto Web specificato. Questo può essere utile se desideri testare le prestazioni o il comportamento dell'app con la prelettura del contenuto in uno stato noto \(caricato o meno\).  
  
## Per forzare il precaricamento delle risorse specificate di ContentPrefetcher  
 Questa procedura presuppone che tu abbia già impostato la funzionalità ContentPrefetcher e specificato gli URI di contenuto da precaricare nel progetto dell'app. Per forzare il precaricamento del contenuto quando le risorse specificate sono nuove o modificate, devi avviare e arrestare l'app prima di scegliere il comando **Trigger prelettura applicazioni Windows Store**. Prima di tutto esegui l'app per registrare gli URI. Il comando **Trigger prelettura applicazioni Windows Store** forza la funzionalità ContentPrefetcher a scaricare il contenuto e ad aggiungerlo nella cache. Nelle esecuzioni successive dell'app, puoi presupporre che il contenuto sia stato precaricato.  
  
1.  Avvia l'app per registrare gli URI del contenuto di prelettura con l'app. Scegli **Avvia debug**  \(Tasto di scelta rapida: F5\) dal menu **Debug**.  
  
2.  Scegli **Termina debug** dal menu **Debug** \(Tasto di scelta rapida: MAIUSC\+F5\).  
  
3.  Scegli **Altre destinazioni debug** dal menu **Debug**, quindi scegli **Trigger prelettura applicazioni Windows Store**.  
  
 Ora puoi eseguire testare, analizzare o eseguire il debug dell'app con le risorse Web in prelettura.  
  
> [!NOTE]
>  Ripeti questi passaggi quando aggiungi o modifichi il contenuto Web specificato.  
  
## Vedere anche  
 [Post di blog: Trigger prelettura app di Windows in Visual Studio 2013 Update 2](http://blogs.msdn.com/b/visualstudioalm/archive/2014/02/06/triggering-prefetch-for-windows-store-apps-in-visual-studio-2013-update-2.aspx)