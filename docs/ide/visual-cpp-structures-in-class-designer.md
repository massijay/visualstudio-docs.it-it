---
title: "Visual C++ Structures in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], structures"
ms.assetid: bad18ab6-d956-47a6-a413-811cc26db5f5
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Structures in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La Progettazione classi supporta strutture C\+\+ dichiarate tramite la parola chiave `struct`.  Di seguito è riportato un esempio:  
  
```  
struct MyStructure  
{  
   char a;  
   int i;  
   long j;  
};  
```  
  
 Per ulteriori informazioni sull'utilizzo del tipo `struct` vedere [struct](/visual-cpp/cpp/struct-cpp).  
  
 Una forma della struttura C\+\+ in un diagramma classi viene visualizzata e funziona come una forma della classe, con l'eccezione che l'etichetta **Struct** ha angoli quadrati anziché angoli arrotondati.  
  
|Elemento di codice|Visualizzazione di Progettazione classi|  
|------------------------|---------------------------------------------|  
|`struct StructureName {};`|**NomeStruttura**<br /><br /> Struct|  
  
## Vedere anche  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Classi e struct](/visual-cpp/cpp/classes-and-structs-cpp)   
 [struct](/visual-cpp/cpp/struct-cpp)