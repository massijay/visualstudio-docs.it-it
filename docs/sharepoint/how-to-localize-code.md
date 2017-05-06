---
title: "Procedura: localizzare il codice"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "localizzazione di codice [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, localizzazione"
ms.assetid: 0e852052-5ad4-4517-81cf-8865ec304441
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura: localizzare il codice
  Nel codice non localizzato vengono utilizzati valori stringa hardcoded.  Per localizzare stringhe di codice, sostituirle con chiamate a <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>, ovvero un metodo che fa riferimento a risorse localizzate.  
  
## Localizzazione del codice  
  
#### Per localizzare il codice  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida per un elemento del progetto e quindi scegliere **Aggiungi**, **Modulo**.  
  
     Scegliere il modello **File di risorse**.  
  
    > [!NOTE]  
    >  Assicurarsi di aggiungere il file di risorse a un elemento di progetto SharePoint in modo che sia disponibile la proprietà Tipo distribuzione.  Questa proprietà viene richiesta in un secondo momento nella procedura.  
  
2.  Assegnare al file di risorse della lingua predefinita un nome di propria scelta con estensione resx, ad esempio MyAppResources.resx.  
  
3.  Ripetere i passaggi 1 e 2 per aggiungere file di risorse separati all'elemento di progetto SharePoint, uno per ogni lingua localizzata.  
  
     Utilizzare lo stesso nome base per ogni file di risorse localizzato, ma aggiungere l'ID delle impostazioni cultura.  Assegnare, ad esempio, a una risorsa localizzata in tedesco il nome MyAppResources.de\-DE.resx.  
  
4.  Aprire ogni file di risorse e aggiungere stringhe localizzate.  Utilizzare lo stesso ID stringa in ogni file.  
  
5.  Cambiare il valore della proprietà **Tipo distribuzione** di ogni file di risorse su **AppGlobalResource** per fare in modo che ogni file venga distribuito nella cartella App\_GlobalResources del server.  
  
6.  Lasciare il valore della proprietà **Operazione di compilazione** di ogni file su **Risorsa incorporata**.  
  
     Le risorse incorporate vengono compilate nella DLL del progetto.  
  
7.  Compilare il progetto in modo da creare le DLL satellite delle risorse.  
  
8.  In **Progettazione pacchetti** scegliere la scheda **Avanzate** e aggiungere l'assembly satellite.  
  
9. Nella casella **Percorso** anteporre una cartella con l'ID delle impostazioni cultura al percorso, ad esempio de\-DE\\*Project Item Name*.resources.dll.  
  
10. Se la soluzione non fa già riferimento all'assembly System.Web, aggiungere tale riferimento e inserire nel codice una direttiva a <xref:System.Web>.  
  
11. Individuare tutte le stringhe hardcoded nel codice visibili agli utenti, ad esempio il testo dell'interfaccia utente, errori e testo del messaggio.  Sostituirle con una chiamata al metodo <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> utilizzando la sintassi seguente:  
  
    ```  
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")  
    ```  
  
12. Premere il tasto F5 per compilare ed eseguire l'applicazione.  
  
13. In SharePoint modificare la lingua di visualizzazione predefinita.  
  
     Nell'applicazione verranno visualizzate le stringhe localizzate.  Per la visualizzazione delle risorse localizzate, è necessario che nel server SharePoint sia installato un Language Pack corrispondente alle impostazioni cultura del file di risorse.  
  
## Vedere anche  
 [Localizzazione di soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)   
 [Procedura: localizzare una funzionalità](../sharepoint/how-to-localize-a-feature.md)   
 [Procedura: localizzare il markup ASPX](../sharepoint/how-to-localize-aspx-markup.md)   
 [Procedura: aggiungere un file di risorse](../sharepoint/how-to-add-a-resource-file.md)  
  
  