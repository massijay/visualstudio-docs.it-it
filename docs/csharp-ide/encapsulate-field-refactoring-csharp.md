---
title: "Encapsulate Field Refactoring (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.encapsulatefield"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "Encapsulate Field refactoring operation [C#]"
  - "refactoring [C#], Encapsulate Field"
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Encapsulate Field Refactoring (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'operazione di refactoring **Incapsula campo** consente di creare rapidamente una proprietà da un campo esistente e di aggiornare facilmente il codice con riferimenti alla nuova proprietà.  
  
 Quando un [campo](/dotnet/csharp/programming-guide/classes-and-structs/fields) è [public](/dotnet/csharp/language-reference/keywords/public), altri oggetti possono accedere direttamente a tale campo e modificarlo, senza essere rilevati dall'oggetto a cui appartiene il campo.  Usando le [proprietà](/dotnet/csharp/programming-guide/classes-and-structs/properties) per incapsulare il campo, è possibile disattivare l'accesso diretto ai campi.  
  
 Per creare la nuova proprietà, l'operazione **Incapsula campo** imposta il modificatore di accesso relativo al campo che si vuole incapsulare su [private](/dotnet/csharp/language-reference/keywords/private), quindi genera le funzioni di accesso [get](/dotnet/csharp/language-reference/keywords/get) e [set](/dotnet/csharp/language-reference/keywords/set) per tale campo.  In alcuni casi, viene generata una sola funzione di accesso `get`, ad esempio quando il campo viene dichiarato di sola lettura.  
  
 Il motore di refactoring consente di aggiornare il codice con i riferimenti alla nuova proprietà nelle aree specificate nella sezione **Aggiorna riferimenti** della finestra di dialogo **Incapsula campo**.  
  
### Per creare una proprietà da un campo  
  
1.  Creare un'applicazione console denominata `EncapsulateFieldExample` quindi sostituire `Program` con il codice di esempio seguente.  
  
    ```c#  
    class Square  
    {  
        // Select the word 'width' and then use Encapsulate Field.  
        public int width, height;  
    }  
    class MainClass  
    {  
        public static void Main()  
        {  
            Square mySquare = new Square();  
            mySquare.width = 110;  
            mySquare.height = 150;  
            // Output values for width and height.  
            Console.WriteLine("width = {0}", mySquare.width);  
            Console.WriteLine("height = {0}", mySquare.height);  
        }  
    }  
    ```  
  
2.  Nell'[editor di codice](../ide/writing-code-in-the-code-and-text-editor.md) posizionare il cursore nella dichiarazione, sul nome del campo che si vuole incapsulare.  Nell'esempio seguente, posizionare il cursore sulla parola `width`:  
  
    ```c#  
    public int width, height;  
    ```  
  
3.  Nel menu **Refactoring** fare clic su **Incapsula campo**.  
  
     Viene visualizzata la finestra di dialogo **Incapsula campo**.  
  
     È inoltre possibile digitare il tasto di scelta rapida CTRL \+ R, E per visualizzare la finestra di dialogo **Incapsula campo**.  
  
     È inoltre possibile fare clic sul tasto destro del mouse del cursore, scegliere **Refactoring**, quindi fare clic su **Incapsula campo** per visualizzare la finestra di dialogo **Incapsula campo**.  
  
4.  Specificare le impostazioni.  
  
5.  Premere INVIO o fare clic sul pulsante **OK**.  
  
6.  Se è stata selezionata l'opzione **Anteprima modifiche riferimento** opzione, viene visualizzata la finestra **Anteprima modifiche riferimento**.  Fare clic sul pulsante **Applica**.  
  
     Nel file di origine verrà visualizzato il codice delle funzioni di accesso `get` e `set` seguenti:  
  
    ```c#  
    public int Width  
    {  
        get { return width; }  
        set { width = value; }  
    }  
    ```  
  
     Anche il codice nel metodo `Main` viene aggiornato in base al nuovo nome della proprietà `Width`.  
  
    ```c#  
    Square mySquare = new Square();  
    mySquare.Width = 110;  
    mySquare.height = 150;  
    // Output values for width and height.  
    Console.WriteLine("width = {0}", mySquare.Width);  
    ```  
  
## Note  
 L'operazione **Incapsula campo** può essere eseguita solo quando il cursore è posizionato sulla stessa riga della dichiarazione di campo.  
  
 Per le dichiarazioni relative a più campi, **Incapsula campo** usa la virgola come limite tra i campi e avvia il refactoring nel campo più vicino al cursore e sulla stessa riga del cursore.  È inoltre possibile specificare il campo che si desidera incapsulare selezionandone il nome nella dichiarazione.  
  
 Il codice generato da questa operazione di refactoring viene modellato dalla funzionalità di frammenti di codice per Incapsula campo.  I frammenti di codice sono modificabili.  Per altre informazioni, vedere [Frammenti di codice](../ide/code-snippets.md).  
  
## Vedere anche  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)   
 [Frammenti di codice Visual C\#](../ide/visual-csharp-code-snippets.md)