---
title: "Procedura dettagliata: cattura programmatica delle informazioni grafica | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 21
caps.handback.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura dettagliata: cattura programmatica delle informazioni grafica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La funzionalità Diagnostica grafica di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] consente di acquisire a livello di codice informazioni grafiche da un'app Direct3D.  
  
 L'acquisizione a livello di codice è utile in scenari quali ad esempio:  
  
-   Iniziare l'acquisizione a livello di codice quando l'app grafica non usa la presentazione della catena di scambio, ad esempio quando esegue il rendering su una trama.  
  
-   Iniziare l'acquisizione a livello di codice quando l'app non esegue il rendering, ad esempio quando usa DirectCompute per eseguire calcoli.  
  
-   Chiamare `CaptureCurrentFrame` quando un problema di rendering è difficile da prevedere e acquisire nei test manuali, ma può essere previsto a livello di codice usando le informazioni sullo stato dell'app in fase di esecuzione.  
  
##  <a name="CaptureDX11_2"></a> Acquisizione a livello di codice in Windows 8.1  
 Questa parte della procedura dettagliata illustra l'acquisizione a livello di codice nelle app che usano l'API DirectX 11.2 su Windows 8.1, che usa il metodo di acquisizione affidabile. Per informazioni sull'acquisizione a livello di codice nelle app che usano versioni precedenti di DirectX in Windows 8.0, vedere [Acquisizione a livello di codice in Windows 8.0 e versioni precedenti](#CaptureDX11_1) più avanti in questa procedura dettagliata.  
  
 Questa sezione illustra l'esecuzione delle attività seguenti:  
  
-   Preparazione dell'app per usare l'acquisizione a livello di codice  
  
-   Ottenere l'interfaccia IDXGraphicsAnalysis  
  
-   Acquisizione di informazioni grafiche  
  
> [!NOTE]
>  Le implementazioni precedenti di acquisizione a livello di codice si basavano su Remote Tools per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per fornire funzionalità di acquisizione, Windows 8.1 supporta direttamente l'acquisizione mediante Direct3D 11.2. Di conseguenza, per l'acquisizione a livello di codice in Windows 8.1 non è più necessario installare Remote Tools.  
  
### Preparazione dell'app per usare l'acquisizione a livello di codice  
 Per usare l'acquisizione a livello di codice nell'app, deve includere le intestazioni necessarie. Queste intestazioni fanno parte di Windows 8.1 SDK.  
  
##### Per includere le intestazioni per l'acquisizione a livello di codice  
  
-   Includere le intestazioni nel file di origine in cui verrà definita l'interfaccia IDXGraphicsAnalysis:  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    >  Non includere il file di intestazione `vsgcapture.h`, che supporta l'acquisizione a livello di codice in Windows 8.0 e versioni precedenti, per eseguire l'acquisizione a livello di codice nelle app Windows 8.1. Questa intestazione non è compatibile con DirectX 11.2. Se si include il file dopo l'intestazione `d3d11_2`, il compilatore genera un avviso. Se si include `vsgcapture.h` prima di `d3d11_2`, l'app non si avvierà.  
  
    > [!NOTE]
    >  Se nel computer è installata la versione di DirectX SDK del giugno 2010 e il percorso di inclusione del progetto contiene `%DXSDK_DIR%include\x86`, spostarlo alla fine del percorso di inclusione. Eseguire la stessa operazione per il percorso della libreria.  
  
#### Windows Phone 8.1  
 Poiché Windows Phone 8.1 SDK non include l'intestazione `DXProgrammableCapture.h`, sarà necessario definire manualmente l'interfaccia `IDXGraphicsAnalysis` in modo da poter usare i metodi `BeginCapture()` e `EndCapture()`. Includere altre intestazioni come descritto nella sezione precedente.  
  
###### Per definire l'interfaccia IDXGraphicsAnalysis  
  
-   Definire l'interfaccia IDXGraphicsAnalysis nello stesso file in cui sono stati inclusi i file di intestazione.  
  
    ```  
    interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
    IDXGraphicsAnalysis : public IUnknown  
    {  
        STDMETHOD_(void, BeginCapture)() PURE;  
        STDMETHOD_(void, EndCapture)() PURE;  
    };  
    ```  
  
 Per praticità, si possono eseguire questi passaggi in un nuovo file di intestazione e quindi includerlo nel punto dell'app in cui è necessario.  
  
