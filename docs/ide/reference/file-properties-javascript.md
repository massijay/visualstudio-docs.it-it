---
title: "Propriet&#224; file, JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.expandedsdknode.fileversion"
  - "javascript.project.property.expandedsdknode.uri"
  - "javascript.project.property.expandedsdknode.filename"
  - "javascript.project.property.reference.description"
  - "javascript.project.property.reference.specificversion"
  - "javascript.project.property.reference.identity"
  - "javascript.project.property.fullpath"
  - "javascript.project.property.packageaction"
  - "javascript.project.property.reference.package"
  - "javascript.project.property.copytooutputdirectory"
  - "javascript.project.property.expandedsdknode.sdkpath"
  - "javascript.project.property.reference.filetype"
  - "javascript.project.property.reference.culture"
  - "javascript.project.property.filename"
  - "javascript.project.property.reference.resolvedpath"
  - "javascript.project.property.reference.version"
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Propriet&#224; file, JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Le proprietà dei file consentono di definire le operazioni da eseguire sui file stessi dal sistema del progetto.  Ad esempio, è possibile impostare le proprietà di per indicare se un file deve essere aggiunto al pacchetto come file di risorse.  
  
 È possibile selezionare qualsiasi file in Esplora soluzioni ed esaminarne le proprietà nella finestra Proprietà.  I file JavaScript sono disponibili quattro proprietà: **Copia in directory di output**, **Azione pacchetto**, **Nome file**e **Percorso file**.  
  
## Proprietà dei file  
 In questa sezione vengono descritte le proprietà comuni ai file JavaScript.  
  
### Proprietà Copia nella directory di output  
 Questa proprietà consente di specificare le condizioni in cui il file di origine selezionato verrà copiato nella directory di output.  Selezionare **Non copiare** se il file non viene mai copiato nella directory di output.  Selezionare **Copia sempre** se il file viene sempre copiato nella directory di output.  Selezionare **Copia se più recente** se il file deve essere copiato solo quando è più recente del file esistente con lo stesso nome nella directory di output.  
  
### Azione pacchetto  
 La proprietà **Azione pacchetto** indica che Visual Studio in un file durante la compilazione.  **Azione pacchetto** possono essere assegnati diversi valori:  
  
-   **nessuno** Il file non è incluso nel manifesto di pacchetto.  Un file di questo tipo può essere un file di testo contenente informazioni varie, ad esempio un file Readme.  
  
-   **contenuto** Il file è incluso nel manifesto di pacchetto.  Ad esempio, questa impostazione è il valore predefinito per .htm, un file js, un CSS, un'immagine, un audio, o un file video.  
  
-   **Manifesto** Il file non è incluso nel manifesto di pacchetto.  Invece, il file viene utilizzato per input quando generare il manifesto di pacchetto.  Questo è il valore predefinito per il file di package.appxmanifest.  
  
-   **risorsa** Il file non è incluso nel manifesto di pacchetto.  Invece, il contenuto del file verrà indicizzato nell'indice \(PRI\) delle risorse del pacchetto che entra nel manifesto di pacchetto.  impostazione normalmente utilizzata per il file di risorse.  
  
 Il valore predefinito per **Azione pacchetto** dipende dall'estensione del file aggiunto alla soluzione.  
  
### Proprietà Nome file  
 Visualizza il nome file come valore di sola lettura.  Per rinominare il file, è necessario fare clic con il pulsante destro del mouse in Esplora soluzioni e selezionare **Rinomina**.  
  
### Proprietà percorso completo  
 Visualizza il percorso completo del file come valore di sola lettura.  Per modificare il percorso del file, è possibile trascinare il file in Esplora Risorse.  
  
## Proprietà dei file di riferimento  
 In questa sezione vengono descritte le proprietà comuni ai file a cui si fa riferimento in [!INCLUDE[win8_app_js](../../ide/reference/includes/win8_app_js_md.md)].  Quando si seleziona un riferimento a un file di .winmd, un riferimento SDK, un riferimento da progetto a progetto, o un riferimento a un assembly in Esplora soluzioni, altre proprietà possono visualizzare nella Finestra Proprietà, a seconda del tipo di file.  
  
### Impostazioni cultura  
 Visualizzare il linguaggio associato al riferimento.  
  
### Tipo di file  
 Visualizza il tipo di file di riferimento.  
  
### Versione file  
 Visualizza la versione del file di riferimento.  
  
### Identità  
 Visualizza l'identità del riferimento utilizzata nel progetto, archiviato nel file di progetto.  
  
### Pacchetto  
 Visualizza il nome del manifesto di pacchetto associato al riferimento.  
  
### Percorso risolto  
 Visualizzare il percorso del riferimento utilizzata nel progetto.  
  
### Percorso dell'SDK  
 Visualizzare il percorso del file a cui si fa riferimento SDK.  
  
### Uri  
 Visualizza l'uri che deve essere incluso in HTML del progetto o il file JavaScript per includere il file come file di origine.  
  
### Versione  
 Visualizza la versione del riferimento.  
  
## Vedere anche  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/it-it/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)