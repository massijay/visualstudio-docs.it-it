---
title: "Linee guida per la manutenzione per applicazioni Shell isolata | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio Shell la modalità integrata, facilità di manutenzione"
  - "Modalità integrata shell [Visual Studio], facilità di manutenzione"
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Linee guida per la manutenzione per applicazioni Shell isolata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si distribuisce un'applicazione di shell di Visual Studio isolato, è necessario essere in grado di fornire gli aggiornamenti software per l'applicazione dopo l'installazione. A tale scopo, è necessario installare l'applicazione utilizzando un file di Microsoft Installer \(MSI\). Questo tipo di installazione consente gli aggiornamenti software forniti da Microsoft per essere ridistribuito da Web scaricare e utilizzato dai clienti senza l'intervento personalizzato.  
  
## I requisiti di manutenzione  
 È possibile garantire che l'installazione di shell isolata può consentire gli aggiornamenti, verificare che il programma di installazione soddisfi i seguenti tre criteri.  
  
### Ridistribuire utilizzando un file MSI  
 È necessario utilizzare un file MSI per ridistribuire l'applicazione, poiché un file MSI del prodotto identità viene mantenuta e verificare che l'applicazione dispone di una posizione fisica del computer client. I moduli unione \(file MSM\) non forniscono tali garanzie e non devono essere utilizzati.  
  
### Tenuto conto delle azioni personalizzate  
 Azioni personalizzate sono direttive di installazione non standard in un programma di installazione. Azioni personalizzate modificare parametri quali percorsi dei file, impostazioni del Registro di sistema, le impostazioni utente o altri elementi di installazione. Azioni personalizzate possono modificare i dati al momento dell'installazione.  
  
 Quando si utilizzano azioni personalizzate in un programma di installazione, è necessario assicurarsi che ogni azione personalizzata in fase di installazione deve disporre di un'azione personalizzata corrispondente per annullare l'azione quando l'utente Disinstalla l'applicazione. Se i programma di installazione non riesce a fornire corrispondente Disinstalla azione personalizzata, la rimozione dell'applicazione verrà lasciarlo installato parzialmente.  
  
-   Un'azione personalizzata che si basa su una versione specifica di un file o hash valori avrà esito negativo durante gli aggiornamenti software modificare queste versioni o valori hash. In questo caso l'azione personalizzata è necessario aggiornare manualmente questi valori. Se le versioni di un file o hash i valori vengono condivisi tra versioni del prodotto, si verifica un problema aggiuntivo. Evitare questa dipendenza laddove possibile.  
  
### Tenendo conto dei file condivisi  
 File condivisi con gli stessi nomi e vengono installati nello stesso percorso per più prodotti. Questi prodotti possono variare in versione, Stock mantenendo Unit \(SKU\) o entrambi, e i prodotti possono coesistere in un determinato computer. Tuttavia, i file condivisi creano problemi di manutenzione per diversi motivi:  
  
-   L'aggiornamento di file condivisi può causare problemi di compatibilità perché un aggiornamento a un'applicazione può modificare la versione di un file utilizzato da una seconda applicazione che non è stata aggiornata. Programmi di installazione per i prodotti che condividono i file di conteggio dei riferimenti ai file condivisi. Pertanto, la disinstallazione di un prodotto non influenza i file condivisi oltre la riduzione del conteggio delle istanze installate.  
  
-   Il programma di installazione Quick Fix Engineering \(QFE\) vengono ripristinate le versioni dei file per le versioni dei prodotti che ha gestito il programma di installazione QFE. Questo processo si interrompe potenzialmente un'applicazione che ha recapitato un file condiviso aggiornato.