### Ottenere l'interfaccia IDXGraphicsAnalysis  
 Prima di poter acquisire informazioni grafiche da DirectX 11.2, è necessario ottenere l'interfaccia di debug DXGI.  
  
> [!IMPORTANT]
>  Quando si usa l'acquisizione a livello di codice, si deve continuare a eseguire l'app nella diagnostica grafica \(Alt\+F5 in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\).  
  
##### Per ottenere l'interfaccia IDXGraphicsAnalysis  
  
-   Usare il codice seguente per associare l'interfaccia IDXGraphicsAnalysis all'interfaccia di debug DXGI.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     Verificare il valore `HRESULT` restituito da `DXGIGetDebugInterface1` per assicurarsi di ottenere un'interfaccia valida prima di usarla:  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    >  Se `DXGIGetDebugInterface1` restituisce `E_NOINTERFACE` \(`errore: E_NOINTERFACE Interfaccia non supportata`\), assicurarsi che l'app sia in esecuzione nella diagnostica grafica \(ALT\+F5 in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\).  
  
### Acquisizione di informazioni grafiche  
 Ora che si dispone di un'interfaccia `IDXGraphicsAnalysis` valida, è possibile usare `BeginCapture` e `EndCapture` per acquisire informazioni grafiche.  
  
##### Per acquisire informazioni grafiche  
  
-   Per iniziare ad acquisire informazioni grafiche, usare `BeginCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     Quando viene chiamato `BeginCapture`, l'acquisizione inizia immediatamente senza aspettare l'inizio del frame successivo. L'acquisizione termina quando viene presentato il frame corrente o quando si chiama `EndCapture`:  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
##  <a name="CaptureDX11_1"></a> Acquisizione a livello di codice in Windows 8.0 e versioni precedenti  
 Questa parte della procedura dettagliata illustra l'acquisizione a livello di codice per Windows 8.0 e versioni precedenti che usano l'API DirectX 11.1, che usa il metodo di acquisizione legacy. Per informazioni sull'acquisizione a livello di codice nelle app che usano DirectX 11.2 in Windows 8.1, vedere [Acquisizione a livello di codice in Windows 8.1](#CaptureDX11_2) in precedenza in questa procedura dettagliata.  
  
 Questa sezione illustra le attività seguenti:  
  
-   Preparazione del computer per usare l'acquisizione a livello di codice  
  
-   Preparazione dell'app per usare l'acquisizione a livello di codice  
  
-   Configurazione del nome e del percorso del file del log di grafica  
  
-   Uso dell'API `CaptureCurrentFrame`  
  
### Preparazione del computer per usare l'acquisizione a livello di codice  
 L'API di acquisizione a livello di codice usa Remote Tools per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per rendere disponibili funzionalità di acquisizione. Nel computer in cui verrà eseguita l'app devono essere installati gli strumenti remoti, anche se si usa l'acquisizione a livello di codice nel computer locale. Quando si usa l'acquisizione a livello di codice nel computer locale, non è necessario che [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sia in esecuzione.  
  
 Per usare le API di acquisizione remota in un'app in esecuzione in un computer, è prima di tutto necessario installare Remote Tools per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nel computer. Versioni diverse degli strumenti remoti supportano piattaforme hardware diverse. Per informazioni su come installare gli strumenti remoti, vedere la pagina di [download di Remote Tools](http://go.microsoft.com/fwlink/p/?LinkId=246691) nel sito Web dei download Microsoft.  
  
 In alternativa, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installa i componenti necessari per eseguire l'acquisizione remota per app a 32 bit.  
  
> [!NOTE]
>  Poiché la maggior parte delle app desktop Windows, compreso [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], non è supportata in [!INCLUDE[win8](../debugger/includes/win8_md.md)] per i dispositivi ARM, usare Remote Tools per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] insieme all'API di acquisizione a livello di codice rappresenta l'unico modo per acquisire diagnostica grafica nei dispositivi ARM.  
  
### Preparazione dell'app per usare l'acquisizione a livello di codice  
 Per usare gli strumenti di diagnostica grafica, occorre prima di tutto acquisire le informazioni grafiche necessarie. È possibile acquisire le informazioni a livello di codice usando l'API `CaptureCurrentFrame`.  
  
##### Per preparare l'app all'acquisizione di informazioni grafiche a livello di codice  
  
1.  Assicurarsi che l'intestazione `vsgcapture.h` sia inclusa nel codice sorgente dell'app. Può essere inclusa in una sola posizione, ad esempio nel file di codice sorgente in cui si chiamerà l'API di acquisizione a livello di codice o in un file di intestazione precompilato per chiamare l'API da più file di codice sorgente.  
  
2.  Nel codice sorgente dell'app, ogni volta che si vuole acquisire il resto del frame corrente, chiamare `g_pVsgDbg->CaptureCurrentFrame()`. Questo metodo non accetta parametri e non restituisce un valore.  
  
### Configurazione del nome e del percorso del file del log di grafica  
 Il log di grafica viene creato nel percorso definito dalle macro `DONT_SAVE_VSGLOG_TO_TEMP` e `VSG_DEFAULT_RUN_FILENAME`.  
  
##### Per configurare il nome e il percorso del file del log di grafica  
  
-   Per evitare che il log di grafica venga scritto nella directory temporanea, prima della riga `#include <vsgcapture.h>` aggiungere quanto segue:  
  
    ```  
    #define DONT_SAVE_VSGLOG_TO_TEMP  
    ```  
  
     È possibile definire questo valore in modo da scrivere il log di grafica in un percorso relativo alla directory di lavoro oppure in un percorso assoluto, se la definizione di `VSG_DEFAULT_RUN_FILENAME` è un percorso assoluto.  
  
