---
title: "Reorder Parameters Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.reorder"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Reorder Parameters"
  - "Reorder Parameters refactoring [C#]"
ms.assetid: 4dabf21a-a9f0-41e9-b11b-55760cf2bd90
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Reorder Parameters Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Reorder Parameters` è un'operazione di refactoring di Visual C\# che fornisce un modo semplice per modificare l'ordine dei parametri per metodi, indicizzatori e delegati.  `Reorder Parameters` consente di modificare la dichiarazione e, in qualsiasi posizione venga chiamato il membro, i parametri vengono ridisposti per riflettere il nuovo ordine.  
  
 Per eseguire l'operazione `Reorder Parameters`, posizionare il cursore sopra o accanto a un metodo, indicizzatore o delegato.  Quando il cursore è in posizione, richiamare l'operazione `Reorder Parameters` premendo i tasti di scelta rapida o facendo clic sul comando da un menu di scelta rapida.  
  
> [!NOTE]
>  Il primo parametro non può essere riordinato in un metodo di estensione.  
  
### Per riordinare i parametri  
  
1.  Creare una libreria di classi denominata `ReorderParameters`, quindi sostituire `Class1` con il codice di esempio riportato di seguito.  
  
    ```c#  
    class ProtoClassA  
    {  
        // Invoke on 'MethodB'.  
        public void MethodB(int i, bool b) { }  
    }  
  
    class ProtoClassC  
    {  
        void D()  
        {  
            ProtoClassA MyClassA = new ProtoClassA();  
  
            // Invoke on 'MethodB'.  
            MyClassA.MethodB(0, false);  
        }  
    }  
    ```  
  
2.  Posizionare il cursore su `MethodB`, nella dichiarazione di metodo o nella chiamata di metodo.  
  
3.  Selezionare **Riordina parametri** dal menu **Effettua refactoring**.  
  
     Verrà visualizzata la finestra di dialogo **Riordina parametri**.  
  
4.  Nella finestra di dialogo **Riordina parametri** selezionare `int i` dall'elenco **Parametri**, quindi fare clic sul pulsante Giù.  
  
     In alternativa, è possibile trascinare `int i` dopo `bool b` nell'elenco **Parametri**.  
  
5.  Scegliere **OK** nella finestra di dialogo **Riordina parametri**.  
  
     Se nella finestra di dialogo **Riordina parametri** è selezionata l'opzione **Anteprima modifiche riferimento**, verrà visualizzata la finestra di dialogo **Anteprima modifiche \- Riordina parametri** che fornisce un'anteprima delle modifiche nell'elenco dei parametri per `MethodB` nella firma e nella chiamata al metodo.  
  
    1.  Se viene visualizzata la finestra di dialogo **Anteprima modifiche \- Riordina parametri**, fare clic su **Applica**.  
  
         In questo esempio vengono aggiornati la dichiarazione del metodo e tutti i siti di chiamata al metodo per `MethodB`.  
  
## Note  
 I parametri possono essere riordinati da una dichiarazione di metodo o una chiamata al metodo.  Posizionare il cursore sopra o accanto al metodo o alla dichiarazione di delegato, ma non nel corpo.  
  
## Vedere anche  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)