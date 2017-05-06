---
title: "Cenni preliminari sull&#39;utilizzo di file di un database locale nelle soluzioni Office"
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
helpviewer_keywords: 
  - "dati [sviluppo per Office in Visual Studio], locali"
  - "dati locali [sviluppo per Office in Visual Studio]"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], dati"
ms.assetid: 7a920e6b-f0c3-4a62-b5dd-02668a6177b6
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Cenni preliminari sull&#39;utilizzo di file di un database locale nelle soluzioni Office
  È possibile includere un file di database, ad esempio un file di SQL Server Express \(con estensione mdf\) o di Microsoft Office Access \(mdb\), nella soluzione Office.  In questo modo, gli utenti finali possono gestire un database locale nelle situazioni in cui non è richiesta la gestione di un database centralizzato, ad esempio in una soluzione di inventario locale utilizzata solo in un singolo computer.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Importazione del file di database in un progetto  
 Per importare il file di database nel progetto, utilizzare la **Configurazione guidata origine dati** per creare un'origine dati basata sul file di database.  La procedura guidata consente di aggiungere al progetto il file di database e un DataSet tipizzato.  
  
## Distribuzione del file di database  
 La **Configurazione guidata origine dati** utilizza un percorso relativo per creare connessioni al file di database locale.  Se si gestiscono i percorsi relativi dei file, ciò consente di copiare la soluzione da un computer a un altro.  
  
 Se si distribuisce la soluzione a un server e quindi si distribuisce il documento a ogni utente finale, è necessario distribuire manualmente anche il file di database e quindi installarlo nello stesso percorso relativo del documento.  Ciò significa che l'utente finale non potrà spostare il documento in un nuovo percorso sul computer se non sposta anche il file di database.  
  
## File di database locali e memorizzazione del DataSet nella cache  
 Nelle soluzioni a livello di documento di Microsoft Office Excel e Microsoft Office Word, è possibile memorizzare nella cache dataset contenuti nel documento contrassegnando l'istanza del dataset con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  Quando si aggiunge il file di database al progetto mediante la **Configurazione guidata origine dati**, verrà aggiunto automaticamente anche un dataset tipizzato.  Poiché i dati sono già locali nel computer dell'utente, l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> deve essere applicato a questo dataset solo in rari casi.  Per ulteriori informazioni, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md).  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [Procedura: popolare documenti con dati da un database](../vsto/how-to-populate-documents-with-data-from-a-database.md)   
 [Procedura: Aggiornare un'origine dati con i dati inviati da un controllo host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Memorizzazione di dati nella cache](../vsto/caching-data.md)  
  
  