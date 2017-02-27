---
title: "Decisioni di progettazione di tipo di progetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipi di progetto, la persistenza del file di progetto"
  - "tipi di progetto, i meccanismi di impegno"
  - "tipi di progetto, gli elementi"
  - "tipi di progetto, le decisioni di progettazione"
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Decisioni di progettazione di tipo di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Prima di creare un nuovo tipo di progetto, è necessario eseguire molte decisioni di progettazione relative al tipo di progetto.  È necessario decidere quale tipo elementi dei progetti conterranno, ad esempio i file di progetto vengono salvati in modo permanente e il modello di impegno utilizzare.  
  
## elementi di progetto  
 il progetto utilizzerà i file o gli oggetti astratti?  Se si utilizzano i file, saranno a file basati su riferimento o basati su directory?  I file o gli oggetti astratti utilizzeranno essere locali o remoti?  
  
 Gli elementi di un progetto possono essere file, oppure possono essere oggetti più astratti come gli oggetti in un repository del database o connessioni dati tramite internet.  Se gli elementi sono file, il progetto può essere a un progetto basato su riferimento o basato su directory.  
  
 Nei progetti basati su riferimento, gli elementi possono essere visualizzati in più progetti.  Tuttavia, il file effettivo di un elemento rappresenta si trova in una directory solo.  Nei progetti basati su directory, tutti gli elementi di progetto esistenti nella struttura di directory.  Per ulteriori informazioni, vedere [NIB:Item Management in Projects](http://msdn.microsoft.com/it-it/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 Gli elementi locali vengono archiviati nello stesso computer in cui è installata l'applicazione.  Gli elementi remoti possono essere archiviati in un server separato in una rete locale, o in internet.  
  
## Persistenza del file di progetto  
 I dati verranno file system piani in comune archiviati, o in un archivio strutturato?  I file verranno aperti utilizzando un editor standard, o un editor specifico del progetto?  
  
 Per salvare in modo permanente i dati, la maggior parte delle applicazioni salvano i dati in un file e quindi la lettura di quando un utente deve esaminare o modificare le informazioni.  
  
 Un'archiviazione strutturata, denominato anche file composita, in genere viene utilizzata quando vari oggetti \(COM\) COM devono memorizzare i dati persistenti in un singolo file.  Con archiviazione strutturata, vari componenti software possono condividere un singolo file su disco.  
  
 Sono disponibili svariate opzioni da considerare la possibilità di esaminare la persistenza per gli elementi del progetto.  È possibile eseguire una delle opzioni seguenti:  
  
-   salvare individualmente ogni file quando è stato modificato.  
  
-   Acquisire più transazioni in una singola operazione di **Salvare** .  
  
-   Salvare i file in locale e quindi pubblicazione in un server o utilizzare un altro approccio agli elementi del progetto di salvataggio quando l'elemento rappresenta una connessione dati a un oggetto remoto.  
  
 Per ulteriori informazioni sulla persistenza, vedere [Persistenza del progetto](../../extensibility/internals/project-persistence.md) e [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
## proiettare il modello di impegno  
 Gli oggetti dati persistenti verranno aperti in modalità diretta o nella modalità transazionale?  
  
 Quando gli oggetti dati sono aperti in modalità diretta, le modifiche apportate ai dati sono incluse immediatamente o quando l'utente manualmente salvare il file.  
  
 Quando gli oggetti dati vengono aperti utilizzando la modalità transazionale, le modifiche vengono salvate in un percorso temporaneo in memoria e non applicate finché l'utente manualmente non potrà scegliere per salvare il file.  In quel momento, tutte le modifiche dovranno verificarsi raccolta o non verrà apportata alcuna modifica.  
  
## Vedere anche  
 [Elenco di controllo: Creazione di nuovi tipi di progetto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [NIB:Item Management in Projects](http://msdn.microsoft.com/it-it/762e606b-7f44-4b66-97a1-e30a703654a0)   
 [Apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md)   
 [Persistenza del progetto](../../extensibility/internals/project-persistence.md)   
 [Elementi di un modello di progetto](../../extensibility/internals/elements-of-a-project-model.md)   
 [Componenti di base del modello di progetto](../../extensibility/internals/project-model-core-components.md)   
 [Creazione di tipi di progetto](../../extensibility/internals/creating-project-types.md)