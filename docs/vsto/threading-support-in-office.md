---
title: "Supporto del threading in Office"
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
  - "più thread [sviluppo per Office in Visual Studio]"
  - "modelli a oggetti [sviluppo per Office in Visual Studio], supporto del threading"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], supporto del threading"
  - "threading [sviluppo per Office in Visual Studio]"
ms.assetid: 810a6648-fece-4b43-9eb6-948d28ed2157
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Supporto del threading in Office
  In questo argomento vengono fornite informazioni sul supporto del threading nel modello a oggetti di Microsoft Office.  Il modello a oggetti di Office non è thread\-safe, ma è possibile utilizzare più thread in una soluzione Office.  Le applicazioni Office sono server COM \(Component Object Model\);  i COM consentono ai client di chiamare server COM con thread arbitrari.  Per i server COM che non sono thread\-safe, il COM fornisce un meccanismo che consente di serializzare le chiamate simultanee, in modo che nel server venga eseguito un solo thread logico alla volta.  Questo meccanismo è noto come modello STA \(Single\-Threaded Apartment, apartment a thread singolo\).  Dal momento che le chiamate vengono serializzate, è possibile che i chiamanti vengano bloccati negli intervalli di tempo in cui il server è occupato o sta gestendo altre chiamate su un thread in background.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Conoscenza necessaria per l'utilizzo di più thread  
 Per utilizzare più thread, è necessario possedere almeno una conoscenza di base dei seguenti aspetti del multithreading:  
  
-   API di Windows  
  
-   Concetti COM a più thread  
  
-   Concorrenza  
  
-   Sincronizzazione  
  
-   Marshalling  
  
 Per informazioni generali sul multithreading, vedere [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779).  
  
 Office viene eseguito nell'STA primario.  Capire le implicazioni di tale fenomeno consente di capire come utilizzare più thread con Office.  
  
## Scenario multithreading di base  
 Il codice nelle soluzioni Office viene sempre eseguito nel thread primario dell'interfaccia utente.  Si potrebbe desiderare di ottimizzare le prestazioni dell'applicazione eseguendo un'attività separata su un thread in background.  Lo scopo di questa operazione è di completare idealmente due attività contemporaneamente anziché una dopo l'altra, consentendo una migliore esecuzione, ragione principale per l'utilizzo di più thread.  È possibile ad esempio che il codice eventi si trovi sul thread primario dell'interfaccia utente di Excel, mentre sul thread in background viene eseguita un'attività che raccoglie dati da un server e aggiorna le celle nell'interfaccia utente di Excel con i dati provenienti dal server.  
  
## Thread in background che effettuano chiamate al modello a oggetti di Office  
 Quando un thread in background effettua una chiamata all'applicazione di Office, viene effettuato automaticamente il marshalling della chiamata oltre i limiti del thread STA.  Tuttavia, non è garantito che l'applicazione di Office sia in grado di gestire la chiamata nel momento in cui questa viene effettuata dal thread in background.  Esistono numerose possibilità:  
  
1.  È necessario che l'applicazione di Office distribuisca i messaggi perché la chiamata abbia la possibilità di arrivare.  Se l'applicazione esegue un'elaborazione impegnativa senza cedere le chiamate, il procedimento può richiedere più tempo.  
  
2.  Se un altro thread logico è già nell'apartment, il nuovo thread non può entrare.  In genere ciò si verifica quando un thread logico entra nell'applicazione di Office e quindi esegue una chiamata rientrante all'apartment del chiamante.  L'applicazione viene bloccata in attesa del risultato della chiamata.  
  
3.  Excel può trovarsi in uno stato che non consente la gestione immediata di una chiamata in entrata;  ad esempio, è possibile che l'applicazione di Office visualizzi una finestra di dialogo modale.  
  
 Per le possibilità 2 e 3, COM fornisce l'interfaccia [IMessageFilter](http://msdn.microsoft.com/it-it/e12d48c0-5033-47a8-bdcd-e94c49857248).  Se il server la implementa, tutte le chiamate entrano utilizzando il metodo [HandleIncomingCall](http://msdn.microsoft.com/it-it/7e31b518-ef4f-4bdd-b5c7-e1b16383a5be).  Per la possibilità 2, le chiamate vengono rifiutate automaticamente.  Per la possibilità 3, il server può rifiutare la chiamata a seconda delle circostanze.  Se la chiamata viene rifiutata, il chiamante deve decidere cosa fare.  In genere il chiamante implementa l'interfaccia [IMessageFilter](http://msdn.microsoft.com/it-it/e12d48c0-5033-47a8-bdcd-e94c49857248), nel qual caso il rifiuto verrebbe notificato dal metodo [RetryRejectedCall](http://msdn.microsoft.com/it-it/3f800819-2a21-4e46-ad15-f9594fac1a3d).  
  
 Tuttavia, nel caso di soluzioni create tramite gli strumenti di sviluppo di Office in Visual Studio, l'interoperabilità COM converte tutte le chiamate respinte in un <xref:System.Runtime.InteropServices.COMException> \("Il filtro messaggi ha indicato che l'applicazione è impegnata"\).  Quando si esegue una chiamata relativa al modello a oggetti su un thread in background, è necessario essere pronti a gestire questa eccezione.  In genere, significa riprovare per un certo intervallo di tempo per poi visualizzare una finestra di dialogo.  Tuttavia, è anche possibile creare il thread in background come STA e successivamente registrare un filtro di messaggio perché tale thread gestisca questo caso.  
  
## Avvio del thread in modo corretto  
 Quando si crea un nuovo thread STA, è necessario impostare lo stato di apartment su STA prima dell'avvio del thread.  Nell'esempio di codice riportato di seguito viene illustrato come procedere.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/ThisWorkbook.vb#5)]  
  
 Per ulteriori informazioni, vedere [Managed Threading Best Practices](http://msdn.microsoft.com/library/e51988e7-7f4b-4646-a06d-1416cee8d557).  
  
## Form non modali  
 Un form non modale consente un certo tipo di interazione con l'applicazione durante la visualizzazione del form.  L'utente interagisce con il form e quest'ultimo interagisce con l'applicazione senza chiudersi.  Benché il modello a oggetti di Office supporti i form non modali gestiti, è consigliabile evitarne l'uso nei thread in background.  
  
## Vedere anche  
 [Multithreading in Components](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)   
 [Managed Threading](http://msdn.microsoft.com/library/7b46a7d9-c6f1-46d1-a947-ae97471bba87)   
 [Threading &#40;C&#35; e Visual Basic&#41;](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)   
 [Using Threads and Threading](http://msdn.microsoft.com/library/9b5ec2cd-121b-4d49-b075-222cf26f2344)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  