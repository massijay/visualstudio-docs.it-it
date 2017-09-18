---
title: "Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "assemblies, downloading [ClickOnce]"
  - "ClickOnce deployment, on-demand download"
  - "on-demand assemblies, ClickOnce"
ms.assetid: d20e2789-8621-4806-b5b7-841122da1456
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per impostazione predefinita, tutti gli assembly inclusi in un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono scaricati alla prima esecuzione dell'applicazione.  È tuttavia possibile che alcune parti dell'applicazione vengano utilizzate solo da un gruppo limitato di utenti.  In questo caso è preferibile scaricare un assembly solo quando viene creato uno dei relativi tipi.  Nella procedura dettagliata riportata di seguito vengono illustrate le operazioni da eseguire per impostare come facoltativi determinati assembly inclusi nell'applicazione nonché per scaricarli utilizzando le classi dello spazio dei nomi <xref:System.Deployment.Application>, quando richiesti da Common Language Runtime \(CLR\).  
  
> [!NOTE]
>  L'applicazione dovrà essere eseguita in condizioni di attendibilità totale per utilizzare questa procedura.  
  
## Prerequisiti  
 Per completare questa procedura dettagliata, è necessario disporre di uno dei componenti seguenti:  
  
-   Windows SDK,  scaricabile dall'Area download Microsoft.  
  
-   Visual Studio.  
  
## Creazione dei progetti  
  
#### Per creare un progetto che utilizza un assembly su richiesta  
  
1.  Creare una directory denominata ClickOnceOnDemand.  
  
2.  Aprire il prompt dei comandi di Windows SDK o di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Passare alla directory ClickOnceOnDemand.  
  
4.  Generare una coppia di chiavi pubblica\/privata utilizzando il comando seguente:  
  
    ```  
    sn -k TestKey.snk  
    ```  
  
5.  Utilizzando il Blocco note o un altro editor di testo, definire una classe `DynamicClass` con una singola proprietà `Message`.  
  
     [!code-vb[ClickOnceLibrary#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.vb)]
     [!code-cs[ClickOnceLibrary#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_1.cs)]  
  
6.  A seconda del linguaggio utilizzato, salvare il testo con il nome `ClickOnceLibrary.cs` o `ClickOnceLibrary.vb` nella directory ClickOnceOnDemand.  
  
7.  Compilare il file in un assembly.  
  
    ```c#  
    csc /target:library /keyfile:TestKey.snk ClickOnceLibrary.cs  
    ```  
  
    ```vb#  
    vbc /target:library /keyfile:TestKey.snk ClickOnceLibrary.vb  
    ```  
  
8.  Per ottenere il token della chiave pubblica per l'assembly, utilizzare il comando seguente:  
  
    ```  
    sn -T ClickOnceLibrary.dll  
    ```  
  
9. Creare un nuovo file utilizzando l'editor di testo e immettere il codice riportato di seguito.  Questo codice crea un'applicazione Windows Form che scarica l'assembly ClickOnceLibrary quando è richiesto.  
  
     [!code-cs[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/CSharp/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.cs)]
     [!code-vb[ClickOnceOnDemandCmdLine#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api_2.vb)]  
  
10. Nel codice individuare la chiamata a <xref:System.Reflection.Assembly.LoadFile%2A>.  
  
11. Impostare `PublicKeyToken` sul valore recuperato in precedenza.  
  
12. Salvare il file come `Form1.cs` o `Form1.vb`.  
  
13. Compilarlo in un eseguibile utilizzando il comando seguente:  
  
    ```c#  
    csc /target:exe /reference:ClickOnceLibrary.dll Form1.cs  
    ```  
  
    ```vb#  
    vbc /target:exe /reference:ClickOnceLibrary.dll Form1.vb  
    ```  
  
## Impostazione degli assembly come facoltativi  
  
#### Per impostare come facoltativi gli assembly nell'applicazione ClickOnce mediante MageUI.exe  
  
1.  Utilizzando MageUI.exe, creare un manifesto di applicazione come descritto nella sezione [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Specificare quindi le impostazioni seguenti :  
  
    -   Assegnare al manifesto dell'applicazione il nome `ClickOnceOnDemand`.  
  
    -   Nella riga ClickOnceLibrary.dll della pagina **File** impostare la colonna **Tipo file** su **Nessuno**.  
  
    -   Nella riga ClickOnceLibrary.dll della pagina **File** digitare `ClickOnceLibrary.dll` nella colonna **Gruppo**.  
  
2.  Utilizzando MageUI.exe, creare un manifesto di distribuzione come descritto nella sezione [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Specificare quindi le impostazioni seguenti:  
  
    -   Assegnare al manifesto di distribuzione il nome `ClickOnceOnDemand`.  
  
## Test del nuovo assembly  
  
#### Per testare l'assembly su richiesta  
  
1.  Caricare la distribuzione di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] su un server Web.  
  
2.  Avviare l'applicazione distribuita con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] da un browser Web immettendo l'URL del manifesto di distribuzione.  Se all'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] è stato assegnato il nome `ClickOnceOnDemand` e l'applicazione viene caricata nella directory radice di adatum.com, l'URL sarà simile al seguente:  
  
    ```  
    http://www.adatum.com/ClickOnceOnDemand/ClickOnceOnDemand.application  
    ```  
  
3.  Quando viene visualizzato il form principale, scegliere il controllo <xref:System.Windows.Forms.Button>.  Verrà visualizzata una finestra di messaggio contenente la stringa "Hello, World\!".  
  
## Vedere anche  
 <xref:System.Deployment.Application.ApplicationDeployment>