---
title: "Pagina Debug, Progettazione progetti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesDebug"
helpviewer_keywords: 
  - "Creazione progetti, pagina Debug"
  - "Pagina Debug in Creazione progetti"
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Pagina Debug, Progettazione progetti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!WARNING]
>  Questo argomento non si applica alle applicazioni di archivio di Windows.  Vedere [Avviare una sessione di debug \(VB, C\#, C\+\+ e XAML\)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) in Windows Dev Center.  
  
 Utilizzare la pagina **DebugProgettazione progetti** per impostare le proprietà per eseguire il debug del comportamento in un progetto C\# o Visual Basic.  
  
 Per accedere alla pagina **Debug**, selezionare un nodo di progetto in **Esplora soluzioni**.  Scegliere dal menu **Progetto**, scegliere *ProjectName***Proprietà**.  Quando **Progettazione progetti** viene visualizzato, fare clic sulla scheda **Debug**.  
  
## Configurazione e piattaforma  
 Le seguenti opzioni consentono di selezionare la configurazione e la piattaforma da visualizzare o modificare.  
  
 **Configurazione**  
 Specifica le impostazioni di configurazione da visualizzare o modificare.  Le impostazioni possono essere **Debug** \(impostazione predefinita\), **Release**, o **Tutte le configurazioni**.  Per ulteriori informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
 **Piattaforma**  
 Specifica le impostazioni della piattaforma da visualizzare o modificare.  Le opzioni possono includere **Qualsiasi CPU** \(impostazione predefinita\), **x64**e **x86**.  Per ulteriori informazioni, vedere [Debug and Release Project Configurations](http://msdn.microsoft.com/it-it/0440b300-0614-4511-901a-105b771b236e).  
  
## Azione di avvio  
 L'**Azione di avvio** indica l'elemento da avviare una volta eseguito il debug dell'applicazione: il progetto, un programma personalizzato, un URL o nessun elemento.  Per impostazione predefinita, questa opzione è impostata su **Avvia progetto**.  **Azione di avvio** Che imposta la pagina **Debug** determina il valore della proprietà `StartAction`.  
  
 **Avvia progetto**  
 Scegliere questa opzione per specificare che il file eseguibile \(per i progetti di applicazione console e di applicazione Windows\) deve essere avviato quando l'applicazione viene eseguito il debug.  Tale opzione è selezionata come impostazione predefinita.  
  
 **Avvia programma esterno**  
 Scegliere questa opzione per specificare che un programma specifico deve essere avviato quando l'applicazione viene eseguito il debug.  
  
 **Avvia il browser con URL**  
 Scegliere questa opzione per specificare che un determinato URL deve essere eseguito quando l'applicazione viene eseguito il debug.  
  
## Opzioni di avvio  
 **Argomenti della riga di comando**  
 In questa casella di testo, immettere gli argomenti della riga di comando da utilizzare per il debug.  
  
 **Cartella di lavoro**  
 In questa casella di testo, immettere la directory da cui il progetto verrà avviato  Oppure fare clic sul pulsante sfoglia \(**…**\) per selezionare una directory.  
  
 **Usa computer remoto**  
 Per eseguire il debug dell'applicazione da un computer remoto, selezionare questa casella di controllo e immettere il percorso nel computer remoto nella casella di testo.  
  
## Attiva debugger  
 **Attiva debug codice non gestito**  
 Questa opzione specifica se è supportato il debug del codice nativo.  Selezionare questa casella di controllo se si eseguono chiamate agli oggetti COM o se si avvia un programma personalizzato scritto in codice nativo che chiama il progetto ed eseguire il debug di codice nativo.  Deselezionare questa casella di controllo per disabilitare il debug del codice non gestito.  Per impostazione predefinita, questa casella di controllo è deselezionata.  
  
 **Attiva debug SQL Server**  
 Selezionare o deselezionare questa casella di controllo per abilitare o disabilitare il debug delle routine SQL dall'applicazione Visual Basic.  Per impostazione predefinita, questa casella di controllo è deselezionata.  
  
 **Attiva il processo di hosting di Visual Studio**  
 Selezionare questa casella di controllo per attivare il processo di hosting di Visual Studio.  Per impostazione predefinita, questa casella di controllo è selezionata.  Per ulteriori informazioni, vedere [Processo di hosting \(vshost.exe\)](../../ide/hosting-process-vshost-exe.md).  
  
 Per eseguire il debug in un'area di sicurezza, è necessario attivare questa opzione e **Esegui debug dell'applicazione con il set di autorizzazioni selezionato** in [Finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md).  
  
## Vedere anche  
 [Debug in Visual Studio](../../debugger/debugging-in-visual-studio.md)   
 [Impostazioni di progetto per le configurazioni di debug C\#](../../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Impostazioni di progetto per una configurazione di debug Visual Basic](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Managing Debugging Properties](http://msdn.microsoft.com/it-it/92474d16-e7fe-4fac-9287-6bd6b3a7eb68)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: creare e modificare le configurazioni](../../ide/how-to-create-and-edit-configurations.md)