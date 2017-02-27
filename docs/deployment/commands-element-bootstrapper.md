---
title: "Elemento &lt;Commands&gt; (programma di avvio automatico) | Microsoft Docs"
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
  - "<Commands> (elemento) [programma di avvio automatico]"
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 13
---
# Elemento &lt;Commands&gt; (programma di avvio automatico)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento `Commands` implementa i test descritti dagli elementi al di sotto dell'elemento `InstallChecks` e dichiara il pacchetto che il programma di avvio automatico [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] deve installare se il test ha esito negativo.  
  
## Sintassi  
  
```  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## Elementi e attributi  
 L'elemento `Commands` è obbligatorio  L'elemento dispone del seguente attributo.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Reboot`|Parametro facoltativo.  Determina se è necessario riavviare il sistema quando uno dei package restituisce il codice di uscita del riavvio.  Di seguito sono elencati i valori validi:<br /><br /> `Defer` \-  Il riavvio viene rimandato a una fase successiva.<br /><br /> `Immediate` \-  Determina un riavvio immediato se uno dei package restituisce il codice di uscita del riavvio.<br /><br /> `None` \-  Le richieste di riavvio vengono ignorate.<br /><br /> Il valore predefinito è `Immediate`.|  
  
## Command  
 L'elemento `Command` è un elemento figlio di `Commands`.  L'elemento `Commands` può contenere uno o più elementi `Command`.  e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`PackageFile`|Obbligatorio.  Nome del package da installare se una o più condizioni specificate da `InstallConditions` restituiscono il valore false.  Il package deve essere definito nello stesso file utilizzando un elemento `PackageFile`.|  
|`Arguments`|Parametro facoltativo.  Set di argomenti della riga di comando da passare al file del package.|  
|`EstimatedInstallSeconds`|Parametro facoltativo.  Tempo stimato, in secondi, necessario per l'installazione del package.  Questo valore determina la dimensione dell'indicatore di stato visualizzato dal programma di avvio automatico.  Il valore predefinito è 0. In questo caso, non viene specificata alcuna stima.|  
|`EstimatedDiskBytes`|Parametro facoltativo.  Quantità stimata di spazio su disco, in byte, occupata dal package al completamento dell'installazione.  Questo valore viene utilizzato nei requisiti dello spazio su disco visualizzati dal programma di avvio automatico.  Il valore predefinito è 0. In questo caso, il programma di avvio automatico non visualizza alcun requisito di spazio su disco.|  
|`EstimatedTempBytes`|Parametro facoltativo.  Quantità stimata di spazio temporaneo su disco, in byte, necessaria per il package.|  
|`Log`|Parametro facoltativo.  Percorso relativo del file di log generato dal package, rispetto alla directory radice del package.|  
  
## InstallConditions  
 L'elemento `InstallConditions` è un elemento figlio di `Command`.  Ciascun elemento `Command` può contenere al massimo un elemento `InstallConditions`.  Se non sono presenti elementi `InstallConditions`, verrà sempre eseguito il package specificato da `Condition`.  
  
## BypassIf  
 L'elemento `BypassIf` è un elemento figlio di `InstallConditions` e descrive una condizione positiva in presenza della quale il comando non deve essere eseguito.  Ogni elemento `InstallConditions` può contenere zero o più elementi `BypassIf`.  
  
 `BypassIf` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio.  Nome della proprietà da verificare.  È necessario che la proprietà sia stata precedentemente definita da un elemento figlio dell'elemento `InstallChecks`.  Per ulteriori informazioni, vedere [Elemento \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obbligatorio.  Tipo di confronto da eseguire.  Di seguito sono elencati i valori validi:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obbligatorio.  Valore da confrontare con la proprietà.|  
|`Schedule`|Parametro facoltativo.  Nome di un tag `Schedule` che definisce quando è necessario valutare la regola.|  
  
## FailIf  
 L'elemento `FailIf` è un elemento figlio di `InstallConditions` e descrive una condizione positiva in presenza della quale l'installazione deve essere interrotta.  Ogni elemento `InstallConditions` può contenere zero o più elementi `FailIf`.  
  
 `FailIf` presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio.  Nome della proprietà da verificare.  È necessario che la proprietà sia stata precedentemente definita da un elemento figlio dell'elemento `InstallChecks`.  Per ulteriori informazioni, vedere [Elemento \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Obbligatorio.  Tipo di confronto da eseguire.  Di seguito sono elencati i valori validi:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Obbligatorio.  Valore da confrontare con la proprietà.|  
|`String`|Parametro facoltativo.  Testo da visualizzare quando si verifica un errore.|  
|`Schedule`|Parametro facoltativo.  Nome di un tag `Schedule` che definisce quando è necessario valutare la regola.|  
  
## ExitCodes  
 L'elemento `ExitCodes` è un elemento figlio di `Command`.  L'elemento `ExitCodes` contiene uno o più elementi `ExitCode`, che determinano il comportamento dell'installazione in caso di restituzione di un codice di uscita da un package.  Sotto un elemento `Command` può essere presente un solo elemento `ExitCode` facoltativo.  `ExitCodes` non presenta attributi.  
  
## ExitCode  
 L'elemento `ExitCode` è un elemento figlio di `ExitCodes`.  L'elemento `ExitCode` determina il comportamento dell'installazione in caso di restituzione di un codice di uscita da un pacchetto.  `ExitCode` non contiene elementi figlio e presenta gli attributi seguenti.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Value`|Obbligatorio.  Valore del codice di uscita a cui è applicabile l'elemento `ExitCode`.|  
|`Result`|Obbligatorio.  Modalità di reazione dell'installazione al codice di uscita.  Di seguito sono elencati i valori validi:<br /><br /> `Success` \-  Contrassegna il package come correttamente installato.<br /><br /> `SuccessReboot` \-  Contrassegna il package come correttamente installato e determina il riavvio del sistema.<br /><br /> `Fail` \-  Contrassegna il package come non installato.<br /><br /> `FailReboot` \-  Contrassegna il package come non installato e determina il riavvio del sistema.|  
|`String`|Parametro facoltativo.  Valore da visualizzare in seguito alla restituzione del codice di uscita.|  
|`FormatMessageFromSystem`|Parametro facoltativo.  Determina se utilizzare il messaggio di errore fornito dal sistema corrispondente al codice di uscita oppure il valore specificato in `String`.  I valori validi sono: `true`, che consente di utilizzare il messaggio di errore fornito dal sistema, e `false`, che consente di utilizzare la stringa specificata da `String`.  L'impostazione predefinita è `false`.  Se questa proprietà è `false` ma `String` non è impostato, verrà utilizzato il messaggio di errore fornito dal sistema.|  
  
## Esempio  
 Nell'esempio di codice riportato di seguito vengono definiti i comandi per l'installazione di .NET Framework 2.0.  
  
```  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## Vedere anche  
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)   
 [Elemento \<InstallChecks\>](../deployment/installchecks-element-bootstrapper.md)