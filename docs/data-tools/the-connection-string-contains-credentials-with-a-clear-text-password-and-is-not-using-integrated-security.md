---
title: "La stringa di connessione contiene credenziali con una password in testo non crittografato e non utilizza la sicurezza integrata | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 501d85af-92e0-4471-b280-8a59c0688575
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# La stringa di connessione contiene credenziali con una password in testo non crittografato e non utilizza la sicurezza integrata
Salvare la stringa di connessione nel file DBML corrente e i file di configurazione dell'applicazione con queste informazioni riservate?Fare clic su No per salvare la stringa di connessione senza le informazioni riservate.  
  
 Quando si utilizzano connessioni dati in cui sono contenute informazioni riservate, ad esempio le password incluse nella stringa di connessione, è possibile salvare la stringa di connessione nel file DBML di un progetto e il file di configurazione dell'applicazione con o senza le informazioni riservate.  
  
> [!WARNING]
>  Se si imposta in modo esplicito la proprietà **Impostazioni applicazione** presente nelle proprietà **Connessione** su **False**, la password verrà aggiunta nel file DBML.  
  
### Per salvare la stringa di connessione con le informazioni riservate nelle impostazioni dell'applicazione del progetto  
  
-   Scegliere **Sì**.  
  
     La stringa di connessione viene archiviata come impostazione dell'applicazionee include le informazioni riservate in testo normale.Il file DBML non contiene le informazioni riservate.  
  
### Per salvare la stringa di connessione senza le informazioni riservate nelle impostazioni dell'applicazione del progetto  
  
-   Scegliere **No**.  
  
     La stringa di connessione viene archiviata come impostazione dell'applicazione, ma non viene inclusa la password.  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)