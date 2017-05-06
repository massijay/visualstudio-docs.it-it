---
title: "Procedura: configurare la sicurezza dell&#39;elenco di inclusione"
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
  - "elenchi di inclusione [sviluppo per Office in Visual Studio]"
  - "autorizzazioni [sviluppo per Office in Visual Studio]"
ms.assetid: 0609d8f0-4630-4e17-aeb3-14f3134165cf
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# Procedura: configurare la sicurezza dell&#39;elenco di inclusione
  Se si dispone delle autorizzazioni di amministratore, è possibile configurare la richiesta di attendibilità di [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] per controllare se agli utenti finali viene data la possibilità di installare le soluzioni Office salvando una decisione sull'attendibilità nell'elenco di inclusione.  Per informazioni sugli elenchi di inclusione, vedere [Concessione dell'attendibilità alle soluzioni Office mediante gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Per le soluzioni presenti in ognuna delle cinque aree, è possibile impostare le opzioni seguenti:  
  
-   Attivazione della chiave di richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] e dell'elenco di inclusione.  È possibile consentire agli utenti finali di concedere l'attendibilità alle soluzioni Office firmate con un certificato.  
  
-   Limitazione della chiave di richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] e dell'elenco di inclusione.  È possibile consentire agli utenti finali di installare le soluzioni Office firmate con un certificato che identifichi l'autore che non è considerato già attendibile.  
  
-   Disattivazione della chiave di richiesta di attendibilità [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] e dell'elenco di inclusione.  È possibile impedire agli utenti finali di installare qualsiasi soluzione Office non firmata con un certificato attendibile in modo esplicito.  
  
## Attivazione dell'elenco di inclusione  
 Attivare l'elenco di inclusione per un'area quando si desidera che agli utenti finali siano fornite le opzioni di installazione ed esecuzione di qualsiasi soluzione Office proveniente da quell'area.  
  
#### Per attivare l'elenco di inclusione mediante l'editor del Registro di sistema  
  
1.  Aprire l'editor del Registro di sistema.  
  
    1.  Fare clic su **Start**, quindi su **Esegui**.  
  
    2.  Nella casella **Apri**, digitare **regedt32.exe**, quindi scegliere **OK**.  
  
2.  Trovare la seguente chiave del Registro di sistema:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Creare la chiave se è inesistente.  
  
3.  Aggiungere le sottochiavi seguenti come **Valore stringa**, se inesistenti, con i valori associati.  
  
    |Sottochiave del valore stringa|Valore|  
    |------------------------------------|------------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**Disabled**|  
    |**MyComputer**|**Enabled**|  
    |**LocalIntranet**|**Enabled**|  
    |**TrustedSites**|**Enabled**|  
  
     Per impostazione predefinita, **Internet** ha  il valore **AuthenticodeRequired** e **UntrustedSites** ha il valore **Disabled**.  
  
#### Per attivare a livello di codice l'elenco di inclusione  
  
1.  Creare un'applicazione console Visual Basic o Visual C\#.  
  
2.  Aprire il file Program.vb o Module1.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## Limitazione dell'elenco di inclusione  
 Limitare l'elenco di inclusione in modo che le soluzioni vengano firmate con certificati Authenticode con identità conosciuta, prima che agli utenti venga richiesta una decisione sull'attendibilità.  
  
#### Per limitare l'elenco di inclusione  
  
1.  Aprire l'editor del Registro di sistema.  
  
    1.  Fare clic su **Start**, quindi su **Esegui**.  
  
    2.  Nella casella **Apri**, digitare **regedt32.exe**, quindi scegliere **OK**.  
  
2.  Trovare la seguente chiave del Registro di sistema:  
  
     \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel  
  
     Creare la chiave se è inesistente.  
  
3.  Aggiungere le sottochiavi seguenti come **Valore stringa**, se inesistenti, con i valori associati.  
  
    |Sottochiave del valore stringa|Valore|  
    |------------------------------------|------------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**MyComputer**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     Per impostazione predefinita, **Internet** ha  il valore **AuthenticodeRequired** e **UntrustedSites** ha il valore **Disabled**.  
  
#### Per limitare l'elenco di inclusione a livello di codice  
  
1.  Creare un'applicazione console Visual Basic o Visual C\#.  
  
2.  Aprire il file Program.vb o Module1.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
  
## Disattivazione dell'elenco di inclusione  
 È possibile disabilitare l'elenco di inclusione in modo che gli utenti finali possano installare solo le soluzioni firmate con un certificato attendibile e noto.  
  
#### Per disabilitare l'elenco di inclusione  
  
1.  Aprire l'editor del Registro di sistema.  
  
    1.  Fare clic su **Start**, quindi su **Esegui**.  
  
    2.  Nella casella **Apri**, digitare **regedt32.exe**, quindi scegliere **OK**.  
  
2.  Creare la chiave del Registro di sistema seguente, se inesistente:  
  
     **\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel**  
  
3.  Aggiungere le sottochiavi seguenti come **Valore stringa**, se inesistenti, con i valori associati.  
  
    |Sottochiave del valore stringa|Valore|  
    |------------------------------------|------------|  
    |**UntrustedSites**|**Disabled**|  
    |**Internet**|**Disabled**|  
    |**MyComputer**|**Disabled**|  
    |**LocalIntranet**|**Disabled**|  
    |**TrustedSites**|**Disabled**|  
  
#### Per disabilitare a livello di codice l'elenco di inclusione  
  
1.  Creare un'applicazione console Visual Basic o Visual C\#.  
  
2.  Aprire il file Program.vb o Module1.cs per la modifica e aggiungere il codice seguente.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
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
 [Concessione dell'attendibilità alle soluzioni Office mediante gli elenchi di inclusione](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Sicurezza delle soluzioni Office](../vsto/securing-office-solutions.md)  
  
  