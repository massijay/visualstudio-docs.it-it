---
title: "Procedura: creare un manifesto di pacchetto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "dipendenze, pacchetti del programma di avvio automatico personalizzati"
  - "package (file) [ClickOnce]"
  - "file di pacchetto [Windows Installer]"
  - "prerequisiti, pacchetto del programma di avvio automatico personalizzato"
ms.assetid: 5aecc507-2764-42f2-ae6f-c227971cf0af
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# Procedura: creare un manifesto di pacchetto
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per distribuire i prerequisiti dell'applicazione è possibile utilizzare un programma di avvio automatico.  Tale programma contiene un unico file manifesto del prodotto e un manifesto di pacchetto per ogni set di impostazioni locali.  Le funzionalità condivise da versioni localizzate diverse devono essere contenute nel manifesto del prodotto.  
  
 Per ulteriori informazioni sui manifesti di pacchetto, vedere [Procedura: creare il manifesto di un prodotto](../deployment/how-to-create-a-product-manifest.md).  
  
## Creazione del manifesto di pacchetto  
  
#### Per creare il manifesto di pacchetto  
  
1.  Creare una directory per il programma di avvio automatico.  In questo esempio viene utilizzato C:\\package.  
  
2.  Creare una sottodirectory con il nome delle impostazioni locali, ad esempio en per la lingua inglese.  
  
3.  In Visual Studio creare un file XML denominato `package.xml` e salvarlo nella cartella C:\\package\\en.  
  
4.  Aggiungere codice XML per elencare il nome del programma di avvio automatico, le impostazioni cultura per il manifesto di pacchetto localizzato e il contratto di licenza facoltativo.  Nel codice XML riportato di seguito vengono utilizzate le variabili `DisplayName` e `Culture`, definite in un elemento successivo.  
  
    ```  
    <Package  
        xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
        Name="DisplayName"  
        Culture="Culture"  
        LicenseAgreement="eula.txt">  
    ```  
  
5.  Aggiungere codice XML per elencare tutti i file contenuti nella directory specifica delle impostazioni locali.  Nel codice XML riportato di seguito viene utilizzato un file denominato eula.txt applicabile alle impostazioni locali **en**.  
  
    ```  
    <PackageFiles>  
      <PackageFile Name="eula.txt"/>  
    </PackageFiles>  
    ```  
  
6.  Aggiungere codice XML per definire stringhe localizzabili per il programma di avvio automatico.  Nel codice XML riportato di seguito vengono aggiunte stringhe di errore per le impostazioni locali en.  
  
    ```  
      <Strings>  
        <String Name="DisplayName">Custom Bootstrapper Package</String>  
        <String Name="CultureName">en</String>  
        <String Name="NotAnAdmin">You must be an administrator to install   
    this package.</String>  
        <String Name="GeneralFailure">A general error has occurred while   
    installing this package.</String>  
    </Strings>  
    ```  
  
7.  Copiare la cartella C:\\package nella directory del programma di avvio automatico di Visual Studio.  Nel caso di Visual Studio 2010, la directory è \\Programmi\\Microsoft SDKs\\Windows\\v7.0A\\Bootstrapper\\Packages.  
  
## Esempio  
 Il manifesto di pacchetto contiene informazioni specifiche delle impostazioni locali, ad esempio messaggi di errore, condizioni di licenza del software e Language Pack.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<Package  
  xmlns="http://schemas.microsoft.com/developer/2004/01/bootstrapper"  
  Name="DisplayName"  
  Culture="Culture"  
  LicenseAgreement="eula.txt">  
  
  <PackageFiles>  
    <PackageFile Name="eula.txt"/>  
  </PackageFiles>  
  
  <Strings>  
    <String Name="DisplayName">Custom Bootstrapper Package</String>  
    <String Name="Culture">en</String>  
    <String Name="NotAnAdmin">You must be an administrator to install this package.</String>  
    <String Name="GeneralFailure">A general error has occurred while   
installing this package.</String>  
  </Strings>  
</Package>  
```  
  
## Vedere anche  
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)