---
title: "Registrazione degli eventi per le soluzioni Office"
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
  - "applicazioni di Office [sviluppo per Office in Visual Studio], Visualizzatore eventi"
  - "distribuzione ClickOnce [sviluppo per Office in Visual Studio], Visualizzatore eventi"
  - "distribuzione di applicazioni [sviluppo per Office in Visual Studio], Visualizzatore eventi"
  - "sviluppo per Office in Visual Studio, Visualizzatore eventi"
ms.assetid: 31a246fe-ce1c-4f0e-9a21-9cf974c247fe
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Registrazione degli eventi per le soluzioni Office
  È possibile usare il Visualizzatore eventi di Windows per visualizzare i messaggi di eccezione acquisiti da [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] quando si installano o disinstallano soluzioni Office. Questi messaggi del registratore eventi possono essere usati per risolvere i problemi di installazione e di distribuzione.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Lettura del registro eventi  
 Aprire il **Visualizzatore eventi** e applicare un filtro per visualizzare solo gli eventi desiderati.  
  
#### Per leggere il registro eventi in Windows Server 2003 e Windows XP  
  
1.  Aprire **Strumenti di amministrazione** nel Pannello di controllo.  
  
2.  Avviare il **Visualizzatore eventi**.  
  
3.  Nell'elenco dei registri eventi, selezionare **Applicazione**.  
  
4.  Scegliere **Filtro** dal menu **Visualizza**.  
  
5.  Selezionare **VSTO 4.0** nell'elenco **Origine evento**.  
  
6.  Per gli eventi di installazione, digitare **4096** nella casella **ID evento**.  
  
7.  Fare clic su **OK** per visualizzare l'elenco filtrato.  
  
#### Per leggere il registro eventi in Windows 7, Windows Vista e Windows Server 2008  
  
1.  Aprire **Strumenti di amministrazione** nel Pannello di controllo.  
  
2.  Avviare il **Visualizzatore eventi**.  
  
3.  Espandere **Registri di Windows**.  
  
4.  Nell'elenco dei registri eventi, selezionare **Applicazione**.  
  
5.  Scegliere  **Filtro registro corrente** dal menu **Azione**.  
  
6.  Selezionare **VSTO 4.0** nell'elenco **Origine evento**.  
  
7.  Per gli eventi di installazione, digitare **4096** nella casella **ID evento**.  
  
8.  Fare clic su **OK** per visualizzare l'elenco filtrato.  
  
 Il Visualizzatore eventi include le informazioni seguenti:  
  
-   Il percorso del manifesto della distribuzione per la soluzione.  
  
-   Un messaggio che descrive la causa dell'errore o dell'eccezione.  
  
 Questi messaggi di eccezione possono consentire di determinare la causa di un problema di installazione, ad esempio un certificato o un percorso di documento non attendibile oppure un manifesto della distribuzione non valido.  
  
 Dopo la disinstallazione di una soluzione Office, i messaggi di eccezione rimangono nel registro eventi.  
  
 Per informazioni su come visualizzare o registrare messaggi di eccezione quando una soluzione Office è in esecuzione, vedere [Debug di progetti di Office](../vsto/debugging-office-projects.md) e [Debug di progetti di Office](../vsto/debugging-office-projects.md).  
  
### Localizzazione  
 Il linguaggio del messaggio di eccezione viene determinato dal linguaggio di runtime di Visual Studio Tools per Office. Ad esempio, se nel computer dell'utente finale è stato installato il Language Pack giapponese, il messaggio di eccezione viene scritto nel registro eventi in giapponese.  
  
## Disattivazione del registratore eventi  
 Quando si installano o disinstallano soluzioni Office, il registratore eventi viene attivato per impostazione predefinita. Per disabilitarlo è possibile impostare la variabile di ambiente VSTO\_EVENTLOGDISABLED su "1" \(uno\).  
  
#### Per disabilitare il registro eventi  
  
1.  Aprire **Sistema** nel Pannello di controllo.  
  
2.  Nella scheda **Avanzate** fare clic su **Variabili di ambiente**.  
  
3.  Nel riquadro **Variabili di sistema**, fare clic su **Nuovo**.  
  
4.  Nella finestra di dialogo **Nuova variabile di sistema**, digitare **VSTO\_EVENTLOGDISABLED** nella casella **Nome variabile**.  
  
5.  Nella casella **Valore variabile**, digitare **1**.  
  
6.  Fare clic su **OK**.  
  
## Vedere anche  
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)   
 [Risoluzione dei problemi relativi alla distribuzione di soluzioni Office](../vsto/troubleshooting-office-solution-deployment.md)  
  
  