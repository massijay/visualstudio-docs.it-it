---
title: "CA1704: Gli identificatori devono essere digitati correttamente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 25
---
# CA1704: Gli identificatori devono essere digitati correttamente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|Categoria|Microsoft.Naming|  
|Breaking Change|Breaking|  
  
## Causa  
 Il nome di un identificatore contiene una o più parole che non sono riconosciute dalla libreria del correttore ortografico Microsoft.  Questa regola non controlla costruttori o membri con denominazione specifica come le funzioni di accesso alle proprietà Get e Set.  
  
## Descrizione della regola  
 Questa regola analizza l'identificatore per token e controlla l'ortografia di ogni token.  L'algoritmo di analisi esegue le seguenti trasformazioni:  
  
-   Le lettere maiuscole iniziano un nuovo token.  Ad esempio, MyNameIsJoe viene scomposto nei token "My", "Name", "Is" e "Joe".  
  
-   Per più lettere maiuscole, l'ultima lettera maiuscola inizia un nuovo token.  Ad esempio, GUIEditor viene scomposto nei token "GUI" e "Editor".  
  
-   Gli apostrofi iniziali e finali vengono rimossi.  Ad esempio, 'sender' viene scomposto nel token "sender".  
  
-   I caratteri di sottolineatura vengono considerati fine del token e rimossi.  Ad esempio, Hello\_world viene scomposto nei token "Hello" e "world".  
  
-   La e commerciale incorporata viene rimossa.  Ad esempio, for&mat viene scomposto nel token "format".  
  
 Per impostazione predefinita, viene utilizzata la versione in lingua inglese \(en\) del correttore ortografico.  Non sono attualmente disponibili altri dizionari.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, correggere l'ortografia della parola o aggiungere la parola a un dizionario personalizzato denominato CustomDictionary.xml.  Inserire il dizionario nella directory di installazione dello strumento, nella directory del progetto o nella directory associata allo strumento nel profilo utente \(%USERPROFILE%\\Dati applicazioni\\...\).  Per informazioni su come aggiungere il dizionario personalizzato a un progetto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)  
  
-   Aggiungere le parole che non devono causare una violazione nel percorso Dictionary\/Words\/Recognized.  
  
-   Aggiungere le parole che devono causare una violazione nel percorso Dictionary\/Words\/Unrecognized.  
  
-   Aggiungere le parole che devono essere contrassegnate come obsolete nel percorso Dictionary\/Words\/Deprecated.  Per ulteriori informazioni, vedere l'argomento relativo alla regola correlata [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md).  
  
-   Aggiungere le eccezioni alle regole relative alla distinzione tra maiuscole e minuscole degli acronimi nel percorso Dictionary\/Acronyms\/CasingExceptions.  
  
 Di seguito è fornito un esempio della struttura di un file del dizionario personalizzato.  
  
```  
<Dictionary>  
   <Words>  
      <Unrecognized>  
         <Word>cb</Word>  
      </Unrecognized>  
      <Recognized>  
         <Word>stylesheet</Word>  
         <Word>GotDotNet</Word>  
      </Recognized>  
      <Deprecated>  
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>  
      </Deprecated>  
   </Words>  
   <Acronyms>  
      <CasingExceptions>  
         <Acronym>CJK</Acronym>  
         <Acronym>Pi</Acronym>  
      </CasingExceptions>  
   </Acronyms>  
</Dictionary>  
```  
  
## Esclusione di avvisi  
 Escludere un avviso dalla regola solo se l'ortografia della parola è intenzionalmente errata e se la parola si applica a un insieme limitato della libreria.  L'utilizzo di una corretta ortografia consente di ridurre la curva di apprendimento richiesta per le nuove librerie software.  
  
## Regole correlate  
 [CA2204: I valori letterali devono essere digitati in modo corretto](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703: Le stringhe di risorsa devono essere digitate correttamente](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709: Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708: Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707: Gli identificatori non devono contenere caratteri di sottolineatura](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726: Utilizzare termini preferiti](../code-quality/ca1726-use-preferred-terms.md)  
  
## Vedere anche  
 [Procedura: Personalizzare il dizionario di analisi del codice](../code-quality/how-to-customize-the-code-analysis-dictionary.md)