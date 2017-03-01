---
title: Supporto per siti Web | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- web site projects
ms.assetid: ce9f4266-bb64-4c09-be88-4bd6413f60d0
caps.latest.revision: 17
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 636cbee868bb53be2d0ef85bd309459570eb84c0
ms.lasthandoff: 02/22/2017

---
# <a name="web-site-support"></a>Sito Web di supporto
Un sistema di progetto del sito Web è un sistema di progetto che consente di creare progetti Web. Progetti Web, a sua volta creano applicazioni Web. Un progetto di sito Web genera un file eseguibile per ogni pagina Web che dispone di codice associato. File eseguibile aggiuntivi vengono generati dal file di codice sorgente nella cartella /App_Code.  
  
 Sistemi di progetto di sito Web vengono creati tramite l'aggiunta di modelli e gli attributi di registrazione di un sistema di progetto esistente. Uno di questi attributi seleziona il provider di IntelliSense per la lingua. L'implementazione del provider IntelliSense gestisce riferimenti e il compilatore di linguaggio viene chiamato quando viene richiesta una pagina Web smart non memorizzato nella cache.  
  
 Il compilatore di linguaggio utilizzato per compilare pagine Web deve essere registrato con [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)]. È possibile utilizzare il [ \<compilatore > elemento](http://msdn.microsoft.com/Library/7a151659-b803-4c27-b5ce-1c4aa0d5a823) in un file Web. config per registrare il compilatore, come nell'esempio seguente:  
  
```  
<system.codedom>  <compilers>    <compiler language="py;IronPython" extension=".py"       type="IronPython.CodeDom.PythonProvider, IronPython,       Version=1.0.2391.18146, Culture=neutral,       PublicKeyToken=b03f5f7f11d50a3a" />  </compilers></system.codedom>  
```  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Modelli di sito Web supporto tecnico](../../extensibility/internals/web-site-support-templates.md)  
 Vengono elencati i modelli che è possibile utilizzare per creare nuovi progetti di sito Web e gli elementi associati.  
  
 [Attributi di supporto del sito Web](../../extensibility/internals/web-site-support-attributes.md)  
 Visualizza gli attributi di registrazione che si connettono a un progetto sito Web [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e [!INCLUDE[vstecasp](../../code-quality/includes/vstecasp_md.md)].  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Progetti Web](../../extensibility/internals/web-projects.md)  
 Viene presentata una panoramica dei due tipi di progetti Web, progetti di siti Web e progetti di applicazione Web.