-   Per salvare il log di grafica in un percorso diverso o assegnargli un nome file diverso, prima della riga `#include <vsgcapture.h>` aggiungere quanto segue:  
  
    ```  
    #define VSG_DEFAULT_RUN_FILENAME <filename>  
    ```  
  
     Se non si esegue questo passaggio, il file verrà denominato default.vsglog. Se `DONT_SAVE_VSGLOG_TO_TEMP` non è stato definito, il percorso del file è relativo alla directory temporanea. In caso contrario, è relativo alla directory di lavoro o a un'altra posizione se è stato specificato un nome file assoluto.  
  
 Per le app [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)], il percorso della directory temporanea è specifico di ogni utente e applicazione e in genere è simile a C:\\utenti\\*nomeutente*\\AppData\\Local\\Packages\\*nome famiglia pacchetto*\\TempState\\. Per le app desktop, il percorso della directory temporanea è specifico di ogni utente e in genere è simile a C:\\Utenti\\*nomeutente*\\AppData\\Local\\Temp\\.  
  
> [!NOTE]
>  Per scrivere in una posizione specifica è necessario disporre delle autorizzazioni per la scrittura in quella posizione. In caso contrario, si verificherà un errore. Tenere presente che le app [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] hanno più restrizioni rispetto alle app desktop sui percorsi in cui è possibile scrivere dati e che per scrivere in determinati percorsi può essere necessario eseguire operazioni di configurazione aggiuntive.  
  
### Acquisizione delle informazioni grafiche  
 Dopo aver preparato l'app per l'acquisizione a livello di codice e aver facoltativamente configurato il percorso e il nome del file di log della grafica, compilare l'applicazione ed eseguirla o eseguire il debug per acquisire i dati; non avviare la diagnostica grafica da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando si usa l'API di acquisizione a livello di codice. Il log di grafica viene scritto nel percorso specificato. Se si vuole conservare questa versione del log, spostarlo in un altro percorso. In caso contrario, verrà sovrascritto quando si esegue nuovamente l'app.  
  
> [!TIP]
>  Quando si usa l'acquisizione a livello di codice, è comunque possibile acquisire informazioni grafiche manualmente premendo **STAMP** con l'app in stato attivo. Si può usare questa tecnica per acquisire informazioni grafiche aggiuntive, che non vengono acquisite dall'API di acquisizione a livello di codice.  
  
## Passaggi successivi  
 In questa procedura dettagliata è stato illustrato come acquisire informazioni grafiche a livello di codice. Come passaggio successivo, prendere in considerare questa opzione:  
  
-   Apprendere come analizzare le informazioni grafiche acquisite usando gli strumenti di diagnostica grafica. Vedere [Panoramica](../debugger/overview-of-visual-studio-graphics-diagnostics.md).  
  
## Vedere anche  
 [Cattura informazioni grafica](../debugger/capturing-graphics-information.md)   
 [Procedura dettagliata: cattura delle informazioni grafica](../debugger/walkthrough-capturing-graphics-information.md)