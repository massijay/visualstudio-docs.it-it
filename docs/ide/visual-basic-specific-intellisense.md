---
title: "Funzionalit&#224; di IntelliSense specifiche per Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IntelliSense [Visual Basic]"
  - "IntelliSense [Visual Studio], Visual Basic"
ms.assetid: 4dec8753-05e5-4f74-b304-5f8c4ed8723b
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Funzionalit&#224; di IntelliSense specifiche per Visual Basic
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor del codice sorgente di Visual Basic offre le seguenti funzionalità di IntelliSense:  
  
-   Suggerimenti per la sintassi  
  
     I suggerimenti per la sintassi visualizzano la sintassi dell'istruzione che si sta digitando.  Ciò risulta particolarmente utile per istruzioni quali [Declare](/dotnet/visual-basic/language-reference/statements/declare-statement).  
  
## Completamento automatico  
  
-   Completamento di diverse parole chiave  
  
     Se ad esempio si digita `goto` seguito da uno spazio, IntelliSense visualizzerà un elenco delle etichette definite in un menu a discesa.  Altre parole chiave supportate comprendono `Exit`, `Implements`, `Option` e `Declare`.  
  
-   Completamento di `Enum` e `Boolean`  
  
     Quando un'istruzione fa riferimento a un membro di un'enumerazione, IntelliSense visualizza un elenco dei membri di `Enum`.  Quando un'istruzione si riferisce a `Boolean`, IntelliSense visualizza un menu a discesa contenente le opzioni True e False.  
  
 Il completamento può essere disattivato in base all'impostazione predefinita deselezionando la casella di controllo **Elenco membri automatico** nella pagina **Generale** relativa alla cartella **Visual Basic**.  
  
 È possibile richiamare manualmente il completamento richiamando Elenca membri, Completa parola o ALT\+freccia DESTRA.  Per ulteriori informazioni, vedere [Utilizzo di IntelliSense](../ide/using-intellisense.md).  
  
## IntelliSense sensibile all'area  
 La funzionalità IntelliSense sensibile all'area assiste gli sviluppatori Visual Basic che devono distribuire applicazioni tramite [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e sono vincolati da impostazioni di attendibilità parziale.  Questa funzionalità:  
  
-   Consente di scegliere le autorizzazioni con cui verrà eseguita l'applicazione.  
  
-   Visualizza le API nell'area selezionata come disponibili in Elenca membri, mentre le API che richiedono autorizzazioni aggiuntive vengono visualizzate come non disponibili.  
  
 Per ulteriori informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../deployment/code-access-security-for-clickonce-applications.md).  
  
## Vedere anche  
 [Utilizzo di IntelliSense](../ide/using-intellisense.md)