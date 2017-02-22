---
title: "Comando CodeIndex | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "CodeIndex (comando) [Team Foundation Server]"
  - "strumenti della riga di comando [Team Foundation Server]"
  - "TFSConfig"
ms.assetid: b79568d4-6a64-4ca9-a1ee-3e57f92a9c5c
caps.latest.revision: 18
caps.handback.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Comando CodeIndex
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile usare il comando **CodeIndex** per gestire l'indicizzazione del codice in Team Foundation Server.  Ad esempio, è possibile che si desideri reimpostare l'indice per correggere le informazioni di CodeLens o disabilitare l'indicizzazione per esaminare eventuali problemi di prestazioni del server.  
  
 **Autorizzazioni necessarie**  
  
 Per usare il comando **CodeIndex**, è necessario essere membro del gruppo di sicurezza **Administrators di Team Foundation**.  Vedere [Permission reference for Team Foundation Server](../Topic/Permission%20reference%20for%20Team%20Foundation%20Server.md).  
  
> [!NOTE]
>  Anche se si accede con le credenziali amministrative, per eseguire questo comando, è necessario aprire una finestra del prompt dei comandi con privilegi elevati.  È inoltre necessario eseguire questo comando dal livello applicazione di Team Foundation.  
  
## Sintassi  
  
```  
TFSConfig CodeIndex /indexingStatus | /setIndexing:[ on | off | keepupOnly ] | /ignoreList:[ add | remove | removeAll | view ] ServerPath | /listLargeFiles [/fileCount:FileCount] [/minSize:MinSize] | /reindexAll | /destroyCodeIndex [/noPrompt] | /temporaryDataSizeLimit:[ view | <SizeInGBs> | disable ] | /indexHistoryPeriod:[ view | all | <NumberOfMonths> ] [/collectionName:CollectionName | /collectionId:CollectionId]  
```  
  
#### Parametri  
  
|**Argomento**|**Descrizione**|  
|-------------------|---------------------|  
|`CollectionName`|Specifica il nome della raccolta di progetti team.  Se il nome contiene spazi, racchiuderlo tra virgolette, ad esempio, "Sito Web di Fabrikam".|  
|`CollectionId`|Specifica il numero di identificazione della raccolta di progetti team.|  
|`ServerPath`|Specifica il percorso di un file di codice.|  
  
