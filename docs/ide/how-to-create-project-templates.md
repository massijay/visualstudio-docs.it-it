---
title: 'Procedura: Creare modelli di progetto | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ExportTemplateWizard
helpviewer_keywords:
- Visual Studio templates, creating project templates
- project templates, metadata files
- Visual Studio templates, project templates
- project templates, custom template locations
- project templates, creating
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 279a123088308a54dccfa9abe0bfbcdb18e5aaf1
ms.contentlocale: it-it
ms.lasthandoff: 05/31/2017

---
# <a name="how-to-create-project-templates"></a>Procedura: creare modelli di progetto
Questa procedura consente di creare un modello tramite l'**Esportazione guidata modelli**, che crea il pacchetto del modello in un file con estensione zip. Per una distribuzione più efficiente, è anche possibile creare modelli in formato VSIX tramite l'estensione Esportazione guidata modelli o con i modelli inclusi in [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]. In alternativa è possibile creare modelli manualmente.  
  
### <a name="to-create-a-custom-project-template-with-the-standard-export-template-wizard"></a>Per creare un modello di progetto personalizzato con l'Esportazione guidata modelli standard  
  
1.  Creare un progetto.  
  
    > [!NOTE]
    >  Quando si assegna il nome a un progetto che fungerà da origine per un modello, usare solo caratteri di identificatore validi. Un modello esportato da un progetto con nome contenente caratteri non validi può causare errori di compilazione nei progetti futuri basati sul modello. Per altre informazioni sui caratteri di identificatore valido, vedere [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names) (Nomi di elementi dichiarati).  
  
2.  Modificare il progetto finché non è pronto per l'esportazione come modello.  
  
3.  Modificare in base alle esigenze i file del codice per indicare dove deve essere applicata la sostituzione dei parametri. Per altre informazioni sulla sostituzione dei parametri, vedere [Procedura: Sostituire i parametri di un modello](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Nel menu **Progetto** scegliere**Esporta modello**. Verrà aperta l'**Esportazione guidata modelli**.  
  
5.  Fare clic su **Modello di progetto**.  
  
6.  Se la soluzione corrente contiene più progetti, selezionare i progetti da esportare in un modello.  
  
7.  Scegliere **Avanti**.  
  
8.  Selezionare un'icona e un'immagine di anteprima per il modello. Queste verranno visualizzate nella finestra di dialogo **Nuovo progetto**.  
  
9. Immettere un nome e una descrizione per il modello.  
  
10. Scegliere **Fine**. Il progetto verrà esportato in un file con estensione zip, inserito nel percorso di output specificato e, se questa azione è stata selezionata, importato in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     Se [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] è installato, è possibile eseguire il wrapping del modello finito in un file con estensione vsix per la distribuzione tramite il modello **Progetto VSIX**. Per altre informazioni, vedere [Introduzione al modello di progetto VSIX](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)   
 [Procedura: Creare modelli di elementi](../ide/how-to-create-item-templates.md)

