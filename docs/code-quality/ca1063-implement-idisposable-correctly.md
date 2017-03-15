---
title: "CA1063: Implementare IDisposable correttamente | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementIDisposableCorrectly"
  - "CA1063"
helpviewer_keywords: 
  - "CA1063"
  - "ImplementIDisposableCorrectly"
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1063: Implementare IDisposable correttamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|Category|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 `IDisposable` non è implementato correttamente.  Alcune ragioni per questo problema sono elencate di seguito.  
  
-   IDisposable è stato reimplementato nella classe.  
  
-   Finalize è stato sottoposto nuovamente a override.  
  
-   Dispose è stato sottoposto a override.  
  
-   Dispose\(\) è un Dispose non pubblico, sealed o denominato.  
  
-   Dispose\(bool\) è non protetto, virtuale o non sealed.  
  
-   In tipi non sealed Dispose\(\) deve chiamare Dispose\(true\).  
  
-   Per tipi non sealed l'implementazione Finalize non chiama Dispose\(bool\) o il finalizzatore della classe base.  
  
 La violazione di uno qualsiasi di questi modelli genererà l'avviso.  
  
 Ogni tipo di IDisposable radice non sealed deve fornire il relativo metodo Dispose\(bool\) void virtuale protetto.  Dispose\(\) deve chiamare Dispose\(true\) mentre Finalize deve chiamare Dispose\(false\).  Se si sta creando un tipo di IDisposable radice non sealed, è necessario definire Dispose\(bool\) e chiamarlo.  Per ulteriori informazioni, vedere [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md) nella sezione [Linee guida](../Topic/Framework%20Design%20Guidelines.md) della documentazione di .NET Framework.  
  
## Descrizione della regola  
 Tutti i tipi IDisposable devono correttamente implementare il modello Dispose.  
  
## Come correggere le violazioni  
 Esaminare il codice a disposizione e determinare quale delle seguenti risoluzioni potrà correggere la violazione.  
  
-   Rimuovere IDisposable dall'elenco delle interfacce implementate da {0} ed eseguire l'override dell'implementazione Dispose della classe di base.  
  
-   Rimuovere il finalizzatore dal tipo {0}, eseguire l'override di Dispose\(bool disposing\) e inserire la logica di finalizzazione nel percorso del codice laddove 'disposing' corrisponde a false.  
  
-   Rimuovere {0}, eseguire l'override di Dispose\(bool disposing\) e inserire la logica di eliminazione nel percorso del codice laddove 'disposing' corrisponde a true.  
  
-   Accertarsi che {0} sia dichiarato come pubblico e sealed.  
  
-   Rinominare {0} come 'Dispose' e accertarsi che venga dichiarato come pubblico e sealed.  
  
-   Accertarsi che {0} sia dichiarato come protetto, virtuale e non sealed.  
  
-   Modificare {0} in modo che chiami Dispose\(true\) e quindi GC.SuppressFinalize sull'istanza dell'oggetto corrente \('this' o 'Me' in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), dopodiché venga restituito.  
  
-   Modificare {0} in modo che chiami Dispose\(false\) e quindi venga restituito.  
  
-   Se si scrive una classe IDisposable radice non sealed, accertarsi che l'implementazione di IDisposable segua il modello descritto in precedenza in questa sezione.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio di pseudo\-codice  
 Nello pseudo\-codice riportato di seguito viene fornito un esempio generale delle procedure consigliate per l'implementazione di Dispose\(bool\) in una classe che utilizza risorse gestite e native.  
  
```  
public class Resource : IDisposable   
{  
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);  
    private AnotherResource managedResource = new AnotherResource();  
  
// Dispose() calls Dispose(true)  
    public void Dispose()  
    {  
        Dispose(true);  
        GC.SuppressFinalize(this);  
    }  
    // NOTE: Leave out the finalizer altogether if this class doesn't   
    // own unmanaged resources itself, but leave the other methods  
    // exactly as they are.   
    ~Resource()   
    {  
        // Finalizer calls Dispose(false)  
        Dispose(false);  
    }  
    // The bulk of the clean-up code is implemented in Dispose(bool)  
    protected virtual void Dispose(bool disposing)  
    {  
        if (disposing)   
        {  
            // free managed resources  
            if (managedResource != null)  
            {  
                managedResource.Dispose();  
                managedResource = null;  
            }  
        }  
        // free native resources if there are any.  
        if (nativeResource != IntPtr.Zero)   
        {  
            Marshal.FreeHGlobal(nativeResource);  
            nativeResource = IntPtr.Zero;  
        }  
    }  
}  
```