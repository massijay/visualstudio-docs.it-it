---
title: "Procedura: creare il manifesto di un prodotto | Microsoft Docs"
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
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "dipendenze, pacchetto del programma di avvio automatico personalizzato"
  - "prerequisiti, pacchetto del programma di avvio automatico personalizzato"
  - "prodotto (file) [ClickOnce]"
  - "file di prodotto [Windows Installer]"
ms.assetid: 2d316aaa-8bc0-4ce5-90ab-23b3eac0b5dd
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedura: creare il manifesto di un prodotto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per distribuire i prerequisiti dell'applicazione è possibile creare un programma di avvio automatico.  Tale programma contiene un unico file manifesto del prodotto e un manifesto di pacchetto per ogni set di impostazioni locali.  Il manifesto di pacchetto contiene aspetti specifici della localizzazione del pacchetto,  inclusi stringhe, contratti di licenza dell'utente finale e Language Pack.  
  
 Per ulteriori informazioni sui manifesti di prodotto, vedere [Procedura: creare un manifesto di pacchetto](../deployment/how-to-create-a-package-manifest.md).  
  
## Creazione del manifesto del prodotto  
  
#### Per creare il manifesto del prodotto  
  
1.  Creare una directory per il programma di avvio automatico.  In questo esempio viene utilizzato C:\\package.  
  
2.  In Visual Studio creare un nuovo file XML denominato `product.xml` e salvarlo nella cartella C:\\package.  
  
3.  Aggiungere il seguente codice XML per descrivere lo spazio dei nomi XML e il codice prodotto per il pacchetto.  Sostituire il codice prodotto con un identificatore univoco per il pacchetto.  
  
    ```  
    <Product  
    xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"   
    ProductCode="Custom.Bootstrapper.Package">  
    ```  
  
4.  Aggiungere codice XML per specificare che il pacchetto dispone di una dipendenza.  In questo esempio viene utilizzata una dipendenza da Microsoft Windows Installer 3.1.  
  
    ```  
    <RelatedProducts>  
        <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
      </RelatedProducts>  
    ```  
  
5.  Aggiungere codice XML per elencare tutti i file contenuti nel programma di avvio automatico.  In questo esempio viene utilizzato il nome file di pacchetto CorePackage.msi.  
  
    ```  
    <PackageFiles>  
        <PackageFile Name="CorePackage.msi"/>  
    </PackageFiles>  
    ```  
  
6.  Copiare o spostare il file CorePackage.msi nella cartella C:\\package.  
  
7.  Aggiungere codice XML per installare il pacchetto tramite i comandi del programma di avvio automatico.  Il programma di avvio automatico aggiungerà automaticamente il flag **\/qn** al file MSI, il quale verrà installato senza alcun avviso.  Se il file è un file con estensione exe, il programma di avvio automatico esegue tale file tramite la shell.  Il codice XML seguente non contiene argomenti per CorePackage.msi, ma è possibile inserire l'argomento della riga di comando nell'attributo Arguments.  
  
    ```  
    <Commands>  
        <Command PackageFile="CorePackage.msi" Arguments="">  
    ```  
  
8.  Aggiungere il seguente codice XML per verificare che il programma di avvio automatico sia installato.  Sostituire il codice prodotto con il GUID per il componente ridistribuibile.  
  
    ```  
    <InstallChecks>  
        <MsiProductCheck   
            Property="IsMsiInstalled"   
            Product="{XXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
    </InstallChecks>  
    ```  
  
9. Aggiungere codice XML per modificare il comportamento del programma di avvio automatico a seconda che il componente del programma sia già installato o meno.  Se il componente è installato, il programma di avvio automatico non viene eseguito.  Il seguente codice XML consente di controllare se l'utente corrente è un amministratore, poiché questo componente richiede privilegi amministrativi.  
  
    ```  
    <InstallConditions>  
        <BypassIf   
           Property="IsMsiInstalled"   
           Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
            Compare="ValueNotEqualTo" Value="True"  
            String="NotAnAdmin"/>  
    </InstallConditions>  
    ```  
  
10. Aggiungere codice XML per impostare codici di uscita nel caso in cui l'installazione sia stata completata correttamente e sia necessario un riavvio.  Nel seguente codice XML sono illustrati i codici di uscita Fail e FailReboot, i quali indicano che il programma di avvio automatico non continuerà a installare pacchetti.  
  
    ```  
    <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
    </ExitCodes>  
    ```  
  
11. Aggiungere il seguente codice XML per terminare la sezione per i comandi del programma di avvio automatico.  
  
    ```  
        </Command>  
    </Commands>  
    ```  
  
12. Spostare la cartella C:\\package nella directory del programma di avvio automatico di Visual Studio.  Nel caso di Visual Studio 2010, la directory è \\Programmi\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Esempio  
 Il manifesto del prodotto contiene le istruzioni di installazione per i prerequisiti personalizzati.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Product  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  ProductCode="Custom.Bootstrapper.Package">  
  
  <RelatedProducts>  
    <DependsOnProduct Code="Microsoft.Windows.Installer.3.1" />  
  </RelatedProducts>  
  
  <PackageFiles>  
    <PackageFile Name="CorePackage.msi"/>  
  </PackageFiles>  
  
  <InstallChecks>  
    <MsiProductCheck Product="IsMsiInstalled"   
      Property="{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}"/>  
  </InstallChecks>  
  
  <Commands>  
    <Command PackageFile="CorePackage.msi" Arguments="">  
  
      <InstallConditions>  
        <BypassIf Property="IsMsiInstalled"  
          Compare="ValueGreaterThan" Value="0"/>  
        <FailIf Property="AdminUser"   
          Compare="ValueNotEqualTo" Value="True"  
         String="NotAnAdmin"/>  
      </InstallConditions>  
  
      <ExitCodes>  
        <ExitCode Value="0" Result="Success"/>  
        <ExitCode Value="1641" Result="SuccessReboot"/>  
        <ExitCode Value="3010" Result="SuccessReboot"/>  
        <DefaultExitCode Result="Fail" String="GeneralFailure"/>  
      </ExitCodes>  
    </Command>  
  </Commands>  
</Product>  
```  
  
## Vedere anche  
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)