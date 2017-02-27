---
title: "Procedura dettagliata: utilizzo delle API del profiler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti di prestazioni, procedure dettagliate"
  - "strumenti di profilatura, procedure dettagliate"
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Procedura dettagliata: utilizzo delle API del profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata viene utilizzata un'applicazione C\# per illustrare l'utilizzo delle API degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Le API del profiler verranno utilizzate per limitare la quantità di dati raccolti durante la profilatura tramite strumentazione.  
  
 I passaggi in questa procedura dettagliata si applicano genericamente a un'applicazione in C\/C\+\+.  Per ciascun linguaggio, sarà necessario configurare l'ambiente di compilazione in modo appropriato.  
  
 In genere, si inizia analizzando le prestazioni dell'applicazione utilizzando esempi di profilatura.  Se l'esempio di profilatura non fornisce informazioni che consentano di individuare un collo di bottiglia, la profilatura mediante strumentazione sarà in grado di fornire un maggior livello di dettaglio.  La profilatura tramite strumentazione è molto utile per esaminare l'interazione tra thread.  
  
 Tuttavia, un maggiore livello di dettaglio comporterà una maggiore quantità di dati raccolti.  La profilatura tramite strumentazione potrebbe quindi causare la creazione di file dati di grandi dimensioni.  Inoltre, l'utilizzo della strumentazione comporta maggiori probabilità di influenza sulle prestazioni dell'applicazione.  Per ulteriori informazioni, vedere [Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md) e [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md).  
  
 Il Profiler di Visual Studio consente di limitare la raccolta di dati.  In questa procedura dettagliata viene fornito un esempio per limitare la raccolta dei dati utilizzando le API del profiler.  Il Profiler di Visual Studio fornisce un'API per il controllo della raccolta di dati dall'interno di un'applicazione.  
  
 Per il codice nativo, le API del profiler di Visual Studio si trovano nel file VSPerf.dll.  Il file di intestazione VSPerf.h e la libreria di importazione VSPerf.lib si trovano nella directory Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  
  
 Per il codice gestito, le API del profiler si trovano nel file Microsoft.VisualStudio.Profiler.dll.  Questa DLL si trova nella directory Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.Profiler>.  
  
## Prerequisiti  
 Nella presente procedura dettagliata si presuppone che l'ambiente di sviluppo scelto sia configurato per supportare il debug e il campionamento.  Negli argomenti seguenti viene fornita una panoramica di questi prerequisiti:  
  
 [Procedura: Scegliere un metodo di raccolta](../profiling/how-to-choose-collection-methods.md)  
  
 [Procedura: Fare riferimento alle informazioni sui simboli di Windows](../profiling/how-to-reference-windows-symbol-information.md)  
  
 Per impostazione predefinita, il profiler una volta avviato, raccoglie i dati a livello globale.  Il codice seguente posto all'inizio del programma disattiva la profilatura globale.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
 È possibile disattivare la raccolta di dati dalla riga di comando anziché tramite una chiamata API.  Nei passaggi seguenti si presuppone che l'ambiente di compilazione da riga di comando sia configurato per eseguire gli strumenti di profilatura e di sviluppo,  incluse le impostazioni necessarie per VSInstr e VSPerfCmd.  Vedere Strumenti di profilatura della riga di comando.  
  
## Limitazione della raccolta dati tramite l'utilizzo delle API del Profiler  
  
#### Per creare il codice da profilare  
  
1.  Creare un nuovo progetto C\# in Visual Studio, oppure eseguire una compilazione da riga di comando, a seconda delle preferenze.  
  
    > [!NOTE]
    >  La compilazione deve fare riferimento alla libreria Microsoft.VisualStudio.Profiler.dll che si trova nella directory Microsoft Visual Studio 9\\Team Tools\\Performance Tools.  
  
2.  Copiare e incollare il codice seguente nel progetto:  
  
    ```  
    using System;  
    using System.Collections.Generic;  
    using System.Text;  
    using Microsoft.VisualStudio.Profiler;  
  
    namespace ConsoleApplication2  
    {  
        class Program  
        {  
            public class A  
            {  
             private int _x;  
  
             public A(int x)  
             {  
              _x = x;  
             }  
  
             public int DoNotProfileThis()  
             {  
              return _x * _x;  
             }  
  
             public int OnlyProfileThis()  
             {  
              return _x + _x;  
             }  
  
             public static void Main()  
             {  
            DataCollection.StopProfile(  
            ProfileLevel.Global,  
            DataCollection.CurrentId);  
              A a;  
              a = new A(2);  
              int x;      
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());  
              DataCollection.StartProfile(  
                  ProfileLevel.Global,  
                  DataCollection.CurrentId);  
              x = a.OnlyProfileThis();  
              DataCollection.StopProfile(  
                  ProfileLevel.Global,   
                  DataCollection.CurrentId);  
              Console.WriteLine("2 doubled is {0}", x);  
             }  
            }  
  
        }  
    }  
    ```  
  
#### Per raccogliere e visualizzare dati nell'IDE di Visual Studio  
  
1.  Aprire l'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Scegliere **Profiler** dal menu **Analizza**, quindi selezionare **Nuova sessione di prestazioni**.  
  
2.  Aggiungere il binario compilato all'elenco **Destinazioni** nella finestra **Esplora prestazioni**.  Fare clic con il pulsante destro del mouse su **Destinazioni** e quindi scegliere **Aggiungi binario di destinazione**.  Nella finestra di dialogo **Aggiungi binario di destinazione** individuare il binario e scegliere **Apri**.  
  
3.  Selezionare **Strumentazione** dall'elenco **Metodo** nella barra degli strumenti di **Esplora prestazioni**.  
  
4.  Fare clic su **Avvio con profilatura**.  
  
     Il profiler eseguirà l'instrumentazione e il binario e verrà creato un file di report delle prestazioni.  Il file di report delle prestazioni verrà visualizzato nel nodo **Report** di **Esplora prestazioni**.  
  
5.  Aprire il file di report delle prestazioni risultante.  
  
 Per impostazione predefinita, quando il profiler viene avviato, raccoglie dati a livello globale.  Il codice seguente posto all'inizio del programma disattiva la profilatura globale.  
  
```  
DataCollection.StopProfile(  
ProfileLevel.Global,  
DataCollection.CurrentId);  
```  
  
#### Per raccogliere e visualizzare dati da riga di comando  
  
1.  Compilare una versione di debug del codice di esempio creato in precedenza nella procedura "Per creare il codice da profilare".  
  
2.  Per profilare un'applicazione gestita, digitare il comando seguente per impostare le variabili di ambiente appropriate:  
  
     VsPefCLREnv \/traceon  
  
3.  Digitare il comando seguente: VSInstr \<nome file\>.exe  
  
4.  Digitare il comando seguente: VsPerfCmd \/start:trace \/output:\<nome file\>.vsp  
  
5.  Digitare il comando seguente: VSPerfCmd \/globaloff  
  
6.  Eseguire il programma.  
  
7.  Digitare il comando seguente: VSPerfCmd \/shutdown  
  
8.  Digitare il comando seguente: VSPerfReport \/calltrace:\<nome file\>.vsp  
  
     Viene creato un file csv nella directory corrente, con i dati risultanti relativi alle prestazioni.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Profiler>   
 [Riferimenti per le API del profiler di Visual Studio \(native\)](../profiling/visual-studio-profiler-api-reference-native.md)   
 [Introduzione](../profiling/getting-started-with-performance-tools.md)   
 [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md)