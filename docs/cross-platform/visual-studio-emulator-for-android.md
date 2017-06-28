---
title: "Emulatore di Visual Studio per Android | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "tgt-pltfrm-cross-plat"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Emulatore di Visual Studio per Android
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L’Emulatore di Visual Studio per Android è un’applicazione desktop che emula un dispositivo Android.  Fornisce un ambiente virtualizzato in cui è possibile eseguire il debug e testare applicazioni Android senza un dispositivo fisico.  Offre inoltre un ambiente isolato per i prototipi di applicazioni.  
  
 Emulatore di Visual Studio per Android è progettato per fornire prestazioni paragonabili a un dispositivo reale.  Prima di pubblicare l'applicazione, tuttavia, è consigliabile testare l'applicazione in un dispositivo fisico.  
  
 È possibile testare l'applicazione in un profilo univoco del dispositivo per ognuna delle piattaforme Android, risoluzioni dello schermo e altre proprietà di hardware supportate dall'emulatore di Visual Studio per Android.  
  
 Di seguito sono elencate le diverse sezioni di questo argomento:  
  
-   [Installazione o disinstallazione](#Installing)  
  
-   [Requisiti di sistema e compatibilità con le versioni precedenti](#Requirements)  
  
-   [Rete con l’emulatore di Visual Studio per Android](#Networking)  
  
-   [Configurazione dell’emulatore di Visual Studio per Android](#Configuring)  
  
-   [Funzionalità che è possibile testare nell'emulatore](#FeaturesTest)  
  
-   [Funzionalità che non è possibile testare nell'emulatore](#FeaturesNonTest)  
  
-   [Risorse di supporto](#Support)  
  
##  <a name="Installing"></a> Installazione o disinstallazione  
 Installazione  
  
 Visual Studio l'emulatore di Android è un componente di strumenti multipiattaforma disponibili in Visual Studio e verrà installato durante un'installazione personalizzata di Visual Studio quando si seleziona lo sviluppo di piattaforme mobili, quindi strumenti comuni e Software Development Kit e quindi emulatore di Visual Studio per Android.  
  
 Disinstallazione  
  
 È possibile installare l'emulatore di Visual Studio per Android usando la funzionalità Installazione applicazioni del Pannello di controllo.  
  
> [!NOTE]
>  La disinstallazione di Visual Studio non comporta la disinstallazione dell'emulatore.  È necessario disinstallare l'emulatore separatamente.  
  
 Quando si disinstalla l'emulatore di Visual Studio per Android, le schede Ethernet Hyper\-V virtuali creati per utilizzare l'emulatore non vengono rimossi automaticamente.  È possibile rimuovere manualmente queste schede virtuali \(se non sono in uso\) aprendo Hyper\-V Manager, selezionando una delle immagini VHD dell'emulatore, scegliendo la scheda Rete e quindi **Rimuovi** per ognuna delle opzioni visualizzate nella scheda.  
  
##  <a name="Requirements"></a> Requisiti di sistema e compatibilità con le versioni precedenti  
 Per informazioni importanti su requisiti hardware, software e di configurazione per l'emulatore di Visual Studio per Android, vedere gli argomenti seguenti.  
  
-   [Requisiti di sistema per Visual Studio Emulator per Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
 Visual Studio l'emulatore di Android richiede Visual Studio 2015. non è compatibile con le versioni precedenti di Visual Studio.  
  
 Nuove versioni dell'emulatore installate in versioni precedenti e possono, in alcuni casi, sostituire le immagini precedenti, ignorando le impostazioni, applicazioni e i file installati in tali immagini.  
  
##  <a name="Networking"></a> Rete con l’emulatore di Visual Studio per Android  
 La connessione dell'emulatore di Visual Studio per Android si comporta come la connessione di un computer desktop con queste caratteristiche:  
  
-   L'emulatore viene visualizzato sulla rete come un dispositivo distinto con il proprio indirizzo IP.  
  
-   Non richiede ulteriore software di rete non è già installato con l'emulatore.  
  
-   Non è unito a un dominio Windows.  
  
 Per comprendere le funzionalità di connessione di rete dell'emulatore, essere considerato come, simile a una connessione Wi\-Fi dal telefono Android alla stessa rete.  Se un'applicazione in esecuzione sul telefono può accedere a una risorsa di rete tramite la connessione Wi\-Fi, un'applicazione in esecuzione nell'emulatore può inoltre accedere la stessa risorsa di rete.  
  
 Per i requisiti di sistema vedere[Requisiti di sistema per Visual Studio Emulator per Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).  
  
 Per informazioni sulla risoluzione dei problemi di rete, vedere [Risoluzione dei problemi di Visual Studio Emulatore per Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
##  <a name="Configuring"></a> Configurazione dell’emulatore di Visual Studio per Android  
 Test dell'app Android per la compatibilità tra la varietà di hardware Android scaglionamento può rappresentare un problema.  Telefoni e Tablet nel mercato Android span un'ampia gamma di versioni e le dimensioni dello schermo e sono disponibili in molte configurazioni hardware diverse \(RAM, CPU, architettura e così via\).  Emulatore di Visual Studio per Android semplifica questo utilizzo dei profili di dispositivo.  Il set di profili di dispositivo rappresentano l'hardware più diffuso sul mercato, inclusi i dispositivi da Samsung, Motorola, Sony, generatore di carico e così via.  
  
 In Visual Studio 2015, è possibile installare, disinstallare e avviare i profili di dispositivo utilizzando Gestione emulatori di.  Accedere a Gestione emulatori di scegliendo **strumenti**, quindi **Visual Studio l'emulatore di Android**.  
  
 ![Visual Studio Emulator for Android Manager](../cross-platform/media/android_emu_manager.png "Android\_Emu\_Manager")  
  
 Per impostazione predefinita, sono disponibili quattro profili dispositivo pre\-installato \(telefono\/5 KitKat e il simbolo "e Tablet PC\/7" configurazioni\), come indicato dal testo bianco e icone.  Altri profili nell'elenco verranno visualizzati in grigio fino a quando non si sceglie il **Installa profilo** pulsante e l'installazione viene completata.  È possibile filtrare l'elenco in base al livello dell'API e fare clic sulla freccia di dettagli sul lato inferiore destro di un profilo per visualizzarne i dettagli di configurazione completa.  
  
 Dopo aver installato il set di profili che si desidera di destinazione, è possibile avviare questi nuovi profili direttamente dalla gestione premendo verde **riprodurre** pulsante.  Verranno inoltre visualizzati nel menu a discesa destinazione debug in qualsiasi tipo di progetto per dispositivi mobili multipiattaforma di Visual Studio.  
  
##  <a name="FeaturesTest"></a> Funzionalità che è possibile testare nell'emulatore  
 Per informazioni dettagliate sulle funzionalità che è possibile testare nell'emulatore, vedere questo [documentazione](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx).  
  
##  <a name="FeaturesNonTest"></a> Funzionalità che non è possibile testare nell'emulatore  
 Nell'elenco seguente vengono descritte le funzionalità della piattaforma Android che si **Impossibile** testare nell'emulatore.  È necessario verificare queste funzionalità in un dispositivo fisico.  
  
-   Bussola  
  
-   Giroscopio  
  
-   Controller vibrazione  
  
-   Luminosità  Modifica del livello di luminosità dell'emulatore non visivamente influirà il modo in cui che il dispositivo viene visualizzato sullo schermo.  
  
##  <a name="Support"></a> Risorse di supporto  
 Se il computer host soddisfa i requisiti di sistema e si verifica un problema non incluso in questa guida alla risoluzione dei problemi:  
  
-   Porre una domanda in StackOverflow usando i tag [android\-emulator](http://stackoverflow.com/questions/tagged/android-emulator) e visual\-studio.  
  
-   Segnalare un problema usando lo strumento Invia smile in Visual Studio o in Gestione emulatori.  
  
## Vedere anche  
 [Requisiti di sistema per Visual Studio Emulator per Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Risoluzione dei problemi di Visual Studio Emulatore per Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)