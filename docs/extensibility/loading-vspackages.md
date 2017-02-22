---
title: "Caricamento VS | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Package VS, il caricamento automatico"
  - "VSPackage, caricamento"
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Caricamento VS
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Package VS vengono caricati in Visual Studio solo quando è richiesta la funzionalità. Ad esempio, viene caricato un VSPackage quando Visual Studio viene utilizzata una factory del progetto o un servizio che implementa il VSPackage. Questa funzionalità è denominata caricamento ritardato, che viene utilizzato ogni volta che è possibile migliorare le prestazioni.  
  
> [!NOTE]
>  Visual Studio può determinare alcune informazioni VSPackage, ad esempio i comandi che offre un VSPackage, senza caricare il VSPackage.  
  
 Package VS impostabili per caricare automaticamente in un contesto dell'interfaccia utente specifico, ad esempio, quando una soluzione è aperta. Il <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> questo contesto viene impostato dall'attributo.  
  
### Il caricamento automatico un pacchetto Visual Studio in un contesto specifico  
  
-   Aggiungere il `ProvideAutoLoad` attributo per gli attributi di VSPackage:  
  
    ```c#  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Visualizzare i campi enumerati di <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> per un elenco dei contesti dell'interfaccia utente e i relativi valori GUID.  
  
-   Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
-   Compilare il pacchetto Visual Studio e avviare il debug.  
  
-   Caricare una soluzione o crearne uno.  
  
     VSPackage carica e si arresta in corrispondenza del punto di interruzione.  
  
## Forzare un VSPackage da caricare  
 In alcune circostanze un VSPackage potrebbe essere necessario forzare un altro VSPackage da caricare. Ad esempio, un VSPackage leggero potrebbe caricare un pacchetto più grande in un contesto che non è disponibile come un CMDUIContext.  
  
 È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> metodo per forzare un VSPackage da caricare.  
  
-   Inserire il codice nella <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo del VSPackage che impone un altro VSPackage da caricare:  
  
    ```c#  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Quando viene inizializzato il package VS, verrà sempre `PackageToBeLoaded` da caricare.  
  
     Non utilizzare il caricamento forzato per la comunicazione di VSPackage. In alternativa, usare [Utilizzo e servizi](../extensibility/using-and-providing-services.md).  
  
## Utilizzo di un attributo personalizzato per registrare un VSPackage  
 In alcuni casi potrebbe essere necessario creare un nuovo attributo di registrazione per l'estensione. Per aggiungere nuove chiavi del Registro di sistema o per aggiungere nuovi valori per le chiavi esistenti, è possibile utilizzare gli attributi di registrazione. Il nuovo attributo deve derivare da <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>, e deve eseguire l'override di <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> metodi.  
  
## Creazione di una chiave del Registro di sistema  
 Nel codice seguente, l'attributo personalizzato viene creato un **personalizzato** sottochiave sotto la chiave per il package VS che deve essere registrato.  
  
```c#  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## Creazione di un nuovo valore in una chiave del Registro di sistema esistente  
 È possibile aggiungere valori personalizzati a una chiave esistente. Il codice seguente viene illustrato come aggiungere un nuovo valore a una chiave di registrazione VSPackage.  
  
```c#  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## Vedere anche  
 [Package VS](../extensibility/internals/vspackages.md)