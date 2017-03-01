---
title: Esplorare e aggiornare i modelli di livello nel codice programma | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layer models, navigating in program code
- layer models, updating in program code
ms.assetid: c60edc87-33ee-4964-a954-40069f9febf3
caps.latest.revision: 20
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
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 626fc2b217285ae0c79dbd57f925281e10a0efbb
ms.lasthandoff: 02/22/2017

---
# <a name="navigate-and-update-layer-models-in-program-code"></a>Esplorare e aggiornare i modelli di livello nel codice del programma
Questo argomento descrive gli elementi e le relazioni nei modelli di livello, che è possibile esplorare e aggiornare usando codice programma. Per ulteriori informazioni sui diagrammi di dipendenza dal punto di vista dell'utente, vedere [diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md) e [diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md).  
  
 Il <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer>modello descritto in questo argomento è un aspetto di un più generale <xref:Microsoft.VisualStudio.GraphModel>modello.</xref:Microsoft.VisualStudio.GraphModel> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer> Se si sta scrivendo un [menu un'estensione di comandi o movimenti](../modeling/add-commands-and-gestures-to-layer-diagrams.md), utilizzare il `Layer` modello. Se si sta scrivendo un [estensione di convalida dei livelli](../modeling/add-custom-architecture-validation-to-layer-diagrams.md), è più facile utilizzare il `GraphModel`.  
  
## <a name="transactions"></a>Transazioni  
 Quando si aggiorna un modello, valutare la possibilità di includere le modifiche in un elemento `ILinkedUndoTransaction`. Ciò consente di raggruppare le modifiche in un'unica transazione. Se non è possibile apportare correttamente una modifica, viene eseguito il rollback dell'intera transazione. Se l'utente annulla una modifica, tutte le modifiche verranno annullate.  
  
```  
using (ILinkedUndoTransaction t =  
        LinkedUndoContext.BeginTransaction("a name"))  
{   
    // Make changes here ....  
    t.Commit(); // Don't forget this!  
}  
```  
  
## <a name="containment"></a>Contenuto  
 ![ILayer e ILayerModel possono contenere entrambi oggetti ILayers. ] (../modeling/media/layerapi_containment.png "LayerApi_Containment")  
  
 Livelli (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>) e il modello di livello (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>) possono contenere commenti e livelli.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayer>  
  
 Un livello (`ILayer`) può essere contenuto in un modello di livello (`ILayerModel`) o annidato in un altro elemento `ILayer`.  
  
 Per creare un commento o un livello, usare i metodi di creazione sul contenitore appropriato.  
  
## <a name="dependency-links"></a>Collegamenti di dipendenza  
 Un collegamento di dipendenza è rappresentato da un oggetto e può essere esplorato in entrambe le direzioni:  
  
 ![Oggetto ILayerDependencyLink che connette due ILayers. ] (../modeling/media/layerapi_dependency.png "LayerApi_Dependency")  
  
 Per creare un collegamento di dipendenza, chiamare `source.CreateDependencyLink(target)`.  
  
## <a name="comments"></a>Commenti  
 I commenti possono essere contenuti in livelli o nel modello di livello e possono inoltre essere collegati a qualsiasi elemento livello:  
  
 ![È possibile associare commenti a qualsiasi elemento livello. ] (../modeling/media/layerapi_comments.png "LayerApi_Comments")  
  
 Un commento può essere collegato a qualsiasi numero di elementi o a nessun elemento.  
  
 Per ottenere i commenti collegati a un elemento livello, usare:  
  
```c#  
ILayerModel model = diagram.GetLayerModel();   
IEnumerable<ILayerComment> comments =   
   model.Comments.Where(comment =>   
      comment.Links.Any(link => link.Target == layerElement));  
  
```  
  
> [!CAUTION]
>  La proprietà `Comments` di un elemento `ILayer` ottiene commenti contenuti nell'elemento `ILayer`. Non ottiene i commenti che sono collegati a esso.  
  
 Creare un commento richiamando `CreateComment()` sul contenitore appropriato.  
  
 Creare un collegamento usando `CreateLink()` sul commento.  
  
## <a name="layer-elements"></a>Elementi di livello  
 Tutti i tipi di elemento che possono essere contenuti in un modello sono elementi di livello:  
  
 ![diagramma delle dipendenze sono oggetti ILayerElements. ] (../modeling/media/layerapi_layerelements.png "LayerApi_LayerElements")  
  
## <a name="properties"></a>Proprietà  
 Ogni `ILayerElement` ha un dizionario di stringhe denominato`Properties`. È possibile usare questo dizionario per collegare informazioni arbitrarie a qualsiasi elemento livello.  
  
## <a name="artifact-references"></a>Riferimenti per artefatti  
 Un riferimento a elementi (<xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>) rappresenta il collegamento tra un livello e un elemento di progetto, ad esempio un file, una classe o una cartella.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference> L'utente crea gli elementi quando creano un livello o aggiungervi trascinando gli elementi da Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti in un diagramma di dipendenza. È possibile collegare qualsiasi numero di riferimenti per artefatti a un livello.  
  
 Ogni riga di Esplora livello visualizza un riferimento ad artefatti. Per ulteriori informazioni, vedere [creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md).  
  
 I tipi e i metodi principali interessati dai riferimenti ad artefatti sono i seguenti:  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerArtifactReference> La proprietà Categorie indica il tipo di artefatto al quale viene fatto riferimento, ad esempio una classe, un file eseguibile o un assembly. Questa proprietà determina le modalità di identificazione dell'artefatto di destinazione da parte dell'identificatore.  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A>Crea un riferimento a un elemento da una <xref:EnvDTE.Project>o <xref:EnvDTE.ProjectItem>.</xref:EnvDTE.ProjectItem> </xref:EnvDTE.Project></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ArtifactReferenceExtensions.CreateArtifactReferenceAsync%2A> Si tratta di un'operazione asincrona, quindi in genere si fornisce un callback che viene chiamato al termine della creazione.  
  
 I riferimenti a elementi del livello non devono essere confusi con gli elementi nei diagrammi dei casi di uso.  
  
## <a name="shapes-and-diagrams"></a>Forme e diagrammi  
 Due oggetti sono utilizzati per rappresentare ogni elemento in un modello di livello: un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement>e un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerElement> L'oggetto `IShape` rappresenta la posizione e la dimensione della forma sul diagramma. Nei modelli di livello ogni `ILayerElement` presenta uno `IShape`e ogni `IShape` in una dipendenza diagramma ha un `ILayerElement`. `IShape` è usato anche per i modelli UML, quindi non tutti gli oggetti `IShape` hanno un elemento livello.  
  
 Nello stesso modo, <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>viene visualizzato in un <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram> </xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.ILayerModel>  
  
 Nel codice di un gestore comandi o movimenti personalizzato, è possibile ottenere il diagramma corrente e la selezione corrente di forme dall'importazione `DiagramContext`:  
  
```  
public class ... {  
[Import]  
    public IDiagramContext DiagramContext { get; set; }  
...  
public void ... (...)   
{ IDiagram diagram = this.DiagramContext.CurrentDiagram;  
  ILayerModel model = diagram.GetLayerModel();  
  if (model != null)  
  { foreach (ILayer layer in model.Layers) { ... }}  
  foreach (IShape selected in diagram.SelectedShapes)  
  { ILayerElement element = selected.GetLayerElement();  
    if (element != null) ... }}  
```  
  
 ![Ogni oggetto ILayerElement è presentato da un oggetto IShape. ] (../modeling/media/layerapi_shapes.png "LayerApi_Shapes")  
  
 <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape>e <xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram>consentono inoltre di visualizzare modelli UML.</xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IDiagram></xref:Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation.IShape> Per ulteriori informazioni, vedere [visualizzare un modello UML nei diagrammi](../modeling/display-a-uml-model-on-diagrams.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiunta di comandi e movimenti a diagrammi di dipendenza](../modeling/add-commands-and-gestures-to-layer-diagrams.md)   
 [Aggiungere la convalida architettura personalizzati a diagrammi di dipendenza](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)   
 [Aggiungere proprietà personalizzate a diagrammi di dipendenza](../modeling/add-custom-properties-to-layer-diagrams.md)   
 [Diagrammi di dipendenza: riferimento](../modeling/layer-diagrams-reference.md)   
 [Diagrammi di dipendenza: linee guida](../modeling/layer-diagrams-guidelines.md)   

