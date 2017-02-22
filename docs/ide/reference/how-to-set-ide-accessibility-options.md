---
title: "Procedura: impostare le opzioni di accessibilit&#224; IDE | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "accessibilità [Visual Studio]"
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
caps.latest.revision: 21
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: impostare le opzioni di accessibilit&#224; IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] contiene funzionalità che rendono più agevole la lettura e la scrittura per gli utenti con problemi di vista e difficoltà di movimento.  Queste funzionalità includono tra le altre la modifica della dimensione e del colore del testo negli editor, la modifica della dimensione di testo e pulsanti sulle barre degli strumenti e il completamento automatico per metodi e parametri.  
  
 Inoltre, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supporta i layout di tastiera Dvorak, che consentono di accedere più facilmente ai caratteri utilizzati con maggiore frequenza.  È inoltre possibile personalizzare i tasti di scelta rapida predefiniti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Per ulteriori informazioni, vedere [Identificazione e personalizzazione dei tasti di scelta rapida](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Editor, finestre di dialogo e finestre degli strumenti  
 Per impostazione predefinita, le finestre di dialogo e finestre degli strumenti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzano la stessa dimensione del carattere e colori del sistema operativo.  Le impostazioni dei colori per il frame dell'IDE, finestre di dialogo, le barre degli strumenti e le finestre degli strumenti sono basate una combinazione di colori: luce o buio.  È possibile modificare il tema corrente di colore in [Generale, Ambiente, finestra di dialogo Opzioni](../../ide/reference/general-environment-options-dialog-box.md).  
  
 È inoltre possibile visualizzare finestre popup in visualizzazione codice dell'editor.  Queste finestre possono richiedere la visualizzazione dei membri disponibili per l'oggetto corrente e dei parametri a completare una funzione o un'istruzione.  Queste finestre possono essere utili per gli utenti con difficoltà.  Tuttavia, poiché interferiscono con lo stato attivo nell'editor di codice, possono causare problemi ad altri utenti.  È possibile disattivare queste finestre aprendo la finestra di dialogo Opzioni e deselezionando **Elenco membri automatico** e **Informazioni parametri** in **Editor di testo**, **Tutti i linguaggi**, pagina **Generale** nella finestra di dialogo **Opzioni**.  Per ulteriori informazioni, vedere [How to: Set General Editor Options](http://msdn.microsoft.com/it-it/704e4a7b-2162-4bed-8a47-f4f6ffec98c2).  
  
 Nell'ambiente di sviluppo integrato \(IDE, Integrated Development Environment\) è possibile disporre le finestre nel modo più adatto alle proprie esigenze.  È possibile ancorare, rendere mobile, nascondere, o nascondere automaticamente ogni finestra degli strumenti.  
  
 Per ulteriori informazioni su come modificare il layout delle finestre, vedere [Personalizzazione del layout della finestra](../../ide/customizing-window-layouts-in-visual-studio.md).  
  
### Modificare la dimensione del testo  
 È possibile modificare le impostazioni per le finestre degli strumenti basate su testo, quali le finestre **Comando**, **Controllo immediato** e **Output**, nel riquadro **Tipi di carattere e colori** delle opzioni della scheda **Ambiente** nella finestra di dialogo **Strumenti**.  Se l'opzione **Tutte le finestre degli strumenti di testo** dell'elenco a discesa **Mostra impostazioni per** è selezionata, l'impostazione predefinita degli elenchi a discesa **Primo piano elemento** e **Sfondo elemento** è impostata su **Predefinito**.  È inoltre possibile modificare le impostazioni relative alla modalità di visualizzazione del testo nell'editor.  
  
##### Per modificare la dimensione del testo in finestre degli strumenti ed editor basati su testo  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella cartella **Ambiente** scegliere **Tipi di carattere e colori**.  
  
3.  Selezionare un'opzione dal menu a discesa **Mostra impostazioni per**.  
  
     Per modificare la dimensione dei caratteri del testo in un editor, scegliere **Editor di testo**.  
  
     Per modificare la dimensioni dei caratteri del testo in finestre degli strumenti basate su testo, scegliere **Tutte le finestre degli strumenti di testo**.  
  
     Per modificare la dimensione dei caratteri del testo di descrizione comandi in un editor, scegliere **Descrizione comando editor**.  
  
     Per modificare la dimensione dei caratteri del testo nei popup di completamento delle istruzioni, scegliere **Completamento istruzioni**.  
  
4.  Scegliere **Testo normale** da **Elementi visualizzati**.  
  
5.  In **Tipo di carattere** selezionare un nuovo tipo di carattere.  
  
6.  In **Dimensione** selezionare una nuova dimensione per il carattere.  
  
    > [!NOTE]
    >  Per reimpostare la dimensione del testo in finestre degli strumenti ed editor basati su testo, scegliere **Valori predefiniti**.  
  
7.  Scegliere **OK**.  
  
### Modificare i colori utilizzati nell'IDE  
 È inoltre possibile scegliere di modificare i colori predefiniti di testo, indicatori di margine, spazi ed elementi di codice nell'editor.  
  
> [!NOTE]
>  Per utilizzare colori a contrasto elevato per tutte le finestre delle applicazioni del sistema operativo, premere **ALT di sinistra \+ MAIUSC di sinistra \+ STAMP**.  Se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] è aperto, chiuderlo e riaprirlo per completare l'implementazione dei colori a contrasto elevato.  
  
##### Per modificare il colore degli elementi nell'editor  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella cartella **Ambiente** scegliere **Tipi di carattere e colori**.  
  
3.  Scegliere **Editor di testo** da **Mostra impostazioni per**.  
  
4.  Da **Elementi visualizzati** selezionare l'elemento di cui è necessario modificare la visualizzazione, come **Testo normale**, **Margine indicatore**, **Spazio vuoto visibile**, **HTML \- nome attributo** o **Attributo XML**.  
  
5.  Selezionare le impostazioni di visualizzazione dalle seguenti opzioni: **Primo piano elemento**, **Sfondo elemento** e **Grassetto**.  
  
6.  Scegliere **OK**.  
  
## Barre degli strumenti  
 Per migliorare l'usabilità e l'accessibilità della barra degli strumenti, è possibile aggiungere testo ai pulsanti della barra degli strumenti.  
  
#### Per assegnare testo ai pulsanti della barra degli strumenti  
  
1.  Scegliere **Personalizza** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Personalizza** fare clic sulla scheda **Comandi**.  
  
3.  Selezionare **Barra degli strumenti** e quindi scegliere il nome della barra degli strumenti che contiene il pulsante per cui si intende visualizzare il testo.  
  
4.  Selezionare dall'elenco il comando che si intende modificare.  
  
5.  Scegliere **Modifica selezione**.  
  
6.  Scegliere **Icona e testo**.  
  
#### Per modificare il testo visualizzato del pulsante  
  
1.  Scegliere nuovamente **Modifica selezione**.  
  
2.  Adiacenti in **Nome**, insert fornisce una nuova didascalia per il pulsante selezionato.  
  
## Vedere anche  
 [Funzionalità di accessibilità di Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)   
 [Risorse per la progettazione di applicazioni accessibili](../../ide/reference/resources-for-designing-accessible-applications.md)