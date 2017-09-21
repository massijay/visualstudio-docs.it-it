---
title: "Extract Interface Refactoring (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.csharp.refactoring.extractinterface"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Extract Interface"
  - "Extract Interface refactoring operation [C#]"
ms.assetid: 7d0aa225-3b33-4331-9652-5a67cac6f3d0
caps.latest.revision: 25
caps.handback.revision: 25
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Extract Interface Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'operazione di refactoring Estrai interfaccia consente di creare una nuova interfaccia con membri che provengono da una classe, uno struct o un'interfaccia esistente.  
  
 Quando in diversi client viene utilizzato lo stesso sottoinsieme di membri di una classe, uno struct o un'interfaccia o quando un sottoinsieme di membri è comune a diverse classi, struct o interfacce, può essere utile incorporare il sottoinsieme di membri in un'interfaccia.  Per ulteriori informazioni sull'utilizzo delle interfacce, vedere [Interfacce](/dotnet/csharp/programming-guide/interfaces/index).  
  
 Estrai interfaccia consente di generare un'interfaccia in un nuovo file, posizionando il cursore all'inizio del nuovo file.  È possibile specificare quali membri estrarre nella nuova interfaccia, il nome della nuova interfaccia e il nome del file generato utilizzando la finestra di dialogo **Estrai interfaccia**.  
  
### Per utilizzare Estrai interfaccia  
  
1.  Creare un'applicazione console denominata `ExtractInterface` quindi sostituire `Program` con il codice riportato di seguito.  
  
    ```c#  
    // Invoke Extract Interface on ProtoA.  
    // Note:  the extracted interface will be created in a new file.  
    class ProtoA  
    {  
        public void MethodB(string s) { }  
    }  
    ```  
  
2.  Dopo aver posizionato il cursore in `MethodB`, selezionare **Estrai interfaccia** dal menu **Effettua refactoring**.  
  
     Verrà visualizzata la finestra di dialogo **Estrai interfaccia**.  
  
     È anche possibile premere i tasti di scelta rapida CTRL\+R, I per visualizzare la finestra di dialogo **Estrai interfaccia**.  
  
     È inoltre possibile fare clic con il pulsante destro del mouse, scegliere **Effettua refactoring**, quindi fare clic su **Estrai interfaccia** per visualizzare la finestra di dialogo **Estrai interfaccia**.  
  
3.  Fare clic su **Seleziona tutto**.  
  
4.  Scegliere **OK**.  
  
     Verranno visualizzati il nuovo file, IProtoA.cs, e il codice di seguito riportato:  
  
    ```c#  
    using System;  
    namespace TopThreeRefactorings  
    {  
        interface IProtoA  
        {  
            void MethodB(string s);  
        }  
    }  
    ```  
  
## Note  
 Questa funzionalità è accessibile solo quando il cursore è posizionato nella classe, lo struct o l'interfaccia che contiene i membri da estrarre.  Quando il cursore si trova in questa posizione, richiamare l'operazione di refactoring Estrai interfaccia.  
  
 Quando si richiama Estrai interfaccia su una classe o uno struct, l'elenco delle basi e delle interfacce viene modificato per includere il nome della nuova interfaccia.  Quando si richiama Estrai interfaccia su un'interfaccia, l'elenco delle basi e delle interfacce non viene modificato.  
  
## Vedere anche  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)