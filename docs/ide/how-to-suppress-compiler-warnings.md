---
title: "Procedura: non visualizzare avvisi del compilatore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 31827b17-f933-413d-b28a-b19f903b64ca
caps.latest.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Procedura: non visualizzare avvisi del compilatore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile declutter un log di compilazione specificando uno o più tipi di avvisi del compilatore che non si desidera includere.  Ad esempio, è possibile utilizzare questa tecnica per esaminare alcuni ma non tutte le informazioni generate automaticamente quando si imposta il dettaglio del log di compilazione a normale, a dettagliato, o diagnostica.  Per ulteriori informazioni sui dettagli, vedere [Procedura: visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
### Per eliminare gli avvisi specifici per Visual c o F\#  
  
1.  In **Esplora soluzioni**, selezionare il progetto in cui si desidera eliminare gli avvisi.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.  
  
3.  Scegliere la pagina **Compila**.  
  
4.  Nella casella **Non visualizzare avvisi**, specificare i codici di errore di avvisi da eliminare, separate da punto e virgola e quindi ricompilare la soluzione.  
  
### Per eliminare gli avvisi specifici per Visual C\+\+  
  
1.  In **Esplora soluzioni**, selezionare il progetto o il file di origine in cui si desidera eliminare gli avvisi.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Pagine delle proprietà**.  
  
3.  Selezionare la categoria **Proprietà di configurazione**, selezionare la categoria **C\/C\+\+** quindi scegliere la pagina **Avanzata**.  
  
4.  Effettuare uno dei passaggi riportati di seguito:  
  
    -   Nella casella **Disabilita avvisi specifici**, specificare i codici di errore di avvisi da eliminare, separati da un punto e virgola.  
  
    -   Nella casella **Disabilita avvisi specifici**, scegliere **Modifica** per visualizzare ulteriori opzioni.  
  
5.  Scegliere il pulsante **OK** quindi ricompilare la soluzione.  
  
## Eliminare gli avvisi per Visual Basic  
 È possibile nascondere gli avvisi del compilatore specifici di Visual Basic modificando il file CSPROJ per il progetto.  È inoltre possibile utilizzare [Compilare la pagina, progettazione progetti](../ide/reference/compile-page-project-designer-visual-basic.md) per eliminare gli avvisi per categoria.  Per ulteriori informazioni, vedere [Configurazione degli avvisi in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
#### Per eliminare gli avvisi specifici di Visual Basic  
  
1.  In **Esplora soluzioni**, selezionare il progetto in cui si desidera eliminare gli avvisi.  
  
2.  Sulla barra dei menu, scegliere **Progetto**, **Scarica progetto**.  
  
3.  In **Esplora soluzioni**, scegliere dal menu di scelta rapida del progetto e quindi scegliere **Modifica***ProjectName***vbproj**.  
  
     Il file di progetto viene aperto nell'editor di codice.  
  
4.  Individuare l'elemento di `<NoWarn></NoWarn>` nella configurazione della build con cui viene compilata.  
  
     Nell'esempio seguente viene illustrato l'elemento di `<NoWarn></NoWarn>` in grassetto per la configurazione di compilazione di debug su una piattaforma x86:  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn> </NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
5.  Aggiungere uno o più numeri di avviso come valore dell'elemento di `<NoWarn>`.  Se si specificano numeri di avviso più, separarli con una virgola, come illustrato di seguito.  
  
    ```  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|x86' ">  
        <PlatformTarget>x86</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineDebug>true</DefineDebug>  
        <DefineTrace>true</DefineTrace>  
        <ErrorReport>prompt</ErrorReport>  
        <NoWarn>40059,42024</NoWarn>  
        <WarningLevel>1</WarningLevel>  
      </PropertyGroup>  
    ```  
  
6.  Salvare le modifiche al file CSPROJ.  
  
7.  Sulla barra dei menu, scegliere **Progetto**, **Ricarica progetto**.  
  
8.  Sulla barra dei menu, scegliere **Compila**, **Ricompila soluzione**.  
  
     La finestra **Output** più non sono visualizzati gli avvisi specificato.  
  
 Per ulteriori informazioni, vedere [\/nowarn](/dotnet/visual-basic/reference/command-line-compiler/nowarn).  
  
## Vedere anche  
 [Procedura dettagliata: compilazione di un'applicazione](../ide/walkthrough-building-an-application.md)   
 [Procedura: visualizzare, salvare e configurare file di log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md)   
 [Compilazione di applicazioni in Visual Studio](../ide/compiling-and-building-in-visual-studio.md)