---
title: "Procedura: specificare percorsi dei file di simboli tramite la riga di comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8aa067bb-e8bf-4081-aff0-cfbcf65934a0
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: specificare percorsi dei file di simboli tramite la riga di comando
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per visualizzare informazioni sui simboli quali i nomi della funzione e i numeri di riga, nello strumento della riga di comando VSPerfReport è necessario disporre di accesso ai file di simboli \(con estensione pdb\) dei componenti profilati e ai file di sistema di Windows.  I file di simboli vengono creati quando viene compilato un componente.  Per ulteriori informazioni, vedere [VSPerfReport](../profiling/vsperfreport.md).  VSPerfReport esegue automaticamente la ricerca dei file di simboli nei percorsi seguenti:  
  
-   Percorsi specificati nell'opzione **\/SymbolPath** o nella variabile di ambiente **\_NT\_SYMBOL\_PATH**.  
  
-   Percorso locale esatto in cui è stato compilato un componente.  
  
-   Directory che contiene il file di dati del profilo \(con estensione vsp o vsps\).  
  
 Microsoft fornisce i file con estensione pdb per molti prodotti online in un server di simboli.  Se il computer utilizzato per la generazione di rapporti è connesso a Internet, VSPerfReport si connette al server di simboli online per cercare automaticamente informazioni sui simboli e salvare i file in un archivio locale.  
  
 È possibile specificare il percorso dei file di simboli e l'archivio del server di simboli Microsoft nei modi seguenti:  
  
-   Impostare la variabile di ambiente **\_NT\_SYMBOL\_PATH**.  
  
-   Aggiungere l'opzione **\/SymbolPath** alla riga di comando VSPerfReport.  
  
 È inoltre possibile utilizzare entrambi i metodi.  
  
> [!NOTE]
>  Se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è installato nel computer locale, probabilmente è già stato specificato un percorso per i file di simboli Windows.  Per ulteriori informazioni, vedere [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md).  È comunque necessario configurare VSPerfReport per utilizzare la posizione e il server come viene descritto più avanti in questo argomento.  
  
## Specifica di file di simboli Windows  
  
#### Per configurare l'utilizzo del server di simboli Windows  
  
1.  Se necessario, creare una directory per archiviare in locale i file di simboli.  
  
2.  Utilizzare la sintassi seguente per impostare la variabile di ambiente **\_NT\_SYMBOL\_PATH** o l'opzione VSPerfReport \/SymbolPath:  
  
     **srv\*** *LocalStore* **\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
     dove *LocalStore* è il percorso della directory locale creata.  
  
## Specifica di file di simboli dei componenti  
 Gli strumenti di profilatura effettuano la ricerca di file con estensione pdb dei componenti da profilare nei percorsi originali archiviati nei componenti o nella cartella che contiene il file di dati del profilo.  È possibile specificare altri percorsi da cercare aggiungendo uno o più percorsi a **\_NT\_SYMBOL\_PATH** o all'opzione **\/SymbolPath**.  Separare i percorsi con punti e virgola.  
  
## Esempio  
 La riga di comando seguente imposta la variabile di ambiente **\_NT\_SYMBOL\_PATH** sul server di simboli Windows e la directory locale su **C:\\Symbols**.  
  
 **set  \_NT\_SYMBOL\_PATH\=srv\*C:\\symbols\*http:\/\/msdl.microsoft.com\/downloads\/symbols**  
  
 La riga di comando VSPerfReport seguente aggiunge la directory C:\\Projects\\Symbols al percorso di ricerca tramite l'opzione **\/SymbolPath**.  
  
 **VSPerfReport**  *MyApp* **.exe \/SymbolPath:C:\\Projects\\Symbols \/summary:all**