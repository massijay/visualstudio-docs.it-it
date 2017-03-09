---
title: "Refactoring Estrai Metodo (C#) | Microsoft Docs"
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
  - "vs.csharp.refactoring.extractmethod"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "refactoring [C#], Estrai metodo"
  - "Estrai metodo (operazione di refactoring) [C#]"
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
caps.handback.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Refactoring Estrai Metodo (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Estrai metodo** è un'operazione di refactoring che consente di creare facilmente un nuovo metodo da un frammento di codice in un membro esistente.  
  
 Con **Estrai metodo** è possibile creare un nuovo metodo tramite l'estrazione di una selezione di codice dal blocco di codice di un membro esistente.  Il nuovo metodo estratto contiene il codice selezionato, mentre il codice selezionato nel membro esistente viene sostituito con una chiamata al nuovo metodo.  Se si trasforma un frammento di codice in un metodo corrispondente, sarà possibile riorganizzare il codice in modo rapido e accurato per migliorarne il riutilizzo e la leggibilità.  
  
 L'utilizzo di **Estrai metodo** comporta i seguenti vantaggi:  
  
-   Fornisce procedure di codifica migliori presentando metodi distinti e riutilizzabili.  
  
-   Fornisce codice autodocumentato mediante una buona organizzazione.  
  
     Quando si utilizzano nomi descrittivi, i metodi di alto livello possono fornire maggiori informazioni, come una serie di commenti.  
  
-   Favorisce la creazione di metodi più controllati per semplificare l'override.  
  
-   Riduce la duplicazione del codice.  
  
### Per utilizzare Estrai metodo  
  
1.  Creare un'applicazione console denominata `ExtractMethod` quindi sostituire `Program` con il codice di esempio riportato di seguito.  
  
    ```c#  
    class A  
    {  
        const double PI = 3.141592;  
  
        double CalculatePaintNeeded(double paintPerUnit, double radius)  
        {  
            // Select any of the following:  
            // 1. The entire next line of code.  
            // 2. The right-hand side of the next line of code.  
            // 3. Just "PI *" of the right-hand side of the next line  
            //    of code (to see the prompt for selection expansion).  
            // 4.  All code within the method body.  
            // ...Then invoke Extract Method.  
  
            double area = PI * radius * radius;  
  
            return area / paintPerUnit;  
        }  
    }  
    ```  
  
2.  Consente di selezionare il frammento di codice da estrarre:  
  
    ```c#  
    double area = PI * radius * radius;  
  
    ```  
  
3.  Scegliere **Estrai metodo** dal menu **Effettua refactoring**.  
  
     Viene visualizzata la finestra di dialogo **Estrai metodo**.  
  
     In alternativa, è anche possibile premere i tasti di scelta rapida CTRL\+R, M per visualizzare la finestra di dialogo **Estrai metodo**.  
  
     Inoltre è possibile fare clic con il pulsante destro del mouse sul codice selezionato, scegliere **Effettua refactoring**, quindi fare clic su **Estrai metodo** per visualizzare la finestra di dialogo **Estrai metodo**.  
  
4.  Specificare un nome per il nuovo metodo, ad esempio `CircleArea`, nella casella **Nuovo nome metodo**.  
  
     Verrà visualizzata un'anteprima della firma del nuovo metodo in **Anteprima firma del metodo**.  
  
5.  Scegliere **OK**.  
  
## Note  
 Quando si utilizza il comando **Estrai metodo**, il nuovo metodo viene inserito dopo il membro di origine nella stessa classe.  
  
## Tipi parziali  
 Se la classe è un tipo parziale, **Estrai metodo** genera il nuovo metodo immediatamente dopo il membro di origine.  **Estrai metodo** determina la firma del nuovo metodo, creando un metodo statico quando il codice all'interno del nuovo metodo non fa riferimento a dati di istanza.  
  
## Parametri di tipo generico  
 Quando si estrae un metodo con un parametro di tipo generico non vincolato, il codice generato non aggiungerà il modificatore `ref` a tale parametro, a meno che non gli venga assegnato un valore.  Se il metodo estratto supporta tipi di riferimento come l'argomento di tipo generico, sarà necessario aggiungere manualmente il modificatore `ref` al parametro nella firma del metodo.  
  
## Metodi anonimi  
 Se si tenta di estrarre una parte di un metodo anonimo che include un riferimento a una variabile locale dichiarata o a cui si fa riferimento al di fuori del metodo anonimo, Visual Studio genererà un avviso sulle potenziali modifiche della semantica.  
  
 Quando un metodo anonimo utilizza il valore di una variabile locale, il valore viene restituito al momento dell'esecuzione del metodo anonimo.  Quando si estrae un metodo anonimo in un altro metodo, il valore della variabile locale viene restituito al momento della chiamata al metodo estratto.  
  
 Questa modifica della semantica viene illustrata nell'esempio riportato di seguito.  Se si esegue il codice, nella console verrà stampato **11**.  Se si utilizza **Estrai metodo** per estrarre l'area di codice contrassegnata da commenti nel relativo metodo e si esegue il codice di cui è stato effettuato il refactoring, nella console verrà stampato **10**.  
  
```c#  
class Program  
{  
    delegate void D();  
    D d;  
    static void Main(string[] args)  
    {  
        Program p = new Program();  
        int i = 10;  
        /*begin extraction*/  
            p.d = delegate { Console.WriteLine(i++); };  
        /*end extraction*/  
        i++;  
        p.d();  
    }  
}  
```  
  
 Per ovviare a questo problema, trasformare le variabili locali utilizzate nei campi del metodo anonimo della classe.  
  
## Vedere anche  
 [Refactoring \(C\#\)](../csharp-ide/refactoring-csharp.md)