---
title: "Refactoring Rimuovi parametri (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.remove"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "parametri [C#], rimozione"
  - "refactoring [C#], Rimuovi parametri"
  - "Refactoring Rimuovi parametri [C#]"
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
caps.handback.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactoring Rimuovi parametri (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`Remove Parameters` è un'operazione di refactoring che offre un modo semplice per rimuovere i parametri dai metodi, indicizzatori o delegati.  Rimuovi parametri modifica la dichiarazione; in qualsiasi posizione in cui il membro venga chiamato, il parametro viene rimosso per riflettere la nuova dichiarazione.  
  
 L'operazione Remove Parameters deve essere eseguita posizionando innanzitutto il cursore su un metodo, un indicizzatore o un delegato.  Quando il cursore è in posizione, per richiamare l'operazione Rimuovi `Parameters`, fare clic sul menu **Effettua refactoring**, premere il tasto di scelta rapida o scegliere il comando dal menu di scelta rapida.  
  
> [!NOTE]
>  Il primo parametro non può essere rimosso in un metodo di estensione.  
  
### Per rimuovere i parametri  
  
1.  Creare un'applicazione console denominata `RemoveParameters` quindi sostituire `Program` con il codice riportato di seguito.  
  
    ```c#  
    class A  
    {  
        // Invoke on 'A'.  
        public A(string s, int i) { }  
    }  
  
    class B  
    {  
        void C()  
        {  
            // Invoke on 'A'.  
            A a = new A("a", 2);  
        }  
    }  
    ```  
  
2.  Posizionare il cursore sul metodo `A`, nella dichiarazione di metodo o nella chiamata di metodo.  
  
3.  Dal menu **Refactoring**, selezionare **Rimuovi parametri** per visualizzare la finestra di dialogo **Rimuovi parametri**.  
  
     In alternativa è possibile premere i tasti di scelta rapida CTRL\+R, V  
  
     oppure fare clic con il pulsante destro del mouse sul cursore, scegliere **Effettua refactoring** e selezionare quindi **Rimuovi parametri**.  
  
4.  Nel campo **Parametri**, posizionare il cursore su `int i`, quindi fare clic su **Rimuovi**.  
  
5.  Scegliere **OK**.  
  
6.  Nella finestra di dialogo **Anteprima modifiche \- Rimuovi parametri** fare clic su **Applica**.  
  
## Note  
 I parametri possono essere rimossi da una dichiarazione di metodo o una chiamata al metodo.  Posizionare il cursore sulla dichiarazione di metodo o sul nome delegato e richiamare Rimuovi parametri.  
  
> [!CAUTION]
>  Rimuovi parametri consente di rimuovere un parametro a cui si fa riferimento nel corpo del membro, ma non di rimuovere i riferimenti a tale parametro nel corpo del metodo.  Questa operazione può comportare errori durante la compilazione nel codice.  Tuttavia, è possibile utilizzare la finestra di dialogo **Anteprima modifiche** per esaminare il codice, prima di eseguire l'operazione di refactoring.  
  
 Se il parametro in corso di rimozione viene modificato durante la chiamata a un metodo, la rimozione del parametro comporterà anche la rimozione della modifica.  Ad esempio, se una chiamata al metodo viene modificata da  
  
```c#  
MyMethod(param1++, param2);  
```  
  
 in  
  
```c#  
MyMethod(param2);  
```  
  
 mediante l'operazione di refactoring, `param1` non verrà aggiunto.  
  
## Vedere anche  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)