---
title: "How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment | Microsoft Docs"
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
  - "ClickOnce deployment, prerequisites"
  - "ClickOnce deployment, URLs"
ms.assetid: 590742c3-a286-4160-aa75-7a441bb2207b
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile che in una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengano verificati alcuni prerequisiti che devono essere disponibili nel computer client per l'esecuzione dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Tra questi prerequisiti sono inclusi la versione minima di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] richiesta, la versione del sistema operativo ed eventuali assembly che devono essere preinstallati nella Global Assembly Cache \(GAC\).  Questi prerequisiti tuttavia non possono essere installati da [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. Se manca un prerequisito, l'installazione viene arrestata e viene visualizzata una finestra di dialogo in cui viene spiegato il motivo dell'interruzione dell'installazione.  
  
 I prerequisiti possono essere installati in due modi.  È possibile installarli utilizzando un'applicazione del programma di avvio automatico.  In alternativa, è possibile specificare un URL di supporto per i singoli prerequisiti che verrà visualizzato nella finestra di dialogo qualora il prerequisito non sia disponibile.  Nella pagina a cui fa riferimento l'URL possono essere contenuti collegamenti a istruzioni di installazione del prerequisito richiesto.  Se non viene specificato un URL di supporto per un singolo prerequisito, in [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] verrà visualizzato l'URL di supporto eventualmente specificato nel manifesto di distribuzione dell'intera applicazione.  
  
 Benché sia possibile utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], Mage.exe e MageUI.exe per generare distribuzioni di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], nessuno di questi strumenti supporta direttamente la specifica di URL di supporto per singoli prerequisiti.  In questo documento viene descritto come modificare il manifesto della distribuzione e il manifesto dell'applicazione della distribuzione in modo da includere gli URL di supporto.  
  
### Specifica di un URL di supporto per un singolo prerequisito  
  
1.  Aprire il manifesto dell'applicazione \(file con estensione manifest\) per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in un editor di testo.  
  
2.  Per indicare come prerequisito un sistema operativo specifico, aggiungere l'attributo `supportUrl` all'elemento `dependentOS`:  
  
    ```  
     <dependency>  
        <dependentOS supportUrl="http://www.adatum.com/MyApplication/wrongOSFound.htm">  
          <osVersionInfo>  
            <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" servicePackMinor="0" />  
          </osVersionInfo>  
        </dependentOS>  
      </dependency>  
    ```  
  
3.  Per indicare come prerequisito una determinata versione di Common Language Runtime, aggiungere l'attributo `supportUrl` alla voce `dependentAssembly` che specifica la dipendenza di Common Language Runtime:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/wrongClrVersionFound.htm">  
          <assemblyIdentity name="Microsoft.Windows.CommonLanguageRuntime" version="4.0.30319.0" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
4.  Per indicare come prerequisito un assembly che deve essere preinstallato nella Global Assembly Cache, impostare l'attributo `supportUrl` per l'elemento `dependentAssembly` che specifica l'assembly richiesto:  
  
    ```  
      <dependency>  
        <dependentAssembly dependencyType="preRequisite" allowDelayedBinding="true" supportUrl=" http://www.adatum.com/MyApplication/missingSampleGACAssembly.htm">  
          <assemblyIdentity name="SampleGACAssembly" version="5.0.0.0" publicKeyToken="04529dfb5da245c5" processorArchitecture="msil" language="neutral" />  
        </dependentAssembly>  
      </dependency>  
    ```  
  
5.  Parametro facoltativo.  Per applicazioni destinate a .NET Framework 4, aprire il manifesto della distribuzione \(file con estensione application\) per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] in un editor di testo.  
  
6.  Per un prerequisito di .NET Framework 4, aggiungere l'attributo `supportUrl` all'elemento `compatibleFrameworks`:  
  
    ```  
    <compatibleFrameworks  xmlns="urn:schemas-microsoft-com:clickonce.v2" supportUrl="http://adatum.com/MyApplication/CompatibleFrameworks.htm">  
      <framework targetVersion="4.0" profile="Client" supportedRuntime="4.0.30319" />  
      <framework targetVersion="4.0" profile="Full" supportedRuntime="4.0.30319" />  
    </compatibleFrameworks>  
    ```  
  
7.  Dopo aver modificato manualmente il manifesto dell'applicazione, è necessario firmarlo di nuovo utilizzando il certificato digitale e quindi aggiornare e firmare di nuovo anche il manifesto della distribuzione.  A tale scopo, utilizzare lo strumento dell'SDK Mage.exe o MageUI.exe, poiché rigenerando questi file con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le modifiche manuali vengono annullate.  Per ulteriori informazioni sull'utilizzo di Mage.exe per firmare di nuovo i manifesti, vedere [How to: Re\-sign Application and Deployment Manifests](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
## Sicurezza di .NET Framework  
 L'URL di supporto non verrà visualizzato nella finestra di dialogo se l'applicazione è contrassegnata per essere eseguita in condizioni di attendibilità parziale.  
  
## Vedere anche  
 [Mage.exe \(Strumento per la generazione e la modifica di manifesti\)](../Topic/Mage.exe%20\(Manifest%20Generation%20and%20Editing%20Tool\).md)   
 [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [\<compatibleFrameworks\> Element](../Topic/%3CcompatibleFrameworks%3E%20Element%20\(ClickOnce%20Deployment\).md)   
 [ClickOnce e Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Prerequisiti per la distribuzione dell'applicazione](../deployment/application-deployment-prerequisites.md)