---
title: "Metodi di utilità di modelli di testo | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, utility methods
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: "50"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 534a7317b4bca2abe559c028d025a52997a9f508
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="text-template-utility-methods"></a>Metodi di utilità per i modelli di testo
Esistono diversi metodi che sono sempre disponibili quando si scrive codice in un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] modello di testo. Questi metodi sono definiti in <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
> [!TIP]
>  È inoltre possibile utilizzare altri metodi e i servizi forniti dall'ambiente host in un modello di testo (non pre-elaborato) regolare. Ad esempio, può risolvere i percorsi di file, registrare gli errori e ottenere servizi forniti da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e qualsiasi pacchetto caricato.  Per ulteriori informazioni, vedere [l'accesso a Visual Studio da un modello di testo](http://msdn.microsoft.com/en-us/0556f20c-fef4-41a9-9597-53afab4ab9e4).  
  
## <a name="write-methods"></a>Metodi di scrittura  
 È possibile utilizzare il `Write()` e `WriteLine()` metodi per aggiungere testo all'interno di un blocco di codice standard, anziché utilizzare un blocco di codice di espressione. I seguenti blocchi di codice che seguono sono funzionalmente equivalenti.  
  
##### <a name="code-block-with-an-expression-block"></a>Blocco di codice con un blocco di espressione  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### <a name="code-block-using-writeline"></a>Blocco di codice utilizzando WriteLine)  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 Potrebbe essere utile utilizzare uno di questi metodi di utilità anziché un blocco di espressione all'interno di un blocco di codice lunghi con strutture di controllo annidate.  
  
 Il `Write()` e `WriteLine()` metodi dispongono di due overload, uno che accetta un parametro stringa singolo e uno che accetta una matrice di oggetti da includere nella stringa di più di una stringa in formato composito (ad esempio il `Console.WriteLine()` (metodo)). I seguenti due utilizzi di `WriteLine()` sono funzionalmente equivalenti:  
  
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
  
## <a name="indentation-methods"></a>Metodi di rientro  
 È possibile utilizzare i metodi di rientro per formattare l'output del modello di testo. Il <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> classe dispone di un `CurrentIndent` proprietà stringa che mostra il rientro corrente nel modello di testo e un `indentLengths` campo che rappresenta un elenco dei rientri che sono stati aggiunti. È possibile aggiungere un rientro con il `PushIndent()` (metodo) e sottrazione di un rientro con il `PopIndent()` metodo. Se si desidera rimuovere tutti i rientri, utilizzare il `ClearIndent()` metodo. Blocco di codice seguente viene illustrato come utilizzare questi metodi:  
  
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
  
## <a name="error-and-warning-methods"></a>Errore e i metodi di avviso  
 È possibile utilizzare i metodi di utilità di errore e avviso per aggiungere i messaggi di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] elenco errori. Il codice seguente, ad esempio, aggiungerà un messaggio di errore per l'elenco degli errori.  
  
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
  
## <a name="access-to-host-and-service-provider"></a>Accesso all'Host e i Provider di servizi  
 La proprietà `this.Host` può fornire l'accesso alle proprietà esposte dall'host che sta eseguendo il modello. Per utilizzare `this.Host`, è necessario impostare `hostspecific` attributo la `<@template#>` direttiva:  
  
 `<#@template ... hostspecific="true" #>`  
  
 Il tipo di `this.Host` dipende dal tipo di host in cui è in esecuzione il modello. In un modello che è in esecuzione in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], è possibile eseguire il cast `this.Host` a `IServiceProvider` per accedere ai servizi, ad esempio l'IDE. Ad esempio:  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## <a name="using-a-different-set-of-utility-methods"></a>Utilizzo di un set diverso di metodi di utilità  
 Come parte del processo di generazione del testo, il file del modello viene trasformato in una classe, che è sempre denominata `GeneratedTextTransformation`e che eredita da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>. Se si desidera utilizzare un differente set di metodi, è possibile scrivere la propria classe e specificarlo nella direttiva del modello. La classe deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>.  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 Utilizzare il `assembly` direttiva per fare riferimento all'assembly di cui è possibile trovare la classe compilata.