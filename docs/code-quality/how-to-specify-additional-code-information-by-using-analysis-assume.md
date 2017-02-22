---
title: "Procedura: specificare informazioni aggiuntive sul codice utilizzando __analysis_assume | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__analysis_assume"
helpviewer_keywords: 
  - "__analysis_assume"
ms.assetid: 51205d97-4084-4cf4-a5ed-3eeaf67deb1b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Procedura: specificare informazioni aggiuntive sul codice utilizzando __analysis_assume
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile fornire suggerimenti allo strumento di analisi del codice per codice C\/C\+\+ per semplificare il processo di analisi e ridurre gli avvisi.  Per fornire informazioni aggiuntive, utilizzare la funzione seguente:  
  
 `__analysis_assume(`  `expr`  `)`  
  
 `expr`\- qualsiasi espressione che deve restituire true.  
  
 Lo strumento di analisi del codice presuppone che la condizione rappresentata dall'espressione sia vera nel punto in cui la funzione viene visualizzata e rimanga vera finché non viene apportata una modifica all'espressione, ad esempio tramite assegnazione a una variabile.  
  
> [!NOTE]
>  `__analysis_assume` non influisce sull'ottimizzazione del codice.  Al di fuori dello strumento di analisi del codice, la funzione `__analysis_assume` viene definita operazione no\-op.  
  
## Esempio  
 Nel codice seguente viene utilizzato `__analysis_assume` per correggere l'avviso [C6388](../code-quality/c6388.md) dell'analisi del codice:  
  
```  
#include<windows.h>  
#include<codeanalysis\sourceannotations.h>  
  
using namespace vc_attributes;  
  
// calls free and sets ch to null  
void FreeAndNull(char* ch);  
  
//requires pc to be null  
void f([Pre(Null=Yes)] char* pc);  
  
void test( )  
{  
  char *pc = (char*)malloc(5);  
  FreeAndNull(pc);  
  __analysis_assume(pc == NULL);   
  f(pc);  
}  
```  
  
## Vedere anche  
 [\_\_assume](/visual-cpp/intrinsics/assume)