---
title: "The Text Template Transformation Process | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, transformation process"
ms.assetid: 80b3f0e0-49e7-4865-a1ac-dba068abe96b
caps.latest.revision: 30
caps.handback.revision: 30
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# The Text Template Transformation Process
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il processo di trasformazione del modello di testo prende un file modello di testo come input e genera un nuovo file di testo come output.  Ad esempio, è possibile utilizzare modelli di testo per generare codice Visual Basic o C\# o è possibile generare un rapporto HTML.  
  
 Tre componenti prendono parte a questo processo: il motore, l'host e i processori di direttive.  Il motore controlla il processo; interagisce con l'host e il processore di direttiva per produrre il file di output.  L'host fornisce qualsiasi interazione l'ambiente, ad esempio individua i file e gli assembly.  Il processore di direttiva aggiunge funzionalità, ad esempio la lettura di dati da un file XML o un database.  
  
 Il processo di trasformazione del modello di testo viene eseguito in due passaggi.  Nel primo passaggio, il motore crea una classe temporanea che è nota come la classe della trasformazione generata.  Questa classe contiene il codice generato dalle direttive e dai blocchi di controllo.  Nel secondo passaggio, il motore compila ed esegue la classe della trasformazione generata per produrre il file di output.  
  
## Componenti  
  
|Componente|Descrizione|Personalizzabile \(sì\/no\)|  
|----------------|-----------------|---------------------------------|  
|Motore|Il componente motore controlla il processo di trasformazione del modello di testo|No.|  
|Host|L'host è l'interfaccia tra il motore e l'ambiente utente.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è un host del processo di trasformazione di testo.|Sì.  È possibile scrivere un host personalizzato.|  
|Processori di direttive|I processori di direttive sono classi che gestiscono direttive nei modelli di testo.  È possibile utilizzare direttive per fornire dati a un modello di testo da un'origine di input.|Sì.  È possibile scrivere processori di direttive personalizzati|  
  
## Motore  
 Il motore riceve il modello come stringa dall'host, che gestisce tutti i file utilizzati nel processo di trasformazione.  Il motore chiede quindi all'host di individuare i processori di direttive personalizzati e altri aspetti dell'ambiente,  quindi compila ed esegue la classe della trasformazione generata.  Il motore restituisce il testo generato all'host, che generalmente salva il testo in un file.  
  
## Host  
 L'host è responsabile di tutto ciò che è correlato all'ambiente al di fuori del processo di trasformazione, incluso quanto segue:  
  
-   Individuazione file di testo e binari richiesti dal motore o da un processore di direttiva.  L'host può eseguire ricerche nelle directory e nella Global Assembly Cache per individuare degli assembly.  L'host può individuare codice del processore di direttiva personalizzato per il motore.  L'host può inoltre individuare e leggere file di testo e può restituirne il contenuto come stringhe.  
  
-   Fornire elenchi di assembly e spazi dei nomi standard utilizzati dal motore per creare la classe della trasformazione generata.  
  
-   Fornire il dominio dell'applicazione utilizzato quando il motore compila ed esegue la classe della trasformazione generata.  Un dominio di applicazione separato è utilizzato per proteggere l'applicazione host da errori nel codice del modello.  
  
-   Scrittura del file di output generato.  
  
-   Impostazione dell'estensione predefinita per il file di output generato.  
  
-   Gestione degli errori della trasformazione del modello di testo.  Ad esempio, l'host può visualizzare gli errori nell'interfaccia utente o può scriverli in un file.  In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gli errori vengono visualizzati nella Finestra di messaggio di errore.  
  
-   Fornire un valore di parametro obbligatorio se un utente ha chiamato una direttiva senza fornire un valore.  Il processore di direttiva può specificare il nome della direttiva e il parametro e può chiedere all'host di fornire un valore predefinito se disponibile.  
  
## Direttive e processori di direttive  
 Una direttiva è un comando nel modello di testo.  Fornisce parametri al processo di generazione.  In genere, le direttive definiscono l'origine e il tipo del modello o altro input e l'estensione del file di output.  
  
 Un processore di direttiva può elaborare una o più direttive.  Quando si trasforma un modello, è necessario avere installato un processore di direttiva che può gestire le direttive nel modello.  
  
 Le direttive funzionano aggiungendo codice nella classe della trasformazione generata.  Si chiamano direttive da un modello di testo e il motore elabora tutte le chiamate alle direttive quando crea la classe della trasformazione generata.  Dopo avere chiamato correttamente una direttiva, il resto del codice che si scrive nel modello di testo può basarsi sulla funzionalità che la direttiva fornisce.  Ad esempio, è possibile effettuare la seguente chiamata alla direttiva `import` nel modello:  
  
 `<#@ import namespace="System.Text" #>`  
  
 Il processore di direttiva standard converte questa in un'istruzione `using` nella classe della trasformazione generata.  È quindi possibile utilizzare la classe `StringBuilder` nel resto del codice del modello senza qualificarla come `System.Text.StringBuilder`.