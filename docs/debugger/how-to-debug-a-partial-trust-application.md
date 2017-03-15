---
title: "Procedura: eseguire il debug di un&#39;applicazione parzialmente attendibile | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug [Visual Studio], applicazioni parzialmente attendibili"
  - "applicazioni parzialmente attendibili"
  - "sicurezza [Visual Studio], applicazioni parzialmente attendibili"
ms.assetid: 9d30ad92-28ce-4b21-91d8-698474cddf64
caps.latest.revision: 25
caps.handback.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: eseguire il debug di un&#39;applicazione parzialmente attendibile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le informazioni contenute in questo argomento sono valide per applicazioni Windows e console  
  
 La [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md) semplifica la distribuzione di applicazioni parzialmente attendibili che sfruttano la [Code Access Security](../Topic/Code%20Access%20Security.md) per consentire l'accesso solamente alle risorse di un computer.  
  
 Il debug di un'applicazione parzialmente attendibile può essere complesso perché queste applicazioni hanno autorizzazioni di sicurezza diverse e si comportano quindi in modo diverso in base all'area dalla quale viene eseguita l'installazione.  Se l'installazione viene eseguita da Internet, un'applicazione parzialmente attendibile disporrà di poche autorizzazioni.  Se l'installazione viene eseguita da una rete Intranet locale, avrà un numero di autorizzazioni maggiore. Se l'installazione viene eseguita dal computer locale, avrà autorizzazioni complete.  È inoltre possibile configurare aree personalizzate con autorizzazioni personalizzate.  Potrebbe essere necessario eseguire il debug di un'applicazione parzialmente attendibile in una o più di queste condizioni.  In Visual Studio sono disponibili strumenti che semplificano anche questo tipo di debug.  
  
 Prima di avviare una sessione di debug in Visual Studio, è possibile scegliere un'area dalla quale simulare l'installazione dell'applicazione.  Quando si avvia il debug, verranno assegnate automaticamente le autorizzazioni appropriate per un'applicazione parzialmente attendibile installata da tale area.  In questo modo è possibile controllare il comportamento che avrà l'applicazione quando verrà scaricata da tale area da un utente.  
  
 Se l'applicazione tenta di eseguire un'operazione per cui non dispone della necessaria autorizzazione, verrà generata un'eccezione.  A questo punto sarà possibile scegliere di aggiungere una nuova autorizzazione tramite la funzionalità Informazioni sulle eccezioni, in modo da poter riavviare la sessione di debug con autorizzazioni sufficienti per evitare il problema.  
  
 È possibile controllare successivamente le autorizzazioni aggiunte durante il debug.  Se durante il debug è stato necessario assegnare un'ulteriore autorizzazione, probabilmente occorrerà aggiungere una richiesta di consenso dell'utente in tale punto del codice.  
  
> [!NOTE]
>  Per i visualizzatori del debugger sono richiesti maggiori privilegi rispetto a quelli consentiti da un'applicazione parzialmente attendibile.  I visualizzatori non vengono caricati in caso di interruzione in codice con attendibilità parziale.  Per eseguire il debug tramite un visualizzatore, è necessario eseguire il codice con attendibilità totale.  
  
### Per scegliere un'area per l'applicazione parzialmente attendibile  
  
1.  Scegliere **Proprietà** di *Projectname* dal menu **Progetto**.  
  
2.  Nelle pagine delle proprietà di *Projectname* fare clic sulla pagina **Sicurezza**.  
  
3.  Selezionare **Attiva le impostazioni di sicurezza ClickOnce**.  
  
4.  In **Area da cui verrà installata l'applicazione** fare clic sulla casella di riepilogo a discesa e selezionare l'area dalla quale si desidera simulare l'installazione dell'applicazione.  
  
     Nella griglia **Autorizzazioni necessarie all'applicazione** sono indicate tutte le autorizzazioni disponibili.  Le autorizzazioni assegnate all'applicazione sono contrassegnate con un segno di spunta.  
  
5.  Se si sceglie l'area **\(Personalizzata\)**, selezionare le impostazioni personalizzate adeguate nella colonna **Impostazione** della griglia **Autorizzazioni**.  
  
6.  Scegliere **OK** per chiudere le pagine delle proprietà.  
  
### Per aggiungere un'autorizzazione quando si verifica un'eccezione di sicurezza  
  
1.  Verrà visualizzata la finestra di dialogo **Informazioni sulle eccezioni** contenente il messaggio: SecurityException non gestita.  
  
2.  Nella finestra di dialogo **Informazioni sulle eccezioni** fare clic su **Aggiungi autorizzazione al progetto** in **Azioni**.  
  
3.  Verrà visualizzata la finestra di dialogo **Riavvia debug**.  
  
    -   Se si desidera riavviare la sessione di debug con la nuova autorizzazione, scegliere **Sì**.  
  
    -   Se non si desidera riavviare la sessione di debug immediatamente, scegliere **No**.  
  
### Per visualizzare le autorizzazioni aggiunte durante il debug  
  
1.  Scegliere **Proprietà** di *Projectname* dal menu **Progetto**.  
  
2.  Nelle pagine delle proprietà di *Projectname* fare clic sulla pagina **Sicurezza**.  
  
3.  Esaminare la griglia **Autorizzazioni necessarie all'applicazione**.  Le autorizzazioni aggiunte sono contrassegnate con due icone nella colonna **Inclusa**: il segno di spunta normale, utilizzato per tutte le autorizzazioni incluse, e un'icona aggiuntiva a forma di fumetto con una lettera "i".  
  
4.  Utilizzare la barra di scorrimento verticale per visualizzare l'intera griglia **Autorizzazioni necessarie all'applicazione**.  
  
## Vedere anche  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)