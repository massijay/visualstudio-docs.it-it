---
title: Manifesti dell'applicazione e distribuzione nelle soluzioni Office | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- manifests [Office development in Visual Studio]
- deployment manifests [Office development in Visual Studio]
- application manifests [Office development in Visual Studio]
- assemblies [Office development in Visual Studio], updating
ms.assetid: 4e9abc7c-ef9f-4cb2-a7a9-c95c5f4a1fb7
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 822be7f0e6e79f600331197c60ed48ea84cde200
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="application-and-deployment-manifests-in-office-solutions"></a>Manifesti dell'applicazione e di distribuzione nelle soluzioni Office
  Un manifesto dell'applicazione è un file XML che fornisce informazioni usate da una soluzione Office per individuare e aggiornare i relativi assembly. Un manifesto dell'applicazione può essere usato con un manifesto di distribuzione, costituito da un file XML archiviato nel server, che fornisce le informazioni necessarie per individuare la versione più recente del manifesto dell'applicazione e degli assembly.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="manifest-structure-for-office-solutions"></a>Struttura del manifesto per le soluzioni Office  
 Per le soluzioni Microsoft Office create tramite gli strumenti di sviluppo di Office in Visual Studio, tutti i manifesti sono basati sullo schema ClickOnce standard. Quando si distribuiscono le soluzioni Office, i manifesti dell'applicazione per i progetti di componente aggiuntivo VSTO e a livello di documento si trovano nella cache di ClickOnce. I manifesti di distribuzione non vengono copiati nel computer client.  
  
 Per informazioni sui contenuti dei manifesti dell'applicazione e di distribuzione per progetti di Office, vedere [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md) e [Deployment Manifests for Office Solutions](../vsto/deployment-manifests-for-office-solutions.md).  
  
## <a name="creating-application-and-deployment-manifests"></a>Creazione di manifesti di applicazione e di distribuzione  
 I manifesti dell'applicazione vengono creati automaticamente come parte del processo di compilazione. Ogni volta che si compila un progetto a livello di documento, il percorso del manifesto di distribuzione è incorporato nel documento come proprietà personalizzata del documento. Per i componenti aggiuntivi VSTO, il percorso del manifesto della distribuzione è archiviato nel registro di sistema.  
  
 Per ulteriori informazioni sul **pubblicazione guidata**, vedere [distribuisce una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md).  
  
 Per altre informazioni su come dei manifesti con soluzioni di Office, vedere [distribuisce una soluzione Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Architettura delle personalizzazioni a livello di documento](../vsto/architecture-of-document-level-customizations.md)   
 [Architettura dei componenti aggiuntivi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Application Manifests for Office Solutions](../vsto/application-manifests-for-office-solutions.md)   
 [Manifesti di distribuzione per le soluzioni Office](../vsto/deployment-manifests-for-office-solutions.md)   
 [Manifesto dell'applicazione ClickOnce](/visualstudio/deployment/clickonce-application-manifest)   
 [Manifesto di distribuzione ClickOnce](/visualstudio/deployment/clickonce-deployment-manifest)  
  
  