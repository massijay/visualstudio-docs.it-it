---
title: "Verifica e debug del codice di SharePoint | Microsoft Docs"
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
  - "unit test [sviluppo per SharePoint in Visual Studio]"
  - "IntelliTrace [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, IntelliTrace"
  - "sviluppo per SharePoint in Visual Studio, testing unità"
ms.assetid: b5f3bce2-6a51-41b1-a292-9e384bae420c
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Verifica e debug del codice di SharePoint
  L'utilizzo di IntelliTrace e di unit test consente di eseguire più facilmente il debug delle soluzioni SharePoint nonché di assicurare il corretto funzionamento di ogni singolo metodo nell'applicazione.  È possibile utilizzare queste funzionalità per i progetti SharePoint in [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] seguendo le stesse procedere utilizzate per altri tipi di progetti.  
  
## IntelliTrace  
 IntelliTrace consente di determinare non solo lo stato corrente della soluzione SharePoint, ma anche eventi generati in passato e il contesto in cui si sono verificati.  È possibile scorrere i diversi momenti della soluzione SharePoint in cui sono stati registrati eventi di interesse, esaminando gli stati e i valori delle variabili in ogni punto.  Tramite questa navigazione dinamica, il debug delle soluzioni SharePoint è più facile e rapido, senza la necessità di impostare numerosi punti di interruzione.  È possibile salvare la sessione di debug in un file di log IntelliTrace \(.iTrace\), aprirlo successivamente in Visual Studio Ultimate ed eseguire il debug del post\-arresto anomalo.  Il file .iTrace include informazioni dettagliate su quando e dove gli errori specifici di SharePoint si sono verificati, in modo che sia possibile comprendere cosa stia provocando gli errori.  L'informazione contenuta nel file .iTrace è un sottoinsieme del log completo degli errori creato dall'Unified Logging System \(ULS\) in SharePoint.  Queste informazioni includono eventi specifici per SharePoint, ad esempio quando un profilo utente viene aperto o chiuso e le proprietà in un progetto SharePoint vengono caricate, lette, o modificate.  È possibile stabilire quali eventi IntelliTrace registri.  Per ulteriori informazioni, vedere [Uso dei dati di IntelliTrace salvati](../debugger/using-saved-intellitrace-data.md) e [Configurare IntelliTrace per raccogliere informazioni di debug](http://msdn.microsoft.com/it-it/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
 Quando si verifica un errore in SharePoint, la finestra di dialogo di errore visualizza un identificatore "ID di correlazione" per tale errore specifico.  È inoltre possibile ottenere gli ID di correlazione dagli eventi elencati nel file .iTrace.  Per visualizzare un elenco di tutti gli eventi che si sono verificati con il dato ID di correlazione, è possibile fornire l'ID nella sezione **Analisi** della pagina di riepilogo di IntelliTrace.  In questa sezione, è possibile scegliere se visualizzare solo i nomi degli eventi che si sono verificati o i nomi degli eventi con le informazioni sulle chiamate, ad esempio il nome della funzione, uscite e i punti di ingresso, parametri e valori restituiti.  
  
 È possibile ottenere gli eventi di Visual Studio in IntelliTrace premendo il tasto **F5**.  Per ottenere gli eventi specifici di SharePoint, tuttavia, è necessario raccogliere dati IntelliTrace nelle soluzioni SharePoint tramite Microsoft Monitoring Agent.  Questo strumento raccoglie dati IntelliTrace e crea i file .iTrace per le applicazioni distribuite all'esterno di Visual Studio.  Per ulteriori informazioni, vedere [Funzionalità di IntelliTrace](../debugger/intellitrace-features.md) e [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
## Unit test  
 È possibile individuare più facilmente errori nel codice eseguendo unit test in cui viene scritto ed eseguito il codice di test all'interno di metodi di test.  In questi metodi sono contenute variabili vuote e un'istruzione Assert che è possibile utilizzare per verificare la logica e la funzionalità del progetto in base al modello a oggetti di SharePoint.  Per ulteriori informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).  
  
### Supporto per framework Microsoft Fakes  
 I progetti SharePoint supportano Microsoft Fakes, che è un framework di isolamento in cui è possibile creare test stub basati su delegati e unirli alle applicazioni basate su .NET Framework.  Utilizzando il framework Fakes, è possibile creare, gestire e inserire implementazioni fittizie negli unit test.  Tali shim e stub isolano gli unit test dall'ambiente.  È possibile creare stub per testare il codice che contiene interfacce o classi non\-sealed con i metodi sottoponibili a override.  È possibile creare gli shim per reindirizzare le chiamate hardcoded a classi sealed con metodi statici o non sottoponibili a override in un'implementazione alternativa shim.  È inoltre possibile usare i delegati con i tipi stub che coni tipi shim per personalizzare dinamicamente il comportamento dei singoli membri dello stub.  Per ulteriori informazioni, vedere [Isolamento del codice sottoposto a test con Microsoft Fakes](../test/isolating-code-under-test-with-microsoft-fakes.md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Utilizzo di IntelliTrace](../debugger/intellitrace.md)|Viene descritto come eseguire più facilmente il debug delle soluzioni di Visual Studio utilizzando IntelliTrace.|  
|[Procedura dettagliata: debug di un'applicazione di SharePoint tramite IntelliTrace](../sharepoint/walkthrough-debugging-a-sharepoint-application-by-using-intellitrace.md)|Viene illustrato come utilizzare IntelliTrace per individuare errori di codice in un progetto SharePoint.|  
|[Eseguire unit test del codice](../test/unit-test-your-code.md)|Viene descritto come individuare errori logici nel codice utilizzando gli unit test.|  
  
## Vedere anche  
 [Migliorare la qualità del codice](../test/improve-code-quality.md)  
  
  