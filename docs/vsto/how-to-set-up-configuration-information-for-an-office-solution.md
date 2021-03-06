---
title: 'Procedura: impostare le informazioni di configurazione per una soluzione Office | Documenti Microsoft'
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
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: "33"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8c2e0a904ad3cdbef3e70072d263cc26274de52
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Procedura: definire le informazioni di configurazione per una soluzione Office
  È possibile utilizzare i file di configurazione per configurare le impostazioni specifiche per le soluzioni Office. È possibile specificare impostazioni quali criteri di associazione degli assembly, oggetti remoti, debug e le impostazioni di traccia.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-configuration-file-to-your-office-project"></a>Per aggiungere un file di configurazione al progetto di Office  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
2.  Nel **categorie** riquadro, fare clic su **generale**.  
  
3.  Nel **modelli** riquadro, selezionare **File di configurazione applicazione**.  
  
4.  Nel **nome** digitare lo stesso nome dell'assembly con estensione config. Ad esempio, un file di configurazione per un assembly di progetto di Excel denominato ExcelWorkbook1.dll verrebbe denominato Excelworkbook1.  
  
5.  Fare clic su **Aggiungi**.  
  
6.  Creare il file di configurazione in base allo schema di file di configurazione dell'applicazione. Per ulteriori informazioni, vedere [Schema di File di configurazione per .NET Framework](/dotnet/framework/configure-apps/file-schema/index).  
  
 Non esistono considerazioni speciali per l'utilizzo di file di configurazione con i progetti di Office.  
  
## <a name="see-also"></a>Vedere anche  
 [Schema di File di configurazione per .NET Framework](/dotnet/framework/configure-apps/file-schema/index)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  