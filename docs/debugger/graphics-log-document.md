---
title: "Documento log grafica | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics.vsglog.error"
  - "vs.graphics.experiment"
  - "vs.graphics.vsglog"
ms.assetid: 6ccb1269-d55f-49c4-920d-baedf7de2888
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Documento log grafica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il documento di log della grafica è la registrazione degli eventi di grafica che si sono verificati durante l'esecuzione dell'app in una sessione di diagnostica della grafica.  Dopo la registrazione, è possibile esaminare il log in Analizzatore grafica di Visual Studio per diagnosticare i problemi di rendering e di prestazioni.  
  
 Ecco l'aspetto di un documento di log della grafica in Analizzatore grafica:  
  
 ![Log grafico con due frame acquisiti.](../debugger/media/gfx_diag_demo_graphics_log_orientation.png "gfx\_diag\_demo\_graphics\_log\_orientation")  
  
## Informazioni sui documenti di log della grafica  
 Se si usa Analizzatore grafica per esaminare un documento di log della grafica, è possibile visualizzare gli effetti degli eventi Direct3D che si sono verificati durante l'acquisizione sulla destinazione di rendering.  È possibile individuare aree della destinazione di rendering che contengono un output non previsto.  Quando si seleziona un pixel nell'area interessata, è possibile usare gli strumenti di Diagnostica grafica per esaminarlo, per analizzare gli shader e gli eventi Direct3D che hanno influito su di esso, gli stack di chiamate dell'applicazione che hanno generato tali eventi e gli oggetti DirectX che supportano tali eventi.  È possibile usare queste informazioni per diagnosticare i problemi di rendering nel gioco o nell'app.  
  
 Nella parte superiore della finestra \(**Graphics Experiment.vsglog**\) viene visualizzato l'output della destinazione di rendering corrente del frame selezionato, mentre nella parte inferiore viene visualizzato un **Elenco frame** contenente le immagini di anteprima dei frame acquisiti.  
  
#### Per esaminare un frame  
  
-   In **Elenco frame** selezionare il frame da esaminare.  L'output della destinazione di rendering nella parte superiore del documento di log della grafica viene aggiornato per visualizzare il frame selezionato.  
  
#### Per esaminare un pixel  
  
-   Nella parte superiore del documento di log della grafica, selezionare il pixel desiderato dall'output della destinazione di rendering.  Dopo avere selezionato un pixel, è possibile usare la finestra **Cronologia pixel grafica** per visualizzare informazioni dettagliate sul pixel selezionato.  Per altre informazioni, vedere [Cronologia pixel](../debugger/graphics-pixel-history.md).  
  
## Computer riproduzione  
 Nell'angolo superiore destro di **Elenco frame** è disponibile **Computer riproduzione**.  Computer riproduzione è un computer o un dispositivo usato per riprodurre gli eventi della grafica da un file di log della grafica durante una sessione di diagnostica della grafica successiva.  Usando un dispositivo diverso dal computer di sviluppo per riprodurre gli eventi acquisiti, è possibile riprodurre in modo più accurato l'ambiente di esecuzione in cui si verifica il problema. È ad esempio possibile usare un computer con un hardware o driver di grafica diversi rispetto a quelli presenti nel computer di sviluppo o altri tipi di dispositivi, come un tablet Windows RT basato su ARM o un dispositivo Windows Phone.  
  
 Per informazioni su come specificare un computer di riproduzione, vedere [Procedura: modificare il computer di riproduzione della diagnostica grafica](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md).  
  
## Informazioni di riepilogo del log di grafica  
 Quando un file di log di grafica è il documento attivo, nella finestra **Proprietà** sono visualizzate informazioni sull'ambiente che ha ospitato la sessione di acquisizione di Diagnostica grafica.  Sono visualizzate numerose categorie di informazioni.  
  
 **Informazioni su Direct3D**  
 Riporta le informazioni relative alle funzionalità di hardware e driver della scheda video usata durante la sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Formato High Color 10 bit XR**|**True** se il formato High Color 10 bit XR è supportato; in caso contrario, **False**.|  
|**DirectCompute CS 4.x**|**True** se Compute Shader 4.0 è supportato; in caso contrario, **False**.|  
|**Shader a precisione doppia**|**True** se la scheda video supporta valori a virgola mobile con precisione doppia \(64 bit\); in caso contrario, **False**.|  
|**Elenco comandi driver**|**True** se il driver supporta gli elenchi comandi; in caso contrario, **False**.|  
|**Creazioni simultanee driver**|**True** se il driver supporta la creazione simultanea \(asincrona\); in caso contrario, **False**.|  
|**Formati estesi \(BGRA e così via\)**|**True** se i formati estesi come BGRA sono supportati; in caso contrario, **False**.|  
|**Livello funzionalità hardware massimo**|Visualizza il livello di funzionalità massimo supportato dalla scheda video.|  
  
 **Informazioni visualizzazione**  
 Visualizza le informazioni relative alla scheda video usata durante la sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Descrizione**|Stringa di descrizione della scheda video.|  
|**Memoria visualizzazione**|Quantità di memoria installata nella scheda video grafica.|  
|**Nome driver**|Nome del driver della scheda video grafica.|  
|**Versione driver**|Versione del driver della scheda video grafica.|  
|**Nome**|Nome della scheda video grafica.|  
  
 **File esperimento**  
 Visualizza le informazioni relative al file esperimento associato alla sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Percorso**|Percorso del file con estensione vsglog. **Note:**  Nell'ambito dell'acquisizione legacy, questa proprietà è inutilizzata.|  
  
 **Informazioni sul modulo**  
 Visualizza il nome e la versione delle DLL \(Dynamic Link Library\) caricate dall'app durante la sessione di acquisizione.  
  
 **Informazioni di sistema**  
 Visualizza le informazioni relative all'hardware e al sistema operativo che hanno ospitato l'app durante la sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Memoria**|Quantità di memoria installata nel computer.|  
|**Architettura sistema operativo**|L'architettura della CPU di destinazione del sistema operativo.|  
|**Versione sistema operativo**|Versione del sistema operativo.|  
|**Processore**|Processore installato nel computer.|  
|**Architettura applicazione di destinazione**|L'architettura della CPU di destinazione dell'app.  Può essere diversa da **Architettura sistema operativo**.|  
  
 **Applicazione di destinazione**  
 Visualizza le informazioni relative all'app oggetto della sessione di acquisizione.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Data\/ora ultima modifica**|Data e ora in cui è stata compilata l'app.|  
|**Percorso**|Percorso dell'app.|  
|**ID processo**|ID processo assegnato all'app.|  
|**Versione**|Versione dell'app.|  
  
 **File di log VSG**  
 Visualizza le informazioni relative al documento di log della grafica.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Creato da**|Nome dell'app che ha creato il documento di log della grafica.  Ad esempio, se la sessione di acquisizione è stata avviata da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(acquisizione manuale\), il valore di questa proprietà è [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|**Ora inizio sessione**|Data e ora in cui è stata iniziata la sessione di acquisizione.|  
|**Dimensioni**|Dimensione del documento log grafica.|  
  
## Vedere anche  
 [Procedura dettagliata: oggetti mancanti a causa dello sfondo Vertex](../debugger/walkthrough-missing-objects-due-to-vertex-shading.md)   
 [Procedure dettagliate: debug degli errori di rendering dovuti allo sfondo](../debugger/walkthrough-debugging-rendering-errors-due-to-shading.md)