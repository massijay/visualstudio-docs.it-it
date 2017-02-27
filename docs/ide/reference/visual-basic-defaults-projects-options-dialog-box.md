---
title: "Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ToolsOptionsPages.Projects.VBDefaults"
helpviewer_keywords: 
  - "Istruzione Option Explicit, impostazione nell'IDE"
  - "Istruzione Option Compare, impostazione nell'IDE"
  - "Istruzione Option Strict, impostazione nell'IDE"
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Consente di specificare le impostazioni predefinite per le opzioni di un progetto Visual Basic.  Quando viene creato un nuovo progetto, alla relativa intestazione nell'editor di codice vengono aggiunte le istruzioni delle opzioni specificate.  Queste opzioni si applicano a tutti i progetti di Visual Basic.  
  
 Per visualizzare la finestra di dialogo, dal menu **Strumenti**, fare clic su **Opzioni**, espandere la cartella **Progetti e soluzioni** e fare clic su **Impostazioni predefinite di Visual Basic**.  
  
 **Option Explicit**  
 Imposta il valore predefinito per la compilazione in modo che sia obbligatoria la dichiarazione esplicita delle variabili.  Per impostazione predefinita, **Option Explicit** è impostato su **On**.  Per ulteriori informazioni, vedere [\/optionexplicit](/dotnet/visual-basic/reference/command-line-compiler/optionexplicit).  
  
 **Option Strict**  
 Imposta il valore predefinito per la compilazione in modo che siano obbligatorie conversioni esplicite verso un tipo di dati più piccolo e che non sia consentita l'associazione tardiva.  Per impostazione predefinita, **Option Strict** è impostato su **Off**.  Per ulteriori informazioni, vedere [\/optionstrict](/dotnet/visual-basic/reference/command-line-compiler/optionstrict).  
  
 **Option Compare**  
 Imposta il valore predefinito per la compilazione relativo ai confronti fra stringhe: binario \(con distinzione tra maiuscole e minuscole\) o basato sul testo \(senza distinzione tra maiuscole e minuscole\). Per impostazione predefinita, **Option Compare** è impostato su **Binary**.  Per ulteriori informazioni, vedere [\/optioncompare](/dotnet/visual-basic/reference/command-line-compiler/optioncompare).  
  
 **Option Infer**  
 Imposta il valore predefinito per la compilazione per inferenza di tipo locale.  Per impostazione predefinita, **Option Infer** è impostato su **On** per i nuovi progetti e su **Off** per i progetti dei quali è stata eseguita la migrazione da versioni precedenti di Visual Basic.  Per ulteriori informazioni, vedere [\/optioninfer](/dotnet/visual-basic/reference/command-line-compiler/optioninfer).  
  
## Vedere anche  
 [Soluzioni e progetti](../../ide/solutions-and-projects-in-visual-studio.md)