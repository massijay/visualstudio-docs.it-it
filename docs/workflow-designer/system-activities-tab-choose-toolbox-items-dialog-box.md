---
title: "Scheda System.Activities, finestra di dialogo Scegli elementi della Casella degli strumenti | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS"
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS"
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Scheda System.Activities, finestra di dialogo Scegli elementi della Casella degli strumenti
In questa scheda della finestra di dialogo **Scegli elementi della Casella degli strumenti** è visualizzato un elenco delle attività, dei modelli e degli elementi di [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] disponibili.Per visualizzare l'elenco, scegliere **Scegli elementi della Casella degli strumenti** dal menu **Strumenti** oppure fare clic con il pulsante destro del mouse su **Casella degli strumenti** e scegliere **Scegli elementi** per visualizzare la finestra di dialogo **Scegli elementi della Casella degli strumenti**, quindi selezionare la scheda **System.Activities**.L'elenco include le attività del flusso di lavoro degli assembly System.Activities, System.ServiceModel.Activities e System.Activities.Core.Presentation, tuttavia per impostazione predefinita vengono controllate solo le attività fornite dal sistema mostrate e le attività aggiunte mediante altri assembly visualizzati nella **Casella degli strumenti**.Le ultime attività aggiunte vengono controllate automaticamente e visualizzate nella **Casella degli strumenti** quando si fa clic su **OK** nella finestra di dialogo.Tali elementi vengono inoltre visualizzati nella **Casella degli strumenti** sotto una nuova categoria che corrisponde allo spazio dei nomi in cui risiede l'attività, l'elemento o il modello.  
  
> [!WARNING]
>  Se si prova ad aggiungere un assembly che non contiene attività del flusso di lavoro, viene visualizzata una finestra di errore in cui si segnala che l'assembly non contiene attività.  
  
 Tale finestra di dialogo è indipendente dal progetto e pertanto la scheda **System.Activities** continua a presentarsi in un tipo di progetto non del flusso di lavoro o XAML autonomo.  
  
 Il filtro viene applicato in ogni scheda.Ciò significa che non è possibile aggiungere attività del flusso di lavoro mediante la scheda **Componente .NET**.È necessario aggiungerle mediante la scheda **System.Activities** stessa.  
  
 È possibile deselezionare qualsiasi elemento che non si desidera visualizzare nella **Casella degli strumenti** da questa scheda della finestra di dialogo. In alternativa, è possibile eseguire questa operazione utilizzando l'opzione del menu di scelta rapida **Elimina** nella **Casella degli strumenti**. Eliminando il riferimento a un assembly, l'elemento non viene rimosso dalla **Casella degli strumenti**.  
  
 Quando si crea un'istanza dell'attività trascinandola e rilasciandola nella finestra di progettazione, si aggiunge automaticamente all'elenco degli assembly di riferimento l'assembly che contiene l'elemento.Se inoltre l'attività fa riferimento a un assembly C, C non viene aggiunto all'elenco di assembly di riferimento.L'assembly C deve trovarsi nella GAC o nella stessa directory dell'attività B.Nel caso autonomo, l'assembly deve trovarsi nella GAC o nei percorsi di probe di VS.È quindi possibile trascinare solo e rilasciare le attività nell'area di Progettazione flussi di lavoro.  
  
 Le impostazioni della **Casella degli strumenti** vengono salvate per impostazione predefinita come opzioni utente, pertanto alla successiva apertura della **Casella degli strumenti** viene visualizzato l'elenco personalizzato delle attività del flusso di lavoro.Uno degli effetti collaterali di questa situazione è che, se sono stati aggiunti gli elementi specifici del dominio alla **Casella degli strumenti** mediante la finestra di dialogo **Scegli elementi della Casella degli strumenti**, tali elementi continueranno a essere visualizzati anche se si lavora in un'applicazione console flusso di lavoro.Se non si desidera visualizzarli, è possibile eliminarli utilizzando il menu di scelta rapida oppure deselezionarli nella finestra di dialogo **Scegli elementi della Casella degli strumenti**, come indicato precedentemente.  
  
 Le colonne di questa finestra di dialogo includono le informazioni seguenti:  
  
 Nome  
 Elenca i nomi delle attività del flusso di lavoro attualmente registrate nel computer locale.  
  
 Spazio dei nomi  
 Visualizza la gerarchia dello spazio dei nomi della libreria di classi .NET Framework che definisce la struttura dell'attività.  
  
 Nome assembly  
 Visualizza il nome e la versione dell'assembly .NET Framework che include l'attività.  
  
 Directory  
 Visualizza il percorso dell'assembly .NET Framework che include le attività del flusso di lavoro.Gli assembly si trovano, per impostazione predefinita, nella cartella Global Assembly Cache.  
  
 Per ordinare i componenti elencati, selezionare una delle intestazioni di colonna.