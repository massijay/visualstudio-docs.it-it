---
title: "Sviluppo collaborativo di soluzioni Office | Microsoft Docs"
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
  - "sviluppo collaborativo [sviluppo per Office in Visual Studio]"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], sviluppo collaborativo"
  - "sviluppo per Office in Visual Studio, collaborazione"
  - "controllo del codice sorgente [sviluppo per Office in Visual Studio]"
ms.assetid: c493354b-17d3-4e50-85f0-968b104bc978
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Sviluppo collaborativo di soluzioni Office
  Più sviluppatori possono lavorare su un progetto di Office allo stesso modo in cui collaborano sugli altri progetti di Visual Studio.  Visual Studio è in grado di individuare correttamente l'installazione di Microsoft Office su ogni computer, anche se Office è installato in percorsi diversi.  È tuttavia importante essere consapevoli di alcuni problemi.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Le proprietà di debug non sono condivise  
 Le proprietà di debug non sono condivise tra più utenti sotto il controllo del codice sorgente.  Nei progetti di Visual Basic e Visual C\# le proprietà di debug vengono memorizzate in un file specifico dell'utente \(*NomeProgetto*.vbproj.user o *NomeProgetto*.csproj.user\). Tale file non è incluso nel controllo del codice sorgente.  Se più di un utente esegue il debug, è necessario che ciascuno immetta manualmente le proprietà di debug.  
  
 Se il progetto è contenuto in una condivisione di rete anziché in un controllo del codice sorgente, è necessario effettuare più passaggi per consentire agli sviluppatori che lavorano in collaborazione di aprire la soluzione e testare l'assembly.  
  
## Il controllo del codice sorgente richiede l'estrazione di tutti i file  
 Se per i progetti si utilizza il controllo del codice sorgente, è necessario estrarre tutti i file in un file di codice in **Esplora soluzioni** \(ad esempio, i file di codice ThisDocument, ThisWorkbook o ThisAddIn\) ogni volta che si modifica il file di codice, inclusi i file nascosti per impostazione predefinita.  Se si estrae solo il file di codice di livello superiore, le modifiche potrebbero andare perse.  
  
 Dopo avere apportato le modifiche, archiviare nuovamente tutti i file.  Per ulteriori informazioni sui file di codice nascosti nei progetti, vedere [Progetti di Office in ambiente Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## Sicurezza per la collaborazione informale in una rete  
 Per tutte le soluzioni a livello di documento situate in un percorso di rete \(ad esempio \\\\*NomeServer*\\*NomeCondivisione*\), occorre aggiungere il percorso completo all'elenco delle cartelle attendibili nell'applicazione Microsoft Office in uso.  Selezionare l'opzione che consente di includere le sottodirectory della cartella principale o aggiungere specificamente le cartelle di debug e compilazione all'elenco delle cartelle attendibili.  Per ulteriori informazioni su tale procedura, vedere [Concessione dell'attendibilità ai documenti](../vsto/granting-trust-to-documents.md).  
  
 I certificati temporanei generati automaticamente in fase di compilazione non sono protetti da password.  I certificati contengono il nome di accesso dello sviluppatore e altre informazioni personali.  Se si distribuiscono le personalizzazioni firmate mediante certificati temporanei, gli altri utenti potrebbero accedere a tali informazioni.  
  
## Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Compilazione di soluzioni Office](../vsto/building-office-solutions.md)  
  
  