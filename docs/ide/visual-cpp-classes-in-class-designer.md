---
title: "Visual C++ Classes in Class Designer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.classdesigner.inheritancelinelabel"
helpviewer_keywords: 
  - "Class Designer [Visual Studio], classes"
ms.assetid: 75e56f8c-11ef-42a3-b7ec-3d2cf25c581b
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Visual C++ Classes in Class Designer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Progettazione classi supporta classi C\+\+ e visualizza classi C\+\+ native in modo analogo alle forme delle classi di Visual Basic e Visual C\#, con la differenza che le classi C\+\+ possono avere relazioni di ereditarietà multiple.  È possibile espandere la forma della classe per mostrare più campi e metodi nella classe oppure comprimerla per risparmiare spazio.  
  
> [!NOTE]
>  Progettazione classi non supporta unioni \(un tipo speciale di classe nel quale la memoria allocata è solo la quantità necessario per membro dati più grande dell'unione\).  
  
## Ereditarietà semplice  
 Quando si trascina più di una classe su un diagramma classi e le classi presentano una relazione di ereditarietà, vengono connesse mediante una freccia.  La freccia punta in direzione della classe di base.  Ad esempio, quando le seguenti classi vengono visualizzate in un diagramma classi, una freccia le connette, puntando da B ad A:  
  
```  
class A {};  
class B : A {};  
```  
  
 È anche possibile trascinare solo la classe B sul diagramma classi, fare clic col pulsante destro del mouse sulla forma della classe per B quindi fare clic su **Mostra classi base**.  Verrà visualizzata la relativa classe di base: A.  
  
## Ereditarietà multipla  
 Progettazione classi supporta la visualizzazione di relazioni di ereditarietà da classi multiple.  *Ereditarietà multipla* viene utilizzata quando una classe derivata presenta attributi di più di una classe di base.  Di seguito è riportato un esempio di ereditarietà multipla:  
  
```  
class Bird {};  
class Swimmer {};  
class Penguin : public Bird, public Swimmer {};  
```  
  
 Quando si trascina più di una classe sul diagramma classi e le classi presentano una relazione di ereditarietà multipla, vengono connesse mediante una freccia.  La freccia punta in direzione delle classi di base.  
  
 Facendo clic col pulsante destro del mouse su una forma della classe e quindi su **Mostra classi base** verranno visualizzate le classi di base per la classe selezionata.  
  
> [!NOTE]
>  Il comando **Mostra classi derivate** non è supportato per il codice C\+\+.  È possibile visualizzare le classi derivate scegliendo Visualizzazione classi, espandendo il nodo dei tipi, espandendo la sottocartella **Tipi derivati** e trascinando quindi tali tipi sul diagramma classi.  
  
 Per ulteriori informazioni sulle ereditarietà da classi multiple, vedere [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/it-it/3b74185e-2beb-4e29-8684-441e51d2a2ca) e [Più classi base](/visual-cpp/cpp/multiple-base-classes).  
  
## Classi astratte  
 In Progettazione classi sono supportate le classi astratte, chiamate anche "classi base astratte".  Queste classi non vengono mai utilizzate per creare istanze, ma da esse si possono derivare altre classi.  Utilizzando un esempio citato in "Ereditarietà multipla" più indietro in questo documento, è possibile creare l'istanza della classe `Bird` come oggetti singoli nel modo indicato di seguito:  
  
```  
int main()  
{  
   Bird sparrow;  
   Bird crow;  
   Bird eagle;  
}  
```  
  
 Tuttavia, è possibile che non si intenda creare l'istanza della classe `Swimmer` come oggetti singoli.  Piuttosto, è possibile che si desideri solo derivare altri tipi di classi animali, ad esempio `Penguin`, `Whale` e `Fish`.  In questo caso, è necessario dichiarare la classe `Swimmer` come una classe base astratta.  
  
 Per dichiarare una classe come astratta, è possibile utilizzare la parola chiave `abstract`.  I membri contrassegnati come astratti o inclusi in una classe astratta sono virtuali e devono essere implementati da classi che derivano dalla classe astratta.  
  
```  
class Swimmer abstract  
{  
   virtual void swim();  
   void dive();  
};  
```  
  
 È possibile dichiarare una classe astratta anche includendo almeno una funzione virtuale pura:  
  
```  
class Swimmer  
{  
   virtual void swim() = 0;  
   void dive();  
};  
```  
  
 Quando si visualizzano queste dichiarazioni in un diagramma di classi, il nome della classe `Swimmer` e la relativa funzione virtuale pura `swim` vengono visualizzate in corsivo in una forma di classe astratta, insieme all'annotazione **Classe astratta**.  La forma del tipo di classe astratta è uguale a quella della classe regolare, eccetto per il bordo costituito da una linea punteggiata.  
  
 Una classe derivata da una classe base astratta deve eseguire l'override di ogni funzione virtuale pura della classe base o non è possibile creare l'istanza della classe derivata.  Quindi, se ad esempio una classe `Fish` deriva dalla classe `Swimmer`, `Fish` deve eseguire l'override del metodo `swim`:  
  
```  
class Fish : public Swimmer  
{  
   void swim(int speed);  
};  
  
int main()  
{  
   Fish guppy;  
}  
```  
  
 Quando si visualizza il codice in un diagramma di classi, viene disegnata una linea di ereditarietà da `Fish` a `Swimmer`.  
  
## Classi anonime  
 Progettazione classi supporta classi anonime.  *Tipi di classe anonima* sono classi dichiarate senza un identificatore.  Non possono avere un costruttore o un distruttore, non possono essere passate come argomenti alle funzioni e non possono essere restituiti come valori restituiti dalle funzioni.  È possibile utilizzare una classe anonima per sostituire un nome della classe con un nome typedef, come nell'esempio di seguito riportato:  
  
```  
typedef struct  
{  
    unsigned x;  
    unsigned y;  
} POINT;  
```  
  
 Le strutture possono essere anche anonime.  Progettazione classi visualizza le classi e le strutture anonime così come il rispettivo tipo.  Anche se è possibile dichiarare e visualizzare le classi e le strutture anonime, Progettazione di classi non utilizzerà il nome del tag specificato dal programmatore.  Verrà utilizzato il nome generato da Visualizzazione classi.  La classe o la struttura viene visualizzata in Visualizza classi e Progettazione classi come elemento denominato **\_\_unnamed**.  
  
 Per ulteriori informazioni sulle classi anonime, vedere [Tipi di classe anonimi](/visual-cpp/cpp/anonymous-class-types).  
  
## Classi modello  
 Progettazione classi supporta la visualizzazione di classi modello.  Le dichiarazioni annidate vengono supportate.  Nella tabella seguente vengono illustrate alcune dichiarazioni tipiche.  
  
|Elemento di codice|Visualizzazione di Progettazione classi|  
|------------------------|---------------------------------------------|  
|`template <class T>`<br /><br /> `class A {};`|`A<T>`<br /><br /> Classe modello|  
|`template <class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Classe modello|  
|`template <class T, int i>`<br /><br /> `class A {};`|`A<T, i>`<br /><br /> Classe modello|  
|`template <class T, template <class K> class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Classe modello|  
  
 Nella seguente tabella vengono illustrati alcuni esempi di specializzazione parziale.  
  
|Elemento di codice|Visualizzazione di Progettazione classi|  
|------------------------|---------------------------------------------|  
|`template<class T, class U>`<br /><br /> `class A {};`|`A<T, U>`<br /><br /> Classe modello|  
|`template<class T>`<br /><br /> `class A<T, T> {};`|`A<T, T>`<br /><br /> Classe modello|  
|`template <class T>`<br /><br /> `class A<T, int> {};`|`A<T, int>`<br /><br /> Classe modello|  
|`template <class T1, class T2>`<br /><br /> `class A<T1*, T2*> {};`|`A<T1*, T2*>`<br /><br /> Classe modello|  
  
 Nella seguente tabella vengono illustrati alcuni esempi di ereditarietà nella specializzazione parziale.  
  
|Elemento di codice|Visualizzazione di Progettazione classi|  
|------------------------|---------------------------------------------|  
|`template <class T, class U>`<br /><br /> `class A {};`<br /><br /> `template <class TC>`<br /><br /> `class A<T, int> {};`<br /><br /> `class B : A<int, float>`<br /><br /> `{};`<br /><br /> `class C : A<int, int>`<br /><br /> `{};`|`A<T, U>`<br /><br /> Classe modello<br /><br /> `B`<br /><br /> Classe<br /><br /> \(punta alla classe A\)<br /><br /> `C`<br /><br /> Classe<br /><br /> \(punta alla classe A\)|  
  
 Nella seguente tabella vengono illustrati alcuni esempi di funzioni del modello di specializzazione parziale.  
  
|Elemento di codice|Visualizzazione di Progettazione classi|  
|------------------------|---------------------------------------------|  
|`class A`<br /><br /> `{`<br /><br /> `template <class T, class U>`<br /><br /> `void func(T a, U b);`<br /><br /> `template <class T>`<br /><br /> `void func(T a, int b);`<br /><br /> `};`|`A`<br /><br /> funzione \< T, U \> \(\+ 1 overload\)|  
|`template <class T1>`<br /><br /> `class A {`<br /><br /> `template <class T2>`<br /><br /> `class B {};`<br /><br /> `};`<br /><br /> `template<> template<>`<br /><br /> `class A<type>::B<type> {};`|`A<T1>`<br /><br /> Classe modello<br /><br /> `B<T2>`<br /><br /> Classe modello<br /><br /> \(B è contenuto all'interno della classe A in **Tipi annidati**\)|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `class A : C<int> {};`|`A`<br /><br /> Classe<br /><br /> \-\>C\<int\><br /><br /> `C<T>`<br /><br /> Classe modello|  
  
 Nella seguente tabella vengono illustrati alcuni esempi dell'ereditarietà del modello.  
  
|Elemento di codice|Visualizzazione di Progettazione classi|  
|------------------------|---------------------------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {`<br /><br /> `class B {};`<br /><br /> `}`<br /><br /> `class A : C<int>::B {};`|`A`<br /><br /> Classe<br /><br /> \-\>B<br /><br /> `C<int>`<br /><br /> Classe<br /><br /> \(B è contenuto all'interno della classe C in **Tipi annidati**\)<br /><br /> `C<T>`<br /><br /> Classe modello|  
  
 Nella seguente tabella vengono illustrati alcuni esempi di tipica connessione di classe specializzata.  
  
|Elemento di codice|Visualizzazione di Progettazione classi|  
|------------------------|---------------------------------------------|  
|`template <class T>`<br /><br /> `class C {};`<br /><br /> `template<>`<br /><br /> `class C<int> {};`<br /><br /> `class A : C<int> {};`<br /><br /> `class D : C<float> {};`|`A`<br /><br /> Classe<br /><br /> \-\>C\<int\><br /><br /> `C<int>`<br /><br /> Classe<br /><br /> `C<T>`<br /><br /> Classe modello<br /><br /> `D`<br /><br /> Classe<br /><br /> \-\>C\<float\>|  
|`class B {`<br /><br /> `template <class T>`<br /><br /> `T min (const T &a, const T &b);`<br /><br /> `};`|`B`<br /><br /> min \<T\>|  
  
## Vedere anche  
 [Working with Visual C\+\+ Code \(Class Designer\)](../ide/working-with-visual-cpp-code-class-designer.md)   
 [Classi e struct](/visual-cpp/cpp/classes-and-structs-cpp)   
 [Tipi di classe anonimi](/visual-cpp/cpp/anonymous-class-types)   
 [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/it-it/3b74185e-2beb-4e29-8684-441e51d2a2ca)   
 [Più classi base](/visual-cpp/cpp/multiple-base-classes)   
 [Modelli](/visual-cpp/cpp/templates-cpp)