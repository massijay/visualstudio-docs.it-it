---
title: Cenni preliminari sul modello di automazione | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
caps.latest.revision: 12
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
ms.openlocfilehash: ce59c002accd55b9179cacc60cf944ff72138c7e
ms.lasthandoff: 02/22/2017

---
# <a name="automation-model-overview"></a>Cenni preliminari sul modello di automazione
Il modello di automazione è costituito da un set di oggetti su cui è possibile scrivere un componente aggiuntivo di Visual Studio o estensione. Un componente aggiuntivo è un'applicazione che è possibile modificare l'ambiente di Visual Studio e automatizzare le attività comuni. Un'estensione di Visual Studio è possibile creare componenti personalizzati di Visual Studio o aggiungere la funzionalità dei componenti standard, ad esempio l'editor di testo.  
  
## <a name="objects-in-the-automation-model"></a>Oggetti del modello di automazione  
 Il modello di automazione è costituito da gruppi di oggetti che controllano i principali aspetti dell'ambiente comune correlati. Di seguito è riportato un diagramma che mostra il set completo di oggetti che compongono il modello di automazione.  
  
 ![Grafico di oggetti di automazione di Visual Studio](~/extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")  
Oggetti di automazione di Visual Studio  
  
 Per ulteriori informazioni, vedere [estensione dell'ambiente Visual Studio](http://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792).  
  
 L'ambiente fornisce un modello per aree funzionali diverse. È ad esempio, un modello di codice per diversi elementi che si possono verificare nel codice. È disponibile un modello di documento per vari elementi del documento. Un'area, l'area di progetto, è di particolare interesse per i provider di VSPackage. Potrebbe essere utile di nuovi tipi di progetto per contribuire al modello di automazione in modo analogo a come [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] contribuiscono al modello di automazione. Che processo è descritto in [fornendo automazione per i package VS](../../extensibility/internals/providing-automation-for-vspackages.md).  
  
 Posizioni in cui è possibile estendere il modello di automazione dell'ambiente:  
  
-   Progetto  
  
-   Documento  
  
-   Codice  
  
-   Compilazione  
  
 Per ulteriori informazioni sull'automazione, vedere [automazione ed Extensibility in Visual Studio](http://msdn.microsoft.com/Library/f71a2253-3e68-4e5e-9a18-edbba816caf6). In questo documento e i documenti vengono forniti collegamenti per prendere decisioni relative a come è necessario fornire l'automazione per il pacchetto Visual Studio.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: creare un componente aggiuntivo](http://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
