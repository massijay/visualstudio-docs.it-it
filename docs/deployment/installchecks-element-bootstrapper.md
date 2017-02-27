---
title: "Elemento &lt;InstallChecks&gt; (programma di avvio automatico) | Microsoft Docs"
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
  - "<InstallChecks> (elemento) [programma di avvio automatico]"
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# Elemento &lt;InstallChecks&gt; (programma di avvio automatico)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento `InstallChecks` consente di avviare una serie di test sul computer locale per verificare che tutti i prerequisiti appropriati per un'applicazione siano stati installati.  
  
## Sintassi  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## AssemblyCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`.  Per ciascuna istanza di `AssemblyCheck` il programma di avvio automatico verificherà la presenza dell'assembly identificato dall'elemento nella Global Assembly Cache \(GAC\).  Non contiene alcun elemento e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio.  Nome della proprietà in cui archiviare il risultato.  È possibile fare riferimento a questa proprietà da un test al di sotto di `InstallConditions`, un elemento figlio di `Command`.  Per ulteriori informazioni, vedere [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Obbligatorio.  Nome completo dell'assembly da verificare.|  
|`PublicKeyToken`|Obbligatorio.  Forma abbreviata della chiave pubblica associata all'assembly con nome sicuro.  Per tutti gli assembly archiviati nella Global Assembly Cache è necessario definire un nome, una versione e una chiave pubblica.|  
|`Version`|Obbligatorio.  Versione dell'assembly.<br /><br /> Il numero di versione ha il formato \<*versione principale*\>. \<*versione secondaria*\>. \<*versione build*\>. \<*versione revisione*\>.|  
|`Language`|Parametro facoltativo.  Lingua di un assembly localizzato.  Il valore predefinito è `neutral`.|  
|`ProcessorArchitecture`|Parametro facoltativo.  Processore del computer di destinazione dell'installazione.  Il valore predefinito è `msil`.|  
  
## ExternalCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`.  Per ogni istanza di `ExternalCheck`, il programma di avvio automatico esegue il programma esterno definito in un processo separato e archivia il codice di uscita nella proprietà indicata da `Property`.  `ExternalCheck` è utile per l'implementazione di verifiche di dipendenze complesse o nei casi in cui è possibile verificare l'esistenza di un componente soltanto creandone un'istanza.  
  
 `ExternalCheck` non contiene alcun elemento e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio.  Nome della proprietà in cui archiviare il risultato.  È possibile fare riferimento a questa proprietà da un test al di sotto di `InstallConditions`, un elemento figlio di `Command`.  Per ulteriori informazioni, vedere [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Obbligatorio.  Programma esterno da eseguire.  Il programma deve essere incluso nel package di distribuzione dell'installazione.|  
|`Arguments`|Parametro facoltativo.  Fornisce gli argomenti della riga di comando all'eseguibile il cui nome è specificato da `PackageFile`.|  
  
## FileCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`.  Per ciascuna istanza di `FileCheck` il programma di avvio automatico verificherà l'esistenza del file denominato e ne restituirà il numero di versione.  Se il file non dispone di un numero di versione, il programma di avvio automatico imposta su 0 la proprietà il cui nome è specificato da `Property`.  Se il file non esiste, per `Property` non viene impostato nessun valore.  
  
 `FileCheck` non contiene alcun elemento e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio.  Nome della proprietà in cui archiviare il risultato.  È possibile fare riferimento a questa proprietà da un test al di sotto di `InstallConditions`, un elemento figlio di `Command`.  Per ulteriori informazioni, vedere [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Obbligatorio.  Nome del file da trovare.|  
|`SearchPath`|Obbligatorio.  Disco o cartella in cui eseguire la ricerca del file.  Se `SpecialFolder` è assegnato, deve essere un percorso relativo. In caso contrario, deve essere un percorso assoluto.|  
|`SpecialFolder`|Parametro facoltativo.  Cartella con un significato speciale per Windows o per [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Per impostazione predefinita, `SearchPath` viene interpretato come percorso assoluto.  I valori validi sono i seguenti:<br /><br /> `AppDataFolder` \-  Cartella Dati applicazioni specifica dell'utente corrente per l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].<br /><br /> `CommonAppDataFolder` \-  Cartella Dati applicazioni utilizzata da tutti gli utenti.<br /><br /> `CommonFilesFolder` \-  Cartella File comuni per l'utente corrente.<br /><br /> `LocalDataAppFolder` \-  Cartella dei dati per le applicazioni non comuni.<br /><br /> `ProgramFilesFolder` \-  Cartella Programmi standard per le applicazioni a 32 bit.<br /><br /> `StartUpFolder` \-  Cartella contenente tutte le applicazioni eseguite all'avvio del sistema.<br /><br /> `SystemFolder` \-  Cartella contenente le DLL di sistema a 32 bit.<br /><br /> `WindowsFolder` \-  Cartella contenente l'installazione del sistema Windows.<br /><br /> `WindowsVolume` \-  Unità o partizione contenente l'installazione del sistema Windows.|  
|`SearchDepth`|Parametro facoltativo.  Livello di ricerca del file denominato all'interno delle sottocartelle.  La ricerca viene eseguita in profondità.  Il valore predefinito è 0, che restringe la ricerca alla cartella di livello superiore specificata da `SpecialFolder` e **SearchPath**.|  
  
## MsiProductCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`.  Per ciascuna istanza di `MsiProductCheck` il programma di avvio automatico verifica che l'installazione di Microsoft Windows Installer specificata sia stata completata.  Il valore della proprietà è impostato a seconda dello stato del prodotto installato.  Un valore positivo indica che il prodotto è installato, mentre 0 o \-1 indica che non è installato.  Per ulteriori informazioni, fare riferimento alla funzione MsiQueryFeatureState dell'SDK di Windows Installer. .  Se Windows Installer non è installato nel computer, l'attributo `Property` non viene impostato.  
  
 `MsiProductCheck` non contiene alcun elemento e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio.  Nome della proprietà in cui archiviare il risultato.  È possibile fare riferimento a questa proprietà da un test al di sotto di `InstallConditions`, un elemento figlio di `Command`.  Per ulteriori informazioni, vedere [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Obbligatorio.  GUID del prodotto installato.|  
|`Feature`|Parametro facoltativo.  GUID per una specifica funzionalità dell'applicazione installata.|  
  
## RegistryCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`.  Per ciascuna istanza di `RegistryCheck`, il programma di avvio automatico verifica se la chiave del Registro di sistema specificata è presente o se è impostata sul valore indicato.  
  
 `RegistryCheck` non contiene alcun elemento e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio.  Nome della proprietà in cui archiviare il risultato.  È possibile fare riferimento a questa proprietà da un test al di sotto di `InstallConditions`, un elemento figlio di `Command`.  Per ulteriori informazioni, vedere [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obbligatorio.  Nome della chiave del Registro di sistema.|  
|`Value`|Parametro facoltativo.  Nome del valore del Registro di sistema da recuperare.  Il valore predefinito è la restituzione del testo del valore predefinito.  `Value` deve essere una stringa o un valore DWORD.|  
  
## RegistryFileCheck  
 Questo elemento è un elemento figlio facoltativo di `InstallChecks`.  Per ciascuna istanza di `RegistryFileCheck`, il programma di avvio automatico recupera la versione del file specificato, tentando innanzitutto di recuperare il percorso del file dalla chiave del Registro di sistema specificata.  Questo meccanismo risulta particolarmente utile se si desidera cercare un file in una directory specificata come valore nel Registro di sistema.  
  
 `RegistryFileCheck` non contiene alcun elemento e dispone degli attributi riportati di seguito.  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Property`|Obbligatorio.  Nome della proprietà in cui archiviare il risultato.  È possibile fare riferimento a questa proprietà da un test al di sotto di `InstallConditions`, un elemento figlio di `Command`.  Per ulteriori informazioni, vedere [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Obbligatorio.  Nome della chiave del Registro di sistema.  Il relativo valore viene interpretato come percorso di un file, a meno che non venga impostato l'attributo `File`.  Se la chiave non esiste, per `Property` non viene impostato alcun valore.|  
|`Value`|Parametro facoltativo.  Nome del valore del Registro di sistema da recuperare.  Il valore predefinito è la restituzione del testo del valore predefinito.  `Value` deve essere una stringa.|  
|`FileName`|Parametro facoltativo.  Nome di un file.  Se l'attributo è specificato, si presuppone che il valore ottenuto dalla chiave del Registro di sistema corrisponda a un percorso di directory, al quale viene aggiunto tale nome.  Se non è specificato, si presuppone che il valore restituito dal Registro di sistema corrisponda al percorso completo di un file.|  
|`SearchDepth`|Parametro facoltativo.  Livello di ricerca del file denominato all'interno delle sottocartelle.  La ricerca viene eseguita in profondità.  Il valore predefinito è 0, che restringe la ricerca alla cartella di livello superiore specificata dal valore della chiave del Registro di sistema.|  
  
## Note  
 Gli elementi al di sotto di `InstallChecks` definiscono i test necessari senza eseguirli.  Per eseguire i test, è necessario creare elementi `Command` al di sotto dell'elemento `Commands`.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato l'utilizzo dell'elemento `InstallChecks` nel file del prodotto per [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## InstallConditions  
 Quando vengono valutati, gli elementi `InstallChecks` producono proprietà.  Le proprietà vengono quindi utilizzate dalle `InstallConditions` per determinare se installare, ignorare o arrestare il package.  Nella tabella riportata di seguito sono elencate le `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Se una condizione `FailIf` restituisce true, il package avrà esito negativo.  Le condizioni rimanenti non verranno valutate.|  
|`BypassIf`|Se una condizione `BypassIf` restituisce true, il package verrà ignorato.  Le condizioni rimanenti non verranno valutate.|  
  
## Proprietà predefinite  
 Nella seguente tabella sono elencati gli elementi `BypassIf` e `FailIf`.  
  
|Proprietà|Note|Valori possibili|  
|---------------|----------|----------------------|  
|`Version9X`|Numero di versione di un sistema operativo Windows 9X.|4.10 \= Windows 98|  
|`VersionNT`|Numero di versione di un sistema operativo basato su Windows NT.|Major.Minor.ServicePack<br /><br /> 5.0 \= Windows 2000<br /><br /> 5.1.0 \= Windows XP<br /><br /> 5.1.2 \= Windows XP Professional SP2<br /><br /> 5.2.0 \= Windows Server 2003|  
|`VersionNT64`|Numero di versione di un sistema operativo basato su Windows NT a 64 bit.|Come indicato in precedenza.|  
|`VersionMsi`|Numero di numero del servizio Windows Installer.|2.0 \= Windows Installer 2.0|  
|`AdminUser`|Specifica se un utente dispone di privilegi di amministratore in un sistema operativo basato su Windows NT.|0 \= nessun privilegio di amministratore<br /><br /> 1 \= privilegi di amministratore|  
  
 Ad esempio, per bloccare l'installazione in un computer con sistema operativo Windows 95, utilizzare un codice analogo al seguente:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## Vedere anche  
 [Elemento \<Commands\>](../deployment/commands-element-bootstrapper.md)   
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)