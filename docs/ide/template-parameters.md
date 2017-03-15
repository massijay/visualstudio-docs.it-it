---
title: "Parametri di template | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modelli di elementi, parametri"
  - "modelli di progetto, parametri"
  - "modelli (parametri) [Visual Studio]"
  - "modelli di Visual Studio, parametri"
ms.assetid: 1b567143-08c6-4d7a-b484-49f0671754fe
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Parametri di template
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizzando i parametri nei modelli, è possibile sostituire i valori di alcune chiavi del modello, come ad ad esempio i nomi delle classi e i namespace, quando viene creata un'istanza del modello.  Questi parametri vengono sostituiti dalla Creazione guidata modelli che viene eseguita in background quando si fa clic su **OK** nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.  
  
## Dichiarazione e attivazione dei parametri di un modello  
 I parametri del modello vengono dichiarati nel formato $*parameter*$.  Ad esempio:  
  
-   $safeprojectname$  
  
-   $guid1$  
  
-   $guid5$  
  
#### Per attivare la sostituzione dei parametri nei modelli  
  
1.  Nel file .vstemplate del modello, individuare l'elemento `ProjectItem` che corrisponde all'elemento per il quale si desidera attivare la sostituzione dei parametri.  
  
2.  Impostare l'attributo `ReplaceParameters` dell'elemento `ProjectItem` su `true`.  
  
3.  Nel file di codice dell'elemento del progetto, includere i parametri, se appropriato.  Il parametro seguente, ad esempio, specifica che in un file verrà utilizzato safe project name per lo spazio dei nomi:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
## Parametri di modello riservati  
 Nella tabella riportata di seguito sono elencati i parametri di modello riservati che possono essere utilizzati con qualsiasi modello.  
  
> [!NOTE]
>  Nei parametri di modello viene fatta distinzione tra maiuscole e minuscole.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`clrversion`|Versione corrente di Common Language Runtime \(CLR\).|  
|`GUID [1-10]`|Un GUID utilizzato per sostituire il GUID del progetto in un file di progetto.  È possibile specificare fino a 10 GUID univoci, ad esempio `guid1)`.|  
|`itemname`|Il nome fornito dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**.|  
|`machinename`|Il nome del computer corrente, ad esempio Computer01.|  
|`projectname`|Il nome fornito dall'utente nella finestra di dialogo **Nuovo progetto**.|  
|`registeredorganization`|Il valore della chiave di registro estratta da HKLM\\Software\\Microsoft\\Windows NT\\CurrentVersion\\RegisteredOrganization.|  
|`rootnamespace`|Lo spazio dei nomi radice del progetto corrente.  Questo parametro è valido solo per i modelli di elemento.|  
|`safeitemname`|Il nome fornito dall'utente nella finestra di dialogo **Aggiungi nuovo elemento**, dal quale sono stati rimossi i caratteri non sicuri e gli spazi.|  
|`safeprojectname`|Il nome fornito dall'utente nella finestra di dialogo **Nuovo progetto**, dal quale sono stati rimossi i caratteri non sicuri e gli spazi.|  
|`time`|La data e l'ora correnti nel formato GG\/MM\/AAAA 00:00:00.|  
|`SpecificSolutionName`|Nome della soluzione.  Quando "creare una directory di soluzione" è selezionata, `SpecificSolutionName` è il nome della soluzione.  Quando "creare una directory di soluzione" non è selezionata, `SpecificSolutionName` è vuota.|  
|`userdomain`|L'attuale dominio utente.|  
|`username`|Il nome dell'utente corrente.|  
|`webnamespace`|Nome del sito Web corrente.  Questo parametro viene utilizzato nel modello Web Form per garantire nomi della classe univoci.  Se il sito Web si trova nella directory radice del server Web, questo parametro del modello viene risolto nella directory radice del server Web.|  
|`year`|L'anno corrente nel formato AAAA.|  
  
## Parametri di modello personalizzati  
 Oltre ai parametri dei modelli riservati predefiniti che vengono utilizzati automaticamente durante la sostituzione dei parametri, è possibile specificare i propri valori e i propri parametri dei modelli. Per ulteriori informazioni vedere [Elemento CustomParameters \(modelli di Visual Studio\)](../extensibility/customparameters-element-visual-studio-templates.md)  
  
## Esempio: sostituzione dei nomi di file  
 È possibile specificare nomi di file variabili per elementi del progetto mediante un parametro con l'attributo `TargetFileName`.  È possibile specificare, ad esempio, che il file .exe utilizzi come nome del file il nome del progetto specificato da `$projectname$`.  
  
```  
<TemplateContent>  
    <ProjectItem  
        ReplaceParameters="true"  
        TargetFileName="$projectname$.exe">  
            File1.exe  
    </ProjectItem>  
      ...  
</TemplateContent>  
```  
  
## Esempio: utilizzo del nome del progetto per il nome dello spazio dei nomi  
 Per utilizzare il nome del progetto per il nome dello spazio dei nomi in un file di classe Visual C\#, Class1.cs, utilizzare la seguente sintassi:  
  
```  
#region Using directives  
  
using System;  
using System.Collections.Generic;  
using System.Text;  
  
#endregion  
  
namespace $safeprojectname$  
{  
    public class Class1  
        {  
            public Class1()  
                {  
  
                }  
         }  
}  
```  
  
 Nel file .vstemplate del modello di progetto, includere il seguente codice XML quando si fa riferimento al file Class1.cs:  
  
```  
<TemplateContent>  
    <ProjectItem ReplaceParameters="true">  
        Class1.cs  
    </ProjectItem>  
    ...  
</TemplateContent>  
```  
  
## Vedere anche  
 [Personalizzazione di modelli](../ide/customizing-project-and-item-templates.md)