---
title: "&#200; necessario abilitare in modo esplicito l&#39;accesso al sistema di progetto di Microsoft Office Visual Basic, Applications Edition prima di creare o aprire un progetto di Visual Studio Tools per Microsoft Office System | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vst.project.vbawrongversion"
  - "VST.Project.VBASecurityGenericError"
  - "VST.Project.VBASecurityPermissions"
  - "VST.SelectDocWizard.MissingCOM"
  - "VST.Project.VBASecurityNotSet"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 538021e6-1776-453d-9899-d7fca2f1f58f
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# &#200; necessario abilitare in modo esplicito l&#39;accesso al sistema di progetto di Microsoft Office Visual Basic, Applications Edition prima di creare o aprire un progetto di Visual Studio Tools per Microsoft Office System
  I progetti di sviluppo di Office richiedono l'accesso al sistema di progetto di Visual Basic, Applications Edition in Microsoft Office Word e Microsoft Office Excel, anche se i progetti non usano Visual Basic, Applications Edition.  Il supporto in fase di progettazione dei controlli sia nei progetti di Visual Basic che in quelli di Visual C\# dipende infatti dal sistema di progetto di Visual Basic, Applications Edition.  
  
 Alcuni virus macro per Microsoft Office provano ad automatizzare il sistema di progetto di Visual Basic, Applications Edition per propagarsi.  Abilitando l'accesso al sistema di progetto di Visual Basic, Applications Edition, si rimuove una protezione utile contro la diffusione dei virus macro.  Rimangono tuttavia attivi i normali livelli di sicurezza delle macro, che, assieme all'elenco degli autori attendibili impostati per le applicazioni di Office, determineranno l'esecuzione delle macro nel computer.  
  
> [!NOTE]  
>  Tale condizione si applica solo al computer di sviluppo.  Nei computer degli utenti finali non è necessario abilitare questa opzione per eseguire le soluzioni Office.  
  
 È importante notare che la disabilitazione dell'accesso al sistema di progetto di Visual Basic, Applications Edition non comporta da sola la protezione dai virus, ma consente semplicemente di interrompere la diffusione di alcuni virus ad altri documenti se il computer viene infettato da un virus macro.  Per impostazione predefinita, l'opzione è disabilitata per fornire un ulteriore livello di sicurezza per il computer, ma la sua abilitazione non rende il computer maggiormente soggetto ai virus se si seguono le procedure di sicurezza consigliate.  
  
 La migliore protezione contro i virus macro per Office consiste nell'eseguire Office con un livello di sicurezza Elevato o Molto elevato, nel ritenere attendibili solo le macro provenienti da origini verificate e nell'aggiornare patch di sicurezza e programmi antivirus.  
  
 Per altre informazioni sulla protezione del PC da virus e codice dannoso, vedere [http:\/\/www.microsoft.com\/protect](http://www.microsoft.com/protect).  
  
 È possibile abilitare o disabilitare manualmente l'opzione **Considera attendibile l'accesso al progetto Visual Basic**.  
  
 È possibile ripristinare l'installazione di Office se vengono visualizzati errori VBA o COM.  
  
### Per abilitare o disabilitare l'accesso a progetti Visual Basic  
  
1.  Scegliere **Macro** dal menu **Strumenti** di Word o Excel, quindi fare clic su **Sicurezza**.  
  
2.  Nella finestra di dialogo **Sicurezza** fare clic sulla scheda **Editori attendibili**.  
  
3.  Selezionare la casella di controllo **Considera attendibile l'accesso al progetto Visual Basic** per abilitarla o deselezionarla per disabilitarla.  
  
4.  Fare clic su **OK**.  
  
### Per impostare il livello di sicurezza delle macro di Office  
  
1.  Scegliere **Macro** dal menu **Strumenti** di Word o Excel, quindi fare clic su **Sicurezza**.  
  
2.  Nella scheda **Livello di sicurezza** selezionare l'impostazione desiderata.  
  
     La scheda **Livello di sicurezza** contiene i dettagli su ciascun livello.  Per altre informazioni, vedere l'argomento "Livelli di sicurezza delle macro" nella Guida di Office.  
  
### Per installare VBA con Microsoft Office System 2007  
  
1.  Nel Pannello di controllo eseguire **Installazione applicazioni** o **Programmi e funzionalità**.  
  
2.  Selezionare Microsoft Office nell'elenco **Programmi attualmente installati**.  
  
3.  Fare clic su **Cambia**.  
  
4.  Selezionare **Aggiungi\/Rimuovi funzionalità**, quindi fare clic su **Continua**.  
  
5.  Selezionare **Personalizzazione avanzata applicazioni**, quindi fare clic su **Avanti**.  
  
6.  Espandere **Caratteristiche condivise di Office** nell'elenco **Scegliere le opzioni di aggiornamento per applicazioni e strumenti**.  
  
7.  Aprire il menu a discesa accanto a **Visual Basic, Applications Edition**, quindi fare clic su **Esecuzione dal computer locale**.  
  
8.  Scegliere **Continua**.  
  
9. Fare clic su **Chiudi**.  
  
### Per ripristinare l'installazione di Office  
  
1.  Nel Pannello di controllo eseguire **Installazione applicazioni** o **Programmi e funzionalità**.  
  
2.  Selezionare la versione di Office nell'elenco **Programmi attualmente installati**.  
  
3.  Fare clic su **Cambia**.  
  
4.  Selezionare **Reinstalla o ripristina**, quindi fare clic su **Avanti**.  
  
5.  Selezionare **Rileva problemi e ripristina l'installazione di Office**, quindi fare clic su **Installa**.  
  
## Vedere anche  
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  