---
title: "How to: Configure the ClickOnce Trust Prompt Behavior | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "ClickOnce deployment, install without prompting"
  - "deploying applications [ClickOnce], trust prompt"
  - "ClickOnce applications, install without prompting"
  - "ClickOnce applications, trust prompt"
  - "ClickOnce deployment, trust prompt"
ms.assetid: cc04fa75-012b-47c9-9347-f4216be23cf2
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Configure the ClickOnce Trust Prompt Behavior
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile configurare la richiesta di attendibilità ClickOnce in modo da controllare se agli utenti finali viene data la possibilità di installare applicazioni ClickOnce, ad esempio applicazioni Windows Form, applicazioni Windows Presentation Foundation, applicazioni console, applicazioni browser WPF e soluzioni Office.  Per configurare la richiesta di attendibilità, è necessario impostare le chiavi del Registro di sistema nel computer di ogni utente finale.  
  
 Nella tabella seguente sono illustrate le opzioni di configurazione che è possibile applicare a ognuna delle cinque aree \(Internet, UntrustedSites, MyComputer, LocalIntranet e TrustedSites\).  
  
|Opzione|Valore di impostazione del Registro di sistema|Descrizione|  
|-------------|----------------------------------------------------|-----------------|  
|Abilitare la richiesta di attendibilità.|`Enabled`|La richiesta di attendibilità ClickOnce viene visualizzata in modo che gli utenti finali possano concedere l'attendibilità alle applicazioni ClickOnce.|  
|Limitare la richiesta di attendibilità.|`AuthenticodeRequired`|La richiesta di attendibilità ClickOnce viene visualizzata solo se le applicazioni ClickOnce sono firmate con un certificato che identifica l'autore.|  
|Disabilitare la richiesta di attendibilità.|`Disabled`|La richiesta di attendibilità ClickOnce non viene visualizzata per le applicazioni ClickOnce che non sono firmate con un certificato esplicitamente attendibile.|  
  
 Nella seguente tabella viene illustrato il comportamento predefinito per ogni area.  La colonna Applicazioni si riferisce alle applicazioni Windows Form, Windows Presentation Foundation, browser WPF e console.  
  
|Area|Applicazioni|Soluzioni Office|  
|----------|------------------|----------------------|  
|`MyComputer`|`Enabled`|`Enabled`|  
|`LocalIntranet`|`Enabled`|`Enabled`|  
|`TrustedSites`|`Enabled`|`Enabled`|  
|`Internet`|`Enabled`|`AuthenticodeRequired`|  
|`UntrustedSites`|`Disabled`|`Disabled`|  
  
 È possibile eseguire l'override di queste impostazioni abilitando, limitando o disabilitando la richiesta di attendibilità ClickOnce.  
  
## Abilitazione della richiesta di attendibilità ClickOnce  
 Abilitare la richiesta di attendibilità per un'area quando si desidera che agli utenti finali sia data la possibilità di installare ed eseguire qualsiasi applicazione ClickOnce proveniente da tale area.  
  
#### Per abilitare la richiesta di attendibilità ClickOnce mediante l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema.  
  
    1.  Fare clic su **Start**, quindi su **Esegui**.  
  
    2.  Nella casella **Apri** digitare `regedit32`, quindi scegliere **OK**.  
  
2.  Trovare la seguente chiave del Registro di sistema:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Creare la chiave se è inesistente.  
  
3.  Aggiungere le sottochiavi seguenti come **Valore stringa**, se non già presenti, con i valori associati riportati nella seguente tabella.  
  
    |Sottochiave del valore stringa|Valore|  
    |------------------------------------|------------|  
    |`Internet`|`Enabled`|  
    |`UntrustedSites`|`Disabled`|  
    |`MyComputer`|`Enabled`|  
    |`LocalIntranet`|`Enabled`|  
    |`TrustedSites`|`Enabled`|  
  
     Per le soluzioni Office, `Internet` ha il valore predefinito `AuthenticodeRequired` e `UntrustedSites` ha il valore `Disabled`.  Per tutte le altre, `Internet` ha il valore predefinito `Enabled`.  
  
#### Per abilitare la richiesta di attendibilità ClickOnce a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual C\# in Visual Studio.  
  
2.  Aprire il file Program.vb o Module1.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "Enabled")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Compilare ed eseguire l'applicazione.  
  
## Limitazione della richiesta di attendibilità ClickOnce  
 Limitare la richiesta di attendibilità in modo che le soluzioni debbano essere firmate con certificati Authenticode con identità nota affinché agli utenti venga richiesta una decisione sull'attendibilità.  
  
#### Per limitare la richiesta di attendibilità ClickOnce mediante l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema.  
  
    1.  Fare clic su **Start**, quindi su **Esegui**.  
  
    2.  Nella casella **Apri** digitare `regedit`, quindi scegliere **OK**.  
  
2.  Trovare la seguente chiave del Registro di sistema:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Creare la chiave se è inesistente.  
  
3.  Aggiungere le sottochiavi seguenti come **Valore stringa**, se non già presenti, con i valori associati riportati nella seguente tabella.  
  
    |Sottochiave del valore stringa|Valore|  
    |------------------------------------|------------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`AuthenticodeRequired`|  
    |`MyComputer`|`AuthenticodeRequired`|  
    |`LocalIntranet`|`AuthenticodeRequired`|  
    |`TrustedSites`|`AuthenticodeRequired`|  
  
#### Per limitare la richiesta di attendibilità ClickOnce a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual C\# in Visual Studio.  
  
2.  Aprire il file Program.vb o Module1.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Compilare ed eseguire l'applicazione.  
  
## Disabilitazione della richiesta di attendibilità ClickOnce  
 È possibile disabilitare la richiesta di attendibilità in modo da impedire agli utenti finali di installare soluzioni che non siano già considerate attendibili nei relativi criteri di sicurezza.  
  
#### Per disabilitare la richiesta di attendibilità ClickOnce mediante l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema.  
  
    1.  Fare clic su **Start**, quindi su **Esegui**.  
  
    2.  Nella casella **Apri** digitare `regedit`, quindi scegliere **OK**.  
  
2.  Trovare la seguente chiave del Registro di sistema:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Creare la chiave se è inesistente.  
  
3.  Aggiungere le sottochiavi seguenti come **Valore stringa**, se non già presenti, con i valori associati riportati nella seguente tabella.  
  
    |Sottochiave del valore stringa|Valore|  
    |------------------------------------|------------|  
    |`UntrustedSites`|`Disabled`|  
    |`Internet`|`Disabled`|  
    |`MyComputer`|`Disabled`|  
    |`LocalIntranet`|`Disabled`|  
    |`TrustedSites`|`Disabled`|  
  
#### Per disabilitare la richiesta di attendibilità ClickOnce a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual C\# in Visual Studio.  
  
2.  Aprire il file Program.vb o Module1.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb#  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```c#  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Compilare ed eseguire l'applicazione.  
  
## Vedere anche  
 [Protezione di applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Cenni preliminari sulla distribuzione di applicazioni attendibili](../deployment/trusted-application-deployment-overview.md)   
 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Procedura: aggiungere un autore attendibile a un computer client per applicazioni ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md)