|**Opzione**|**Descrizione**|  
|-----------------|---------------------|  
|**\/indexingStatus**|Mostrare lo stato e la configurazione del servizio di indicizzazione del codice.|  
|**\/setIndexing:**\[ on &#124; off &#124; keepupOnly \]|-   **on**: avviare l'indicizzazione di tutti gli insiemi di modifiche.<br />-   **off**: arrestare l'indicizzazione di tutti gli insiemi di modifiche.<br />-   **keepupOnly**: arrestare l'indicizzazione dei set di modifiche creati in precedenza e avviare l'indicizzazione solo dei nuovi insiemi di modifiche.|  
|**\/ignoreList:**\[ add &#124; remove &#124; removeAll &#124; view \] `ServerPath`<br /><br /> È possibile usare il carattere jolly \(\*\) all'inizio, alla fine, oppure a entrambe le estremità del percorso server.|Specifica l'elenco di file di codice e i rispettivi percorsi da non indicizzare.<br /><br /> -   **add**: aggiungere il file da non indicizzare all'elenco di file ignorati.<br />-   **remove**: rimuovere il file da non indicizzare dall'elenco di file ignorati.<br />-   **removeAll**: cancellare l'elenco dei file ignorati e avviare l'indicizzazione di tutti i file.<br />-   **view**: visualizzare tutti i file non sottoposti a indicizzazione.|  
|**\/listLargeFiles \[\/fileCount:** `FileCount` **\/minSize:** `MinSize`\]|Mostra il numero specificato di file che supera la dimensione specificata in KB.  È quindi possibile usare l'opzione **\/ignoreList** per escludere questi file dall'indicizzazione.|  
|**\/reindexAll**|Cancellare i dati indicizzati in precedenza e riavviare l'indicizzazione.|  
|**\/destroyCodeIndex \[\/noPrompt\]**|Eliminare l'indice del codice e rimuovere tutti i dati indicizzati.  Non è richiesta conferma se si usa l'opzione **\/noPrompt**.|  
|**\/temporaryDataSizeLimit**:\[ view &#124; \<`SizeInGBs`\> &#124; disable \]|Controllare la quantità di dati temporanei creati da CodeLens durante l'elaborazione degli insiemi di modifiche.  Il limite predefinito è 2 GB.<br /><br /> -   **view**: mostrare il limite di dimensioni attuale.<br />-   `SizeInGBs`: modificare il limite di dimensioni.<br />-   **disable**: rimuovere il limite di dimensioni.<br /><br /> Questo limite viene verificato prima dell'elaborazione di un nuovo insieme di modifiche con CodeLens.  Se i dati temporanei superano questo limite, CodeLens sospende l'elaborazione degli insiemi di modifiche precedenti, non di quelli nuovi.  CodeLens riavvia l'elaborazione dopo che i dati sono stati puliti e sono tornati sotto il limite.  La pulizia viene eseguita automaticamente una volta al giorno.  Questo implica che i dati temporanei potrebbero superare questo limite prima dell'esecuzione del processo di pulizia.|  
|**\/indexHistoryPeriod**:\[ view &#124; all &#124; \<`NumberOfMonths`\> \]|Controllare la lunghezza dell'intervallo di indicizzazione della cronologia delle modifiche.  Ciò incide sulla quantità di cronologia che CodeLens mostra all'utente.  Il limite predefinito è di 12 mesi.  Questo significa che CodeLens mostra la cronologia delle modifiche solo degli ultimi 12 mesi.<br /><br /> -   **view**: mostrare il numero di mesi corrente.<br />-   **all**: indicizzare tutta la cronologia modifiche.<br />-   `NumberOfMonths`: modificare il numero di mesi usato per la cronologia modifiche di indice.|  
|**\/collectionName:** `CollectionName`|Specifica il nome della raccolta di progetti team sulla quale eseguire il comando **CodeIndex**.  Obbligatoria se non si usa **\/CollectionId**.|  
|**\/collectionId:** `CollectionId`|Specifica il numero di identificazione della raccolta di progetti team sulla quale eseguire il comando **CodeIndex**.  Obbligatoria se non si usa **\/CollectionName**.|  
  
## Esempi  
  
> [!NOTE]
>  Ogni riferimento a società, organizzazioni, prodotti, nomi di dominio, indirizzi di posta elettronica, logo, persone, luoghi ed eventi è puramente casuale.  Nessuna associazione con nessuna società, organizzazione, prodotto, nome di dominio, indirizzo di posta elettronica, logo, persona, luogo o evento è intenzionale o può essere presupposta.  
  
 Per vedere la configurazione e lo stato di indicizzazione del codice:  
  
```  
TFSConfig CodeIndex /indexingStatus /collectionName:"Fabrikam Web Site"  
```  
  
 Per avviare l'indicizzazione di tutti gli insiemi di modifiche:  
  
```  
TFSConfig CodeIndex /setIndexing:on /collectionName:"Fabrikam Web Site"  
```  
  
 Per arrestare l'indicizzazione dei set di modifiche creati in precedenza e avviare l'indicizzazione solo dei nuovi insiemi di modifiche:  
  
```  
TFSConfig CodeIndex /setIndexing:keepupOnly /collectionName:"Fabrikam Web Site"  
```  
  
 Per trovare fino a 50 file con dimensioni superiori a 10 KB:  
  
```  
TFSConfig CodeIndex /listLargeFiles /fileCount:50 /minSize:10 /collectionName:"Fabrikam Web Site"  
```  
  
 Per escludere un file specifico dall'indicizzazione e aggiungerlo all'elenco di file ignorati:  
  
```  
TFSConfig CodeIndex /ignoreList:add "$/Fabrikam Web Site/Catalog.cs" /collectionName:"Fabrikam Web Site"  
```  
  
 Per visualizzare tutti i file non sottoposti a indicizzazione:  
  
```  
TFSConfig CodeIndex /ignoreList:view  
```  
  
 Per cancellare i dati precedentemente indicizzati e riavviare l'indicizzazione:  
  
```  
TFSConfig CodeIndex /reindexAll /collectionName:"Fabrikam Web Site"  
```  
  
 Per salvare tutta la cronologia dell'insieme di modifiche:  
  
```  
TFSConfig CodeIndex /indexHistoryPeriod:all /collectionName:"Fabrikam Web Site"  
```  
  
 Per rimuovere il limite di dimensioni nei dati temporanei di CodeLens e continuare l'indicizzazione indipendentemente dalle dimensioni dei dati temporanei:  
  
```  
TFSConfig CodeIndex /temporaryDataSizeLimit:disable /collectionName:"Fabrikam Web Site"  
```  
  
 Per eliminare l'indice di codice con conferma:  
  
```  
TFSConfig CodeIndex /destroyCodeIndex /collectionName:"Fabrikam Web Site"  
```  
  
## Vedere anche  
 [Managing server configuration with TFSConfig](http://msdn.microsoft.com/it-it/94424190-3b6b-4f33-a6b6-5807f4225b62)   
 [Command\-line tools for TFS](http://msdn.microsoft.com/it-it/be8c997a-b97b-4e59-97f5-04db0a601a6c)