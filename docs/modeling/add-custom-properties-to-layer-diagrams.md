---
title: "Aggiungere proprietà personalizzate a diagrammi di dipendenza | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, adding custom properties
ms.assetid: 52b3ac25-d10b-4507-a1fe-209ccb4d2777
caps.latest.revision: 21
author: alexhomer1
ms.author: ahomer
manager: douge
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 8f84f22444a5df5b9f4f4af44cd8ee9136403467
ms.openlocfilehash: 6c7e43c180ac5210d9c29961ed7330b370a99075
ms.lasthandoff: 02/22/2017

---
# <a name="add-custom-properties-to-dependency-diagrams"></a>Aggiungere proprietà personalizzate a diagrammi di dipendenza
Quando si scrive codice delle estensioni per diagrammi di dipendenza, è possibile archiviare i valori con qualsiasi elemento in un diagramma di dipendenza. I valori saranno permanenti quando il diagramma viene salvato e riaperto. È possibile configurare anche queste proprietà vengono visualizzate nel **proprietà** finestra in modo che gli utenti possono vedere e modificarli. Ad esempio, è possibile consentire agli utenti di specificare un'espressione regolare per ogni livello e scrivere il codice di convalida per verificare che i nomi delle classi in ogni livello siano conformi al modello specificato dall'utente.  
  
## <a name="properties-not-visible-to-the-user"></a>Proprietà non visibili all'utente  
 Se si desidera semplicemente il codice associ i valori a qualsiasi elemento in un diagramma di dipendenza, è necessario definire un componente MEF. Esiste un dizionario denominato `Properties` <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> Aggiungere semplicemente i valori marshalable al dizionario di qualsiasi elemento del livello. I valori saranno salvati come parte del diagramma delle dipendenze. Per ulteriori informazioni, vedere [Naviga e aggiornare i modelli nel codice del programma di livello](../modeling/navigate-and-update-layer-models-in-program-code.md).  
  
## <a name="properties-that-the-user-can-edit"></a>Proprietà modificabili dall'utente  
 **Preparazione iniziale**  
  
> [!IMPORTANT]
>  Per fare in modo che le proprietà vengano visualizzate, è necessario apportare le seguenti modifiche in ogni computer in cui si desidera che le proprietà del livello siano visibili.  
>   
>  1.  Eseguire il blocco note utilizzando **Esegui come amministratore**. Aprire `%ProgramFiles%\Microsoft Visual Studio [version]\Common7\IDE\Extensions\Microsoft\Architecture Tools\ExtensibilityRuntime\extension.vsixmanifest`  
> 2.  Nell'elemento `Content` aggiungere:  
>   
>     ```xml  
>     <MefComponent>Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.Provider.dll</MefComponent>  
>     ```  
> 3.  Sotto il **Visual Studio Tools** sezione del menu start dell'applicazione di Visual Studio, aprire **Developer Command Prompt**.  
>   
>      Immettere:  
>   
>      `devenv /rootSuffix /updateConfiguration`  
>   
>      `devenv /rootSuffix Exp /updateConfiguration`  
> 4.  Riavviare Visual Studio.  
  
 **Assicurarsi che il codice sia in un progetto VSIX**  
  
 Se la proprietà fa parte di un comando, di un movimento o di un progetto di convalida, non è necessario aggiungere alcun valore. Il codice per la proprietà personalizzata deve essere specificato in un progetto Extensibility di Visual Studio definito come componente MEF. Per ulteriori informazioni, vedere [aggiungere comandi e movimenti a diagrammi di dipendenza](../modeling/add-commands-and-gestures-to-layer-diagrams.md) o [aggiungere la convalida architettura personalizzati a diagrammi di dipendenza](../modeling/add-custom-architecture-validation-to-layer-diagrams.md).  
  
 **Definire la proprietà personalizzata**  
  
 Per creare una proprietà personalizzata, definire una classe come quella seguente:  
  
```  
[Export(typeof(IPropertyExtension))]  
public class MyProperty   
      : PropertyExtension<ILayerElement>  
{  
  // Implement the interface.  
}  
```  
  
 È possibile definire le proprietà in <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>o una qualsiasi delle classi derivate, che includono:</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>  
  
-   `ILayerModel` - il modello  
  
-   `ILayer` - ciascun livello  
  
-   `ILayerDependencyLink` - i collegamenti tra i livelli  
  
-   `ILayerComment`  
  
-   `ILayerCommentLink`  
  
## <a name="example"></a>Esempio  
 Il codice seguente è un descrittore di proprietà personalizzate tipico. Definisce una proprietà booleana nel modello di livello (`ILayerModel`) che consente all'utente di specificare i valori per un metodo di convalida personalizzata.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;  
  
namespace MyNamespace  
{  
  /// <summary>  
  /// Custom properties are added to the Layer Designer via a custom  
  /// Property Descriptor. We have to export this Property Descriptor  
  /// using MEF to make it available in the Layer Designer.  
  /// </summary>  
  [Export(typeof(IPropertyExtension))]  
  public class AllTypesMustBeReferencedProperty   
      : PropertyExtension<ILayerModel>  
  {  
    /// <summary>  
    /// Each custom property must have a unique name.   
    /// Usually we use the full name of this class.  
    /// </summary>  
    public static readonly string FullName =  
      typeof(AllTypesMustBeReferencedProperty).FullName;  
  
    /// <summary>  
    /// Construct the property. Notice the use of FullName.  
    /// </summary>  
    public AllTypesMustBeReferencedProperty()  
            : base(FullName)  
    {  }  
  
    /// <summary>  
    /// The display name is shown in the Properties window.  
    /// We therefore use a localizable resource.  
    /// </summary>  
    public override string DisplayName  
    {  
      get { return Strings.AllTypesMustBeReferencedDisplayName; }  
    }  
  
    /// <summary>  
    /// Description shown at the bottom of the Properties window.  
    /// We use a resource string for easier localization.  
    /// </summary>  
    public override string Description  
    {  
      get { return Strings.AllTypesMustBeReferencedDescription; }  
    }  
  
    /// <summary>  
    /// This is called to set a new value for this property. We must  
    /// throw an exception if the value is invalid.  
    /// </summary>  
    /// <param name="component">The target ILayerElement</param>  
    /// <param name="value">The new value</param>  
    public override void SetValue(object component, object value)  
    {  
      ValidateValue(value);  
      base.SetValue(component, value);  
    }  
    /// <summary>  
    /// Helper to validate the value.  
    /// </summary>  
    /// <param name="value">The value to validate</param>  
    private static void ValidateValue(object value)  
    {  }  
  
    public override Type PropertyType  
    { get { return typeof(bool); } }  
  
    /// <summary>  
    /// The segment label of the properties window.  
    /// </summary>  
    public override string Category  
    {   
      get  
      {  
        return Strings.AllTypesMustBeReferencedCategory;  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Estendere i diagrammi di dipendenza](../modeling/extend-layer-diagrams.md)

