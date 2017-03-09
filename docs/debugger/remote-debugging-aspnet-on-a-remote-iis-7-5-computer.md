---
title: "Debug remoto di ASP.NET in un computer remoto con IIS 7.5 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "hero-article"
ms.assetid: 573a3fc5-6901-41f1-bc87-557aa45d8858
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug remoto di ASP.NET in un computer remoto con IIS 7.5
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile distribuire un'applicazione Web ASP.NET in un computer Windows Server 2008 R2 con IIS 7.5 e configurarla per il debug remoto. Le istruzioni seguenti illustrano come installare e configurare un'applicazione Visual Studio 2015 MVC 4.5.2.  
  
## Creare l'applicazione nel computer di Visual Studio  
  
1.  Creare una nuova applicazione MVC ASP.NET \(**File\/Nuovo\/Progetto**, quindi selezionare **Visual C\#\/Web\/Applicazione Web ASP.NET**. Nella sezione modelli **ASP.NET 4.5.2** selezionare **MVC**. Annullare la pagina **Configurare l'app Web di Microsoft Azure**. \) e denominarla **MyMVC**.  
  
2.  Aprire il file HomeController.cs e impostare un punto di interruzione nel metodo `About()`.  
  
3.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Pubblica**.  
  
4.  Per **Selezionare una destinazione di pubblicazione** selezionare **Personalizzato** e denominare il profilo **MyMVC**. Scegliere **Avanti**.  
  
5.  Nella scheda **Connessione** impostare il campo **Metodo di pubblicazione** su **File System** e il campo **Percorso di destinazione** su una directory locale. Scegliere **Avanti**.  
  
6.  Impostare la configurazione su **Debug**. Fare clic su **Pubblica**.  
  
     L'applicazione verrà pubblicata nella directory locale.  
  
## Distribuire l'applicazione nel computer remoto di Windows Server  
 In questa sezione si presuppone che nel computer Windows Server 2008 R2 sia già abilitato IIS.  
  
1.  Installare ASP.NET:  
  
     **C:\\Windows\\Microsoft.NET\\Framework\(64\)\\v4.0.30319\\aspnet\_regiis.exe \-ir**  
  
2.  Copiare la directory del progetto ASP.NET dal computer di Visual Studio in una directory locale \(denominata **C:\\Publish**\) nel computer Windows Server.  
  
3.  Assicurarsi che il file web.config riporti la versione corretta di .NET Framework.  La versione di .NET Framework installata per impostazione predefinita nel computer è 4.0.30319, mentre è stata creata una versione ASP.NET 4.5.2. Se questa versione non è installata nel computer Windows Server, è necessario modificare la versione:  
  
    ```xml  
    <system.web> <authentication mode="None" /> <compilation debug="true" targetFramework="4.0.30319" /> <httpRuntime targetFramework="4.0.30319" /> </system.web>  
  
    ```  
  
4.  Aprire **Gestione Internet Information Services \(IIS\)** e andare in **Siti**.  
  
5.  Fare clic con il pulsante destro del mouse sul nodo **Sito Web predefinito** e scegliere **Aggiungi applicazione**.  
  
6.  Impostare il campo **Alias** su **MyMVC** e il campo Pool di applicazioni su **ASP.NET v 4.0**. Impostare il **Percorso fisico** su **C:\\Publish** \(dove è stata copiata la directory del progetto ASP.NET\).  
  
7.  Per testare la distribuzione, fare clic con il pulsante destro del mouse su **Sito Web predefinito** e scegliere **Sfoglia**. Verrà visualizzata la pagina Web.  
  
## Installare il debugger remoto nel computer Windows Server  
 Per istruzioni su come scaricare il debugger remoto, vedere [Debug remoto](../debugger/remote-debugging.md).  
  
 Per eseguire il debug remoto delle applicazioni ASP.NET, è possibile avviare il debugger remoto come servizio o eseguire l'applicazione del debugger remoto come amministratore. Informazioni dettagliate su come eseguire il debugger remoto come servizio sono disponibili in [Debug remoto](../debugger/remote-debugging.md).  
  
## Connettersi all'applicazione ASP.NET dal computer di Visual Studio  
  
-   Nel computer di Visual Studio aprire la soluzione **MyMVC**.  
  
-   In Visual Studio fare clic su **Debug\/Connetti a processo**.  
  
-   Impostare il campo Qualificatore su **\<nome computer remoto\>:4020**.  
  
-   Nella finestra **Processi disponibili** verranno visualizzati alcuni processi.  
  
-   Selezionare **Mostra i processi di tutti gli utenti**.  
  
-   Cercare **w3wp.exe** e fare clic su **Connetti**.  
  
-   Aprire il sito Web del computer remoto. In un browser passare a **http:\/\/\<nome computer remoto\>**.  
  
-   Verrà visualizzata la pagina Web ASP.NET. Fare clic su **Informazioni su**.  
  
     Il punto di interruzione verrà raggiunto in Visual Studio.