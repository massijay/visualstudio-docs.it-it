---
title: "Procedura: modificare file Web.Config per instrumentare e profilare applicazioni Web ASP.NET compilate dinamicamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: modificare file Web.Config per instrumentare e profilare applicazioni Web ASP.NET compilate dinamicamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare il metodo di strumentazione degli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per raccogliere dati di intervallo dettagliati, di allocazione di memoria .NET e di durata dell'oggetto .NET da applicazioni Web di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilate in modo dinamico.  
  
 In questo argomento viene descritto come modificare il file di configurazione web.config per abilitare la strumentazione e il profilo delle applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
> [!NOTE]
>  Non è necessario modificare il file web.config quando si utilizza il metodo di profilo campione o quando si desidera instrumentare un modulo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] precompilato.  
  
 La radice di un file web.config è l'elemento **configuration**.  Per instrumentare ed eseguire il profilo di un'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilata in modo dinamico, è necessario aggiungere o modificare gli elementi seguenti:  
  
-   Elemento **configuration\/runtime\/assemblyBinding\/dependentAssembly** che identifica l'assembly Microsoft.VisualStudio.Enterprise.ASPNetHelper che controlla il profilo.  L'elemento **dependentAssembly** contiene i due elementi figlio **assemblyIdentity** e **codeBase**.  
  
-   Un elemento **configuration\/system.web\/compilation** che identifica il passaggio di compilazione successivo al processo del profiler per l'assembly di destinazione.  
  
-   Due elementi **add** che identificano il percorso degli strumenti di profilatura aggiunti alla sezione **configuration\/appSettings**.  
  
 Si consiglia di creare una copia del file web.config originale da utilizzare per ripristinare la configurazione dell'applicazione.  
  
### Per aggiungere l'assembly ASPNetHelper come elemento configuration\/runtime\/assemblyBinding\/dependentAssembly  
  
1.  Se necessario, aggiungere l'elemento **runtime** come elemento figlio dell'elemento **configuration**; in caso contrario, andare al passaggio successivo.  
  
     L'elemento **runtime** non contiene attributi.  L'elemento **configuration** può avere un solo elemento **runtime** figlio.  
  
2.  Se necessario, aggiungere l'elemento **assemblyBinding** come elemento figlio dell'elemento **runtime**; in caso contrario, andare al passaggio successivo.  
  
     L'elemento **runtime** può avere un solo elemento **assemblyBinding** figlio.  
  
3.  Aggiungere il valore e il nome di attributo riportati di seguito all'elemento **assemblyBinding**:  
  
    |Nome attributo|Valore attributo|  
    |--------------------|----------------------|  
    |**Xmlns**|**urn:schemas\-microsoft\-com:asm.v1**|  
  
4.  Aggiungere un elemento **dependentAssembly** come elemento figlio dell'elemento **assemblyBinding**.  
  
     L'elemento **dependentAssembly** non contiene attributi.  
  
5.  Aggiungere un elemento **assemblyIdentity** come figlio dell'elemento **dependentAssembly**.  
  
6.  Aggiungere i valori e i nomi di attributo riportati di seguito all'elemento **assemblyIdentity**:  
  
    |Nome attributo|Valore attributo|  
    |--------------------|----------------------|  
    |**name**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**culture**|**Neutral**|  
  
7.  Aggiungere un elemento **codeBase** come figlio dell'elemento **dependentAssembly**.  
  
8.  Aggiungere i valori e i nomi di attributo riportati di seguito all'elemento **codeBase**:  
  
    |Nome attributo|Valore attributo|  
    |--------------------|----------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` è URL di file di Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll.  Se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene installato nel percorso predefinito, il valore **href** sarà `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### Per aggiungere il passaggio successivo al processo del profiler all'elemento configuration\/system.web\/compilation  
  
1.  Se necessario, aggiungere l'elemento **system.web** come elemento figlio dell'elemento **configuration**; in caso contrario, andare al passaggio successivo.  
  
     L'elemento **system.web** non contiene attributi.  L'elemento **configuration** può avere un solo elemento **system.web** figlio.  
  
2.  Se necessario, aggiungere l'elemento **compilation** come elemento figlio dell'elemento **system.web**; in caso contrario, andare al passaggio successivo.  
  
     L'elemento **system.web** può avere un solo elemento **compilation** figlio.  
  
3.  Rimuovere qualsiasi attributo esistente dall'elemento **compilation** e aggiungere il nome e il valore di attributo seguenti:  
  
    |Nome attributo|Valore attributo|  
    |--------------------|----------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, Version\=10.0.0.0, Culture\=neutral, PublicKeyToken\=b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### Per aggiungere impostazioni del percorso del profiler all'elemento di configuration\/appSettings  
  
1.  Se necessario, aggiungere l'elemento **appSettings** come elemento figlio dell'elemento **configuration**; in caso contrario, andare al passaggio successivo.  
  
     L'elemento **appSettings** non contiene attributi.  L'elemento **configuration** può avere un solo elemento **appSettings** figlio.  
  
2.  Aggiungere un elemento **add** come figlio dell'elemento **appSettings**.  
  
3.  Aggiungere i valori e i nomi di attributo riportati di seguito all'elemento **add**:  
  
    |Nome attributo|Valore attributo|  
    |--------------------|----------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**value**|`PerformanceToolsFolder` **\\VSInstr.Exe**|  
  
4.  Aggiungere un altro elemento **add** come figlio dell'elemento **appSettings**.  
  
5.  Aggiungere i valori e i nomi di attributo riportati di seguito a questo elemento **add**:  
  
    |Nome attributo|Valore attributo|  
    |--------------------|----------------------|  
    |**key**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**value**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` è percorso dei file eseguibili del profiler.  Se [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene installato nel percorso predefinito, il valore sarà **C:\\Program Files\\Microsoft Visual Studio 10.0\\Team Tools\\Performance Tools**  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## Esempio  
 Di seguito viene presentato un file web.config completo che abilita la strumentazione e il profilo delle applicazioni Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] compilate dinamicamente.  In questo esempio si presuppone che non vi siano state altre impostazioni nel file prima della modifica.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## Vedere anche  
 [Procedura: instrumentare un'applicazione ASP.NET compilata in modo dinamico e raccogliere dati di intervallo dettagliati](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [Procedura: instrumentare un'applicazione ASP.NET compilata in modo dinamico e raccogliere dati di memoria](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)