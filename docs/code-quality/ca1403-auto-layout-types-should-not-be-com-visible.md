---
title: 'CA1403: I tipi layout automatici non devono essere visibili a COM | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- AutoLayoutTypesShouldNotBeComVisible
- CA1403
helpviewer_keywords:
- CA1403
- AutoLayoutTypesShouldNotBeComVisible
ms.assetid: a7007714-f9b4-4730-94e0-67d3dc68991f
caps.latest.revision: "17"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e5f8617b7ed5f0bec9ecaa2f4fbca1653cee46f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1403-auto-layout-types-should-not-be-com-visible"></a>CA1403: I tipi layout automatici non devono essere visibili a COM
|||  
|-|-|  
|TypeName|AutoLayoutTypesShouldNotBeComVisible|  
|CheckId|CA1403|  
|Categoria|Microsoft.Interoperability|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Un tipo di valore modello COM (Component Object) è contrassegnato con il <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=fullName> attributo impostato su <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=fullName>.  
  
## <a name="rule-description"></a>Descrizione della regola  
 <xref:System.Runtime.InteropServices.LayoutKind>tipi di layout sono gestiti da common language runtime. Il layout di questi tipi possa cambiare tra le versioni di .NET Framework, che interromperanno il client COM che prevede un layout specifico. Si noti che se il <xref:System.Runtime.InteropServices.StructLayoutAttribute> attributo non è specificato, c#, [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], e i compilatori C++ specificano il <xref:System.Runtime.InteropServices.LayoutKind> layout per i tipi di valore.  
  
 Se non diversamente specificato, tutti i tipi non generici pubblici sono visibili a COM. tutti i tipi generici e non pubblici non sono visibili a COM. Tuttavia, per ridurre i falsi positivi, la regola richiede la visibilità COM di tipo per indicare in modo esplicito; l'assembly che contiene deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> impostato su `false` e il tipo deve essere contrassegnato con il <xref:System.Runtime.InteropServices.ComVisibleAttribute> impostato su `true`.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, modificare il valore della <xref:System.Runtime.InteropServices.StructLayoutAttribute> attributo <xref:System.Runtime.InteropServices.LayoutKind> o <xref:System.Runtime.InteropServices.LayoutKind>, oppure rendere il tipo visibile a COM.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## <a name="example"></a>Esempio  
 Nell'esempio seguente viene illustrato un tipo che viola la regola e un tipo che soddisfa la regola.  
  
 [!code-csharp[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/CSharp/ca1403-auto-layout-types-should-not-be-com-visible_1.cs)]
 [!code-vb[FxCop.Interoperability.AutoLayout#1](../code-quality/codesnippet/VisualBasic/ca1403-auto-layout-types-should-not-be-com-visible_1.vb)]  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1408: Non usare AutoDual ClassInterfaceType](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione all'interfaccia della classe](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)   
 [Qualificazione di tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)