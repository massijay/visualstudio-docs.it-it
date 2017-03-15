---
title: "Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, eventi"
ms.assetid: 4d08e541-fc67-4e68-bf31-30d346aa2aa0
caps.latest.revision: 18
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 18
---
# Le regole associate (BoundsRules) vincolano posizione e dimensione delle forme
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In *regola limiti* è una classe che definisce i limiti della dimensione e la posizione di una forma.  Fornisce un metodo che viene chiamato ripetutamente mentre l'utente sta trascinando una forma o gli angoli o i lati della forma.  
  
 Nell'esempio vincola una forma rettangolare sia una barra di dimensione fissa, orizzontale o verticale.  Quando l'utente trascina gli angoli o i lati, le vibrazioni struttura tra le due configurazioni consentite di altezza e larghezza.  
  
 La regola limiti è una classe derivata da <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>.  Un'istanza della regola verrà creata nella forma:  
  
```  
using Microsoft.VisualStudio.Modeling.Diagrams; ...  
public partial class BarShape  
{  
  /// <summary>  
  /// Rule invoked when the user is resizing a shape.  
  /// </summary>  
  public override BoundsRules BoundsRules  
  { get { return new BarBoundsRule(); } }  
}  
/// <summary>  
/// Rule invoked when the user is changing a shape's outline.  
/// Provides real-time mouse rubber-band feedback, so must work fast.  
/// </summary>  
public class BarBoundsRule: BoundsRules  
{   
  public override RectangleD GetCompliantBounds   
     (ShapeElement shape, RectangleD proposedBounds)  
  {  
    double thickness = 0.1;  
    if (proposedBounds.Height > proposedBounds.Width)  
    {  
      // There is a minimum width for a shape; the width  
      // will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
            new SizeD(thickness, proposedBounds.Height));  
    }  
    else  
    {  
      // There is a minimum height for a shape; the   
      // height will actually be set to the lesser of   
      // thickness and that minimum.  
      return new RectangleD(proposedBounds.Location,   
         new SizeD(proposedBounds.Width, thickness));  
} } }  
```  
  
 Si noti che di posizione e le dimensioni possono essere vincolate se lo si desidera.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BoundsRules>   
 [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)