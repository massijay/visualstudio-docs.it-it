---
title: "Modifiche necessarie per l&#39;esecuzione di progetti di Office migrati a .NET Framework 4 o a .NET Framework 4.5 | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "progetti Office [sviluppo per Office in Visual Studio], migrazione a .NET Framework 4"
ms.assetid: e2cd35cc-7731-428e-9046-34fc57a02c48
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Modifiche necessarie per l&#39;esecuzione di progetti di Office migrati a .NET Framework 4 o a .NET Framework 4.5
  Se il framework di destinazione di un progetto di Office viene modificata in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive da una versione precedente di.NET Framework, è necessario eseguire le attività seguenti per assicurarsi che la soluzione possa essere eseguita nel computer di sviluppo e nei computer degli utenti finali:  
  
-   Rimuovere l'oggetto <xref:System.Security.SecurityTransparentAttribute> dal progetto se è stato aggiornato da Visual Studio 2008.  
  
-   Eseguire un comando **Clean** in Visual Studio per poter eseguire o eseguire il debug del progetto nel computer di sviluppo.  
  
-   Aggiornare il prerequisito di .NET Framework per il progetto.  
  
-   Gli utenti finali devono anche reinstallare la soluzione se in precedenza è stata distribuita con ClickOnce prima dell'impostazione di un framework di destinazione diverso.  
  
 Per altre informazioni su queste attività, vedere le sezioni corrispondenti riportate di seguito.  
  
## Rimozione dell'attributo SecurityTransparent da progetti aggiornati da Visual Studio 2008  
 Se si aggiorna un progetto di Office da Visual Studio 2008 e il framework di destinazione del progetto viene successivamente modificato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario rimuovere <xref:System.Security.SecurityTransparentAttribute> dal progetto. Visual Studio non rimuove automaticamente questo attributo. Se non si rimuove questo attributo, viene visualizzato un messaggio di errore quando si compila il progetto.  
  
 Per altre informazioni sulle circostanze in cui Visual Studio può modificare il framework di destinazione di un progetto aggiornato a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], vedere [Aggiornamento e migrazione di soluzioni Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
#### Per rimuovere SecurityTransparentAttribute  
  
1.  Con il progetto aperto in Visual Studio, aprire **Esplora soluzioni**.  
  
2.  Nel nodo **Proprietà** \(per C\#\) o **Progetto personale** \(per Visual Basic\) fare doppio clic sul file di codice AssemblyInfo per aprirlo nell'editor di codice.  
  
    > [!NOTE]  
    >  Per visualizzare il file di codice AssemblyInfo nei progetti di Visual Basic, è necessario fare clic sul pulsante **Mostra tutti i file** in **Esplora soluzioni**.  
  
3.  Individuare <xref:System.Security.SecurityTransparentAttribute> e rimuoverlo dal file o impostarlo come commento.  
  
    ```vb  
    <Assembly: SecurityTransparent()>  
    ```  
  
    ```csharp  
    [assembly: SecurityTransparent()]  
    ```  
  
## Esecuzione del comando Pulisci per eseguire il debug o eseguire un progetto nel computer di sviluppo  
 Se un progetto di Office è stato compilato prima che il framework di destinazione del progetto venisse modificato in [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario eseguire un comando **Pulisci** quindi ricompilare il progetto dopo la modifica del framework di destinazione.  Se non si esegue un comando **Pulisci**, verrà generata un'eccezione <xref:System.Runtime.InteropServices.COMException> al tentativo di eseguire il debug o di eseguire il progetto la cui destinazione è stata modificata.  
  
 Per altre informazioni sul comando **Pulisci**, vedere [Compilazione di soluzioni Office](../vsto/building-office-solutions.md).  
  
## Aggiornamento dei prerequisiti per la distribuzione  
 Quando si destina un progetto di Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, è necessario aggiornare il prerequisito di.NET Framework corrispondente nella finestra di dialogo **Prerequisiti**.  In caso contrario, i controlli di progetto limited di InstallShield la distribuzione ClickOnce o per e installa una versione precedente di .NET Framework.  
  
 Per altre informazioni sull'aggiornamento dei prerequisiti per la distribuzione ai computer degli utenti finali, vedere [Procedura: installare i prerequisiti nei computer degli utenti finali per l'esecuzione delle soluzioni Office](http://msdn.microsoft.com/it-it/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98).  
  
## Reinstallazione di soluzioni nei computer degli utenti finali  
 Se si usa ClickOnce per distribuire una soluzione Office destinata a .NET Framework 3.5 e quindi si modifica la destinazione del progetto a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o versioni successive, gli utenti finali devono disinstallare la soluzione e reinstallarla dopo averla ripubblicata.  Se si ripubblica la soluzione di cui è stata reimpostata la destinazione e la soluzione viene aggiornata nei computer degli utenti finali, questi ultimi riceveranno un'eccezione <xref:System.Runtime.InteropServices.COMException> all'esecuzione della soluzione aggiornata.  
  
## Vedere anche  
 [Migrazione di soluzioni Office a .NET Framework 4 o versioni successive](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)  
  
  