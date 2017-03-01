---
title: Progetti | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solutions [Visual Studio]
- custom tools [Visual Studio SDK]
- project subtypes [Visual Studio SDK]
- projects [Visual Studio SDK]
- project types [Visual Studio SDK]
ms.assetid: 237742e4-a638-4d5b-a9b3-6a69d627763c
caps.latest.revision: 43
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 842bef303d7a3211b8711920ef6cec357a876f8a
ms.lasthandoff: 02/22/2017

---
# <a name="projects"></a>Progetti
In Visual Studio, i progetti sono contenitori utilizzati dagli sviluppatori per organizzare i file di codice sorgente e altre risorse che vengono visualizzati in **Esplora**. In genere, i progetti sono file (ad esempio, un file con estensione csproj per un progetto c#) che archiviano i riferimenti ai file di codice sorgente e a risorse come file bitmap. Progetti consentono di organizzare, compilare, eseguire il debug e distribuire il codice sorgente, i riferimenti a servizi Web e database e altre risorse. Package VS possibile estendere il sistema di progetto di Visual Studio in tre modi principali: *i tipi di progetto*, *progetto sottotipi*, e *strumenti personalizzati*.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Tipi di progetto](../../extensibility/internals/project-types.md)  
 *Tipi di progetto* aggiungere il supporto per nuovi tipi di progetti, ad esempio linguaggi di programmazione. Ad esempio, ogni linguaggio che supporta Visual Studio ha un proprio tipo di progetto e l'esempio di integrazione di IronPython include un tipo di progetto per il linguaggio IronPython. È necessario creare un tipo di progetto per linguaggi diversi da c# o Visual Basic per personalizzare come elementi sono compilati, debug, distribuiti e visualizzati **Esplora**. Per ulteriori informazioni, vedere [tipi di progetto](../../extensibility/internals/project-types.md).  
  
 [Progetto (sottotipi)](../../extensibility/internals/project-subtypes.md)  
 *Progetto sottotipi* sono basati sui tipi di progetto e può essere utilizzato per personalizzare la modalità di progetti vengono compilati, il debug e distribuiti. Visual Studio utilizza sottotipi di progetto con progetti Smart Device. la personalizzazione di distribuzione tramite la copia di un programma appena compilato da un computer di sviluppo al dispositivo di destinazione. Tipi di progetto Visual Basic e c# possono essere utilizzati come base per i sottotipi di progetto; Tipi di progetto C++ non è possibile. I tipi di progetto è utilizzabile anche come base per i sottotipi di progetto. Per ulteriori informazioni, vedere [sottotipi progetto](../../extensibility/internals/project-subtypes.md).  
  
 [Progetti Web](../../extensibility/internals/web-projects.md)  
 Viene illustrato il progetto Web, che a sua volta di creare applicazioni Web.  
  
 [Nuova generazione progetto: Dietro le quinte, parte&1;](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) e [nuova generazione progetto: dietro le quinte, parte&2;](../../extensibility/internals/new-project-generation-under-the-hood-part-two.md)  
 Viene illustrato ciò che effettivamente si verifica quando si crea un nuovo progetto.  
  
 [Esempi di VSSDK](../../misc/vssdk-samples.md)  
 Descrive gli esempi VSSDK che si occupano di progetti e soluzioni.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [All'interno di Visual Studio SDK](../../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Illustrano vari aspetti di extensibility di Visual Studio.
