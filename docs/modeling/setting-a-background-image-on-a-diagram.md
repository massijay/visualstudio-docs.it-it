---
title: "Impostazione di un&#39;immagine di sfondo in un diagramma | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Impostazione di un&#39;immagine di sfondo in un diagramma
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Visualization and Modeling SDK è possibile impostare l'immagine di sfondo per una finestra di progettazione generata tramite codice personalizzato.  
  
## Impostazione dell'immagine di sfondo  
  
#### Per impostare un'immagine di sfondo per una finestra di progettazione generata  
  
1.  Copiare il file di immagine da usare come sfondo per il diagramma nella directory Dsl\\Resources del progetto corrente.  
  
2.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla cartella Dsl\\Resources, scegliere **Aggiungi** e quindi fare clic su **Elemento esistente**.  
  
3.  Nella finestra di dialogo **Aggiungi elemento esistente** passare alla cartella Dsl\\Resources.  
  
4.  Nell'elenco **Tipo file** fare clic su **File di immagine**.  
  
5.  Fare clic sul file di immagine copiato nella directory e quindi fare clic su **Aggiungi**.  
  
6.  Fare clic con il pulsante destro del mouse su Dsl e scegliere **Proprietà** per aprire la finestra delle proprietà del progetto DSL.  
  
7.  Nella scheda **Risorse** fare clic su **Il progetto non contiene un file di risorse predefinito. Fare clic qui per crearne uno.**  
  
8.  Aggiungere il file di immagine al file di risorse trascinando l'immagine da **Esplora soluzioni** nella finestra delle risorse.  
  
9. Aprire il menu File e fare clic sull'opzione per salvare le proprietà del progetto.  
  
10. Verificare che il file Dsl\\Properties\\Resources.resx sia presente e contenga il file Resources.Designer.cs.  
  
11. Se Resources.Designer.cs non è presente, fare clic sul file Resources.resx in **Esplora soluzioni**.  
  
12. Nella finestra **Proprietà** impostare la proprietà `Custom Tool` su `ResXFileCodeGenerator`.  
  
13. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto DSL, scegliere **Aggiungi** e fare clic su **Nuova cartella**.  
  
14. Denominare la cartella Custom.  
  
15. Fare clic con il pulsante destro del mouse sulla cartella Custom, scegliere **Aggiungi** e quindi **Nuovo elemento**.  
  
16. Nella finestra di dialogo **Aggiungi nuovo elemento**  fare clic su **File di codice** nell'elenco **Modelli**.  
  
17. Nella casella **Nome** digitare `BackgroundImage.cs` e fare clic su **Aggiungi**.  
  
18. Copiare il codice seguente nel file BackgroundImage.cs, usando lo spazio dei nomi, il nome della classe del diagramma e il nome della risorsa del file di immagine corretti.  
  
     Sostituire "MyDiagramClass" con il nome della classe parziale del diagramma definita in Dsl\\GeneratedCode\\Diagrams.cs.  È anche possibile recuperare lo spazio dei nomi corretto dal file Dsl\\GeneratedCode\\Diagrams.cs.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Per altre informazioni sulla personalizzazione del modello con il codice programma, vedere [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## Vedere anche  
 [Definizione di forme e connettori](../modeling/defining-shapes-and-connectors.md)   
 [Personalizzazione dei campi testo e immagine](../modeling/customizing-text-and-image-fields.md)   
 [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)