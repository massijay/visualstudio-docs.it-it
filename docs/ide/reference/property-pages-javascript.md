---
title: "Pagine propriet&#224;, JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.debugging.debuggertype"
  - "javascript.project.property.debugging.requireauthentication"
  - "javascript.project.property.outputpath"
  - "javascript.project.property.debugging.launchapplication"
  - "javascript.project.property.defaultlanguage"
  - "javascript.project.property.debugging.machinename"
  - "javascript.project.property.debugging.allowlocalnetworkloopback"
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Pagine propriet&#224;, JavaScript
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'opzione **Pagine delle proprietà** permette di accedere alle impostazioni del progetto.  È possibile usare le pagine visualizzate in **Pagine delle proprietà** per modificare le proprietà del progetto.  
  
 Per accedere alle proprietà del progetto, selezionare un nodo del progetto in **Esplora soluzioni**.  Scegliere **Proprietà** dal menu **Progetto**.  
  
 [!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]  
  
 Le pagine e le opzioni seguenti vengono visualizzate in **Pagine delle proprietà**.  
  
## Pagina Configurazione e piattaforma  
 Usare le opzioni seguenti per selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare.  Le impostazioni sono **Debug** \(predefinita\), **Release**, **Tutte le configurazioni** o una configurazione definita dall'utente.  Per altre informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
 **Platform**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare.  Le impostazioni sono **Qualsiasi CPU** \(impostazione predefinita per app di [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)]\), **x64**, **ARM**, **x86** o una piattaforma definita dall'utente.  Per altre informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
## Pagina Generale  
 Usare le opzioni seguenti per impostare le proprietà generali del progetto.  
  
> [!NOTE]
>  Alcune opzioni sono disponibili solo per le app di Windows Store.  
  
 **Percorso output**  
 Specifica il percorso dei file di output per la configurazione del progetto.  Il percorso è relativo. Se si immette un percorso assoluto, questo viene salvato nel progetto.  Il percorso predefinito è bin\\Debug.  
  
 Quando si usano configurazioni di compilazione semplificate, il sistema del progetto determina se compilare una versione di debug o una versione finale.  Quando si fa clic su **Debug**, **Avvia debug** \(o si preme F5\), la compilazione viene salvata nel percorso di debug, indipendentemente dal valore specificato in **Percorso output**.  Tuttavia, il comando **Compila soluzione** del menu **Compila** fa sì che la compilazione venga inserita nel percorso specificato.  Per abilitare configurazioni di compilazione avanzate, sulla barra dei menu scegliere **Strumenti**, **Opzioni**.  Nella finestra di dialogo **Opzioni** espandere **Progetti e soluzioni**, selezionare **Generale** e quindi deselezionare la casella di controllo **Mostra configurazioni della build avanzate**.  In questo modo, è possibile controllare manualmente tutti i valori di configurazione e specificare se compilare una versione di debug o una finale.  Per altre informazioni, vedere [NIB: General, Projects and Solutions, Options Dialog Box](http://msdn.microsoft.com/it-it/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
 **Lingua predefinita**  
 Specifica la lingua predefinita per il progetto.  L'opzione selezionata in **Orologio, lingua e opzioni internazionali** nel Pannello di controllo specifica la lingua preferita dell'utente.  Specificando una lingua predefinita per il progetto, si garantisce che vengano usate le risorse della lingua predefinita specificate se la lingua preferita dell'utente non corrisponde alle risorse della lingua presenti nell'applicazione.  
  
## Pagina Debug  
 Usare le opzioni seguenti per impostare le proprietà per il comportamento di debug nel progetto.  
  
> [!NOTE]
>  Alcune opzioni sono disponibili solo per le app di Windows Store.  
  
 **Debugger da avviare**  
 Specifica l'host predefinito per il debugger.  
  
-   Selezionare **Computer locale** per avviare l'applicazione nel computer host di Visual Studio.  Per altre informazioni, vedere [Esecuzione di app nel computer locale](http://go.microsoft.com/fwlink/?LinkId=234912).  
  
-   Selezionare **Simulatore** per avviare l'applicazione nel simulatore.  Per altre informazioni, vedere [Esecuzione di app nel simulatore](http://go.microsoft.com/fwlink/?LinkId=234913).  
  
-   Selezionare **Computer remoto** per avviare l'applicazione in un computer remoto.  Per altre informazioni sul debug remoto, vedere [Esecuzione di app in un computer remoto](http://go.microsoft.com/fwlink/?LinkId=234914).  
  
 **Avvia applicazione**  
 Specifica se avviare l'applicazione quando si preme F5 o si fa clic su **Debug**, **Avvia debug**.  Selezionare **Sì** per avviare l'applicazione, altrimenti selezionare **No**.  Se si seleziona **No**, è comunque possibile eseguire il debug dell'applicazione usando un metodo diverso per avviarla.  
  
 **Tipo di debugger**  
 Specifica i tipi di codice di cui eseguire il debug.  Selezionare **Solo script** per eseguire il debug del codice JavaScript.  Selezionare **Solo gestito** per eseguire il debug del codice gestito da Common Language Runtime.  Selezionare **Solo nativo** per eseguire il debug del codice C\+\+.  Selezionare **Nativo con script** per eseguire il debug del codice C\+\+ e JavaScript.  Selezionare **Misto \(gestito e nativo\)** per eseguire il debug del codice gestito e C\+\+.  
  
 **Consenti loopback della rete locale**  
 Specifica se l'accesso all'indirizzo di loopback IP è consentito per i test dell'app.  Selezionare **Sì** per consentire l'uso dell'indirizzo di loopback se l'app client si trova nello stesso computer in cui viene eseguita l'applicazione server, altrimenti selezionare **No**.  Questa proprietà è disponibile solo se la proprietà **Debugger da avviare** è impostata su **Computer remoto**.  
  
 **Nome computer**  
 Specifica il nome del computer remoto per l'hosting del debugger.  Questa proprietà è disponibile solo se la proprietà **Debugger da avviare** è impostata su **Computer remoto**.  
  
 **Richiedi autenticazione**  
 Specifica se il computer remoto richiede l'autenticazione.  Questa proprietà è disponibile solo se la proprietà **Debugger da avviare** è impostata su **Computer remoto**.