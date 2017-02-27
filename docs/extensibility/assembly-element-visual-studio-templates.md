---
title: "Elemento Assembly (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#Assembly"
helpviewer_keywords: 
  - "Assembly (elemento) [modelli di Visual Studio]"
  - "<Assembly> (elemento) [modelli di Visual Studio]"
ms.assetid: 9242f76a-1273-4b8a-8f26-6606f91829ef
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Elemento Assembly (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica le informazioni su un assembly che verranno utilizzate dal modello per aggiungere un riferimento a tale assembly nei progetti.  
  
## Sintassi  
  
```  
<Assembly> AssemblyName </Assembly>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Riferimento](../extensibility/reference-element-visual-studio-templates.md)|Specifica il riferimento all'assembly da aggiungere quando l'elemento viene aggiunto a un progetto.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Questo testo specifica l'assembly da aggiungere a un progetto quando viene avviata l'istanza del modello di elemento.  Il nome dell'assembly deve essere specificato in uno dei modi seguenti:  
  
-   Come nome di assembly completo,  Di seguito è riportato un esempio:  
  
    ```  
    <Assembly>  
        MyAssembly, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom = null.  
    </Assembly>  
    ```  
  
-   Come semplice riferimento di testo,  Di seguito è riportato un esempio:  
  
    ```  
    <Assembly> System </Assembly>  
    ```  
  
## Note  
 `Assembly` è un elemento figlio obbligatorio dell'elemento `Reference`.  
  
 È possibile utilizzare gli elementi `Reference`, `References,` e `Assembly` soltanto nei file .vstemplate che hanno un valore dell'attributo `Type` di `Item`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'elemento `TemplateContent` di un modello di elemento.  Questo codice XML aggiunge i riferimenti agli assembly System.dll e System.Data.dll.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)