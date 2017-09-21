---
title: "Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API Using the Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "Windows Forms, globalization"
  - "ClickOnce deployment, globalization"
  - "localization, Windows Forms"
  - "ClickOnce, on-demand download"
  - "Windows Forms, localization"
  - "ClickOnce deployment, localization"
  - "walkthroughs, localization"
ms.assetid: 82b85a47-b223-4221-a17c-38a52c3fb6e2
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API Using the Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le applicazioni Windows Form possono essere configurate per più impostazioni cultura con l'uso di assembly satellite.  Un *assembly satellite* è un assembly in cui sono contenute risorse dell'applicazione per impostazioni cultura diverse da quelle predefinite dell'applicazione.  
  
 Come descritto in [Localizing ClickOnce Applications](../deployment/localizing-clickonce-applications.md), è possibile includere più assembly satellite per più impostazioni cultura all'interno della stessa distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Per impostazione predefinita, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] scaricherà tutti gli assembly satellite nella distribuzione nel computer client, anche se probabilmente un singolo client richiederà un solo assembly satellite.  
  
 Questa procedura dettagliata descrive come contrassegnare gli assembly satellite come facoltativi e scaricare solo l'assembly di cui un computer client ha bisogno per le impostazioni cultura correnti.  
  
> [!NOTE]
>  Ai fini dell'esecuzione del test, nei seguenti esempi di codice viene specificato `ja-JP` a livello di codice per le impostazioni cultura.  Per informazioni su come modificare il codice per un ambiente di produzione, vedere la sezione "Passaggi successivi" più avanti in questo argomento.  
  
### Per contrassegnare gli assembly satellite come facoltativi  
  
1.  Compilazione del progetto.  In questo modo verranno generati gli assembly satellite per tutte le impostazioni cultura in cui si sta eseguendo la localizzazione.  
  
2.  Fare clic con il pulsante destro del mouse sul nome del progetto in Esplora soluzioni, quindi scegliere **Proprietà**.  
  
3.  Fare clic sulla scheda **Pubblica**, quindi su **File applicazione**.  
  
4.  Selezionare la casella di controllo **Mostra tutti i file** per visualizzare gli assembly satellite.  Per impostazione predefinita, tutti gli assembly satellite verranno inclusi nella distribuzione e saranno visibili in questa finestra di dialogo.  
  
     I nomi degli assembly satellite sono strutturati come segue: *CodiceIso*\\NomeApplicazione.resources.dll, dove *CodiceIso* è un'identificatore del linguaggio in formato RFC 1766.  
  
5.  Scegliere **Nuovo...** nell'elenco **Gruppo di download** per ogni identificatore del linguaggio.  Quando viene richiesto di specificare un nome per il gruppo di download, immettere l'identificatore del linguaggio.  Per un assembly satellite giapponese, ad esempio, specificare `ja-JP`.  
  
6.  Chiudere la finestra di dialogo **File applicazione**.  
  
### Per scaricare assembly satellite su richiesta in C\#  
  
1.  Aprire il file Program.cs.  Se questo file non è visualizzato in Esplora soluzioni, selezionare il progetto e scegliere **Mostra tutti i file** dal menu **Progetto**.  
  
2.  Usare il codice seguente per scaricare l'assembly satellite appropriato e avviare l'applicazione.  
  
     [!code-cs[ClickOnce.SatelliteAssemblies#1](../deployment/codesnippet/CSharp/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_1.cs)]  
  
### Per scaricare assembly satellite su richiesta in Visual Basic  
  
1.  Fare clic sulla scheda **Applicazione** nella finestra **Proprietà** dell'applicazione.  
  
2.  Nella parte inferiore della pagina della scheda, scegliere **Visualizza eventi di applicazioni**.  
  
3.  Nella parte iniziale del file ApplicationEvents.VB, aggiungere i seguenti riferimenti importati.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#1](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_2.vb)]  
  
4.  Aggiungere il codice seguente alla classe `MyApplication`.  
  
     [!code-vb[ClickOnce.SatelliteAssembliesVB#2](../deployment/codesnippet/VisualBasic/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer_3.vb)]  
  
## Passaggi successivi  
 In un ambiente di produzione sarà probabilmente necessario rimuovere la riga degli esempi di codice usata per impostare la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> su un valore specifico, perché il valore predefinito per i computer client è quello corretto.  Quando l'applicazione è in esecuzione su un computer client giapponese, ad esempio, la proprietà predefinita <xref:System.Threading.Thread.CurrentUICulture%2A> sarà `ja-JP`.  L'impostazione di tale proprietà a livello di codice è un buon metodo per procedere alla verifica degli assembly satellite prima di distribuire l'applicazione.  
  
## Vedere anche  
 [Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)   
 [Localizing ClickOnce Applications](../deployment/localizing-clickonce-applications.md)