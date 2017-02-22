---
title: "Text Template Utility Methods | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, utility methods"
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
caps.handback.revision: 50
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Text Template Utility Methods
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esistono diversi metodi sempre disponibili quando si scrive del codice in un modello di testo di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Questi metodi sono definiti in <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  È inoltre possibile utilizzare altri metodi e servizi forniti dall'ambiente host in un modello di testo normale \(non pre\-elaborato\).  Ad esempio, è possibile risolvere percorsi di file, registrare errori e ottenere servizi forniti da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e da qualsiasi pacchetto caricato.  Per ulteriori informazioni, vedere [Accessing Visual Studio from a Text Template](http://msdn.microsoft.com/it-it/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## Metodi Write  
 È possibile utilizzare i metodi `Write()` e `WriteLine()` per aggiungere testo in un blocco di codice standard, anziché utilizzare un blocco di codice dell'espressione.  I due seguenti blocchi di codice sono equivalenti a livello funzionale:  
  
##### Blocco di codice con un blocco di espressione  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### Blocco di codice che utilizza WriteLine\(\)  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 È possibile utilizzare uno di questi metodi di utilità anziché un blocco di espressione all'interno di un blocco di codice lungo con strutture di controllo annidate.  
  
 I metodi `Write()` e `WriteLine()` dispongono di due overload, uno che prende un parametro stringa singolo e uno che prende una stringa di formato composto più una matrice di oggetti da includere nella stringa \(come il metodo `Console.WriteLine()` \).  I due seguenti utilizzi di `WriteLine()` sono equivalenti a livello funzionale:  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## Metodi di rientro  
 È possibile utilizzare metodi d rientro per formattare l'output del modello di testo.  La classe <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> dispone di una proprietà stringa `CurrentIndent` che mostra il rientro corrente nel modello di testo e di un campo `indentLengths` che è un elenco dei rientri aggiunti.  È possibile aggiungere un rientro tramite il metodo `PushIndent()`  e ridurre un rientro utilizzando il metodo `PopIndent()`.  Se si desidera rimuovere tutti i rientri, utilizzare il metodo `ClearIndent()`.  Nel blocco di codice riportato di seguito viene illustrato l'utilizzo di questi metodi:  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 Questo blocco di codice produce il seguente output:  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## Metodi per errori e avvisi  
 È possibile utilizzare metodi di utilità per errori e avvisi per aggiungere dei messaggi all'Elenco errori di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Il codice riportato di seguito, ad esempio, aggiunge un messaggio di errore all'Elenco errori:  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## Accesso a host e a provider di servizi  
 La proprietà `this.Host` può fornire l'accesso a proprietà esposte dall'host che sta eseguendo il modello.  Per utilizzare `this.Host`, è necessario impostare l'attributo `hostspecific` nella direttiva `<@template#>`:  
  
 `<#@template ...  hostspecific="true" #>`  
  
 Il tipo di `this.Host` dipende dal tipo di host nel quale il modello è in esecuzione.  In un modello in esecuzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile eseguire il cast di `this.Host` a `IServiceProvider` per accedere a servizi quali l'IDE.  Di seguito è riportato un esempio:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## Utilizzo di un set diverso di metodi di utilità  
 Come parte del processo di generazione del testo, il file modello viene trasformato in una classe che è sempre denominata `GeneratedTextTransformation` e che eredita da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  Se si desidera utilizzare un differente set di metodi, è possibile scrivere una propria classe e specificarla nella direttiva del modello.  La classe deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Utilizzare la direttiva `assembly` per fare riferimento all'assembly che contiene la classe compilata.