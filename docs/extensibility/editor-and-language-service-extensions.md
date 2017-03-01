---
title: Editor e della lingua Service estensioni | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK]
ms.assetid: 5653bac9-724f-4948-a820-68ce6aa96365
caps.latest.revision: 10
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
ms.openlocfilehash: 67d250a2806b367a76fa593026f10d4b671c21b2
ms.lasthandoff: 02/22/2017

---
# <a name="editor-and-language-service-extensions"></a>Editor e le estensioni del servizio di linguaggio
È possibile estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio. L'editor è basato su Windows Presentation Foundation (WPF) e viene scritto in codice gestito. Sebbene questa progettazione è diverso dalla progettazione nelle versioni precedenti di Visual Studio, fornisce la maggior parte delle stesse funzionalità. Per estendere l'editor, usare Managed Extensibility Framework (MEF).  
  
 Visual Studio SDK fornisce adapter noto come *shim* per supportare i package VS che sono stati scritti per le versioni precedenti. Tuttavia, se si dispone di un VSPackage esistente, è consigliabile aggiornarlo per la nuova tecnologia per ottenere migliorate prestazioni e affidabilità.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)|Introduzione all'utilizzo di modelli di elemento dell'Editor.|  
|[Estensione dell'Editor e servizi di linguaggio](../extensibility/extending-the-editor-and-language-services.md)|Collegamenti a documenti che presentano la progettazione e funzionalità dell'editor di componenti di base e viene illustrato come estendere.|  
|[Interfacce legacy nell'Editor](../extensibility/legacy-interfaces-in-the-editor.md)|Collegamenti a documenti che illustrano come accedere all'editor di componenti di base da codice esistente.|  
|[Creazione di finestre di progettazione ed editor personalizzati](../extensibility/creating-custom-editors-and-designers.md)|Collegamenti a documenti che illustrano come creare editor personalizzati.|  
|[Estensibilità del servizio di linguaggio legacy](../extensibility/internals/legacy-language-service-extensibility.md)|Collegamenti a documenti che illustrano come integrare i linguaggi di programmazione in Visual Studio.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Introduce Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Introduce Windows Presentation Foundation (WPF).|
