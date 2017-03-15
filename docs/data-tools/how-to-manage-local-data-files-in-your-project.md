---
title: "Procedura: gestire file di dati locali nel progetto | Microsoft Docs"
ms.custom: ""
ms.date: "09/21/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.data.LocalConnectionConverter"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - ".mdb (file)"
  - "mdf (file)"
  - "dati [Visual Studio], locali"
  - "dati locali"
  - "mdb (file)"
  - "mdf (file)"
ms.assetid: 3ffa1aa9-17e4-422c-a02f-09224828cdfc
caps.latest.revision: 29
caps.handback.revision: 27
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: gestire file di dati locali nel progetto
È possibile includere in un progetto un file di database locale come file.  Alla prima connessione dell'applicazione a un file di database locale, si può scegliere di creare una copia del database nel progetto o di eseguire la connessione al file di database esistente nella posizione corrente.  Se si decide di connettersi al file esistente, verrà creata una connessione, come se ci stesse connettendo a un database remoto, e il file di database verrà lasciato nella posizione originale.  Se invece si sceglie di copiare il database nel progetto, in Visual Studio viene creata una copia del file di database, che viene aggiunta al progetto. Ne viene quindi modificata la connessione in modo che punti al database nel progetto anziché al percorso originale del file di database.  
  
> [!NOTE]
>  Le connessioni dati esistenti in **Esplora server\/Esplora database** vengono modificate in modo che puntino anch'esse al file di database nel progetto, ovvero al file di database nella cartella radice del progetto.  
  
 Quando si compila un progetto, il file di database può essere copiato dalla cartella del progetto radice nella cartella di output \(**bin**\). Selezionare **Mostra tutti i file** in **Esplora soluzioni** per visualizzare la cartella **bin**. Questo comportamento dipende dall'impostazione della proprietà **Copia nella directory di output** del file.  L'impostazione predefinita della proprietà dipende dal tipo di file di database in uso.  
  
> [!NOTE]
>  Il comportamento della proprietà **Copia nella directory di output** non riguarda i progetti Web o i progetti C\+\+.  
  
 Durante lo sviluppo dell'applicazione, eventuali modifiche apportate ai dati \(durante la fase di esecuzione all'interno dell'applicazione\) vengono estese al database nella cartella **bin**.  Se, ad esempio, si preme il tasto F5 per eseguire il debug dell'applicazione, si verrà connessi al database nella cartella **bin**.  Il file di database nella cartella radice del progetto viene modificato solo in caso di modifica dello schema o dei dati del database tramite **Esplora server**, **Esplora database** o [Visual Database Tools](http://msdn.microsoft.com/it-it/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Nella tabella seguente vengono descritte le impostazioni della proprietà **Copia nella directory di output**.  
  
|Impostazione|Comportamento|  
|------------------|-------------------|  
|**Copia se più recente** \(impostazione predefinita per i file sdf\)|Il file di database viene copiato dalla directory del progetto alla directory **bin** alla prima compilazione del progetto.  A ogni successiva compilazione del progetto, la proprietà di **Data ultima modifica** dei file viene confrontata.  Se il file nella cartella del progetto è più recente, verrà copiato nella cartella **bin** e sostituirà il file attualmente al suo interno.  Se invece è più recente il file nella cartella **bin**, non verrà effettuata alcuna copia.  Con questa impostazione vengono mantenute eventuali modifiche apportate ai dati durante la fase di esecuzione. Pertanto, ogni volta che si esegue l'applicazione e si salvano le modifiche ai dati, queste saranno visibili alla successiva esecuzione dell'applicazione. **Caution:**  Questa opzione non è consigliabile per i file mdb o mdf.  Il file di database può essere modificato anche quando non si effettua alcuna modifica ai dati.  È sufficiente aprire una connessione su un file di dati, ad esempio espandendo il nodo **Tabelle** in **Esplora server**, per contrassegnarlo come più recente.|  
|**Copiare sempre** \(impostazione predefinita per i file mdf e mdb\)|Il file di database viene copiato dalla directory del progetto alla directory \/bin a ogni compilazione dell'applicazione.  Quindi, se si compila l'applicazione e si salvano le modifiche apportate al file nella directory \/bin, tali modifiche verranno sovrascritte la volta successiva in cui il file originale viene copiato nella directory \/bin.|  
|**Non copiare**|Il file non viene mai copiato né sovrascritto dal sistema di progetto.  È necessario copiare manualmente il file dalla directory del progetto nella directory di output se si utilizza questa impostazione.|  
  
## Procedura  
  
#### Per rispondere alle richieste nella finestra di dialogo del file di database locale  
  
-   Scegliere **Sì** se si desidera che in Visual Studio venga copiato il file di database all'interno del progetto e che venga modificata la connessione, in modo che punti alla copia nel progetto.  Per ulteriori informazioni sull'utilizzo dei file di database nel progetto, vedere [Cenni preliminari sui dati locali](../data-tools/local-data-overview.md).  
  
-   Scegliere **No** se non si desidera che in Visual Studio il file di database venga copiato all'interno del progetto.  I punti di connessione al file nel percorso originale e il file di database non vengono aggiunti come un file al progetto.  
  
## Vedere anche  
 [Procedura dettagliata: connessione ai dati in un file di database lodale \(Windows Form\)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)   
 [Procedura dettagliata: connessione ai dati in un database di Access \(Windows Form\)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)