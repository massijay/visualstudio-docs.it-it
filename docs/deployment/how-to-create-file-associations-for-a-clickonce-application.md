---
title: 'Procedura: creare associazioni di File per un''applicazione ClickOnce | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- file associations, ClickOnce applications
- ClickOnce deployment, file associations
ms.assetid: 835230c8-3177-440f-85e3-e40f1d8b4f9d
caps.latest.revision: "7"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 491de73e97bf44ea54d5ccdfb604924ff26c9530
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-create-file-associations-for-a-clickonce-application"></a>Procedura: creare associazioni di file per un'applicazione ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]le applicazioni possono essere associate a uno o più estensioni di file, in modo che l'applicazione verrà avviato automaticamente quando l'utente apre un file di tali tipi. Aggiunta di supporto delle estensioni di file a un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione è semplice.  
  
### <a name="to-create-file-associations-for-a-clickonce-application"></a>Per creare associazioni di file per un'applicazione ClickOnce  
  
1.  Creare un [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione in genere, o utilizzarne un'esistente [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione.  
  
2.  Aprire il manifesto dell'applicazione con un editor di testo o XML, ad esempio Blocco note.  
  
3.  Trovare l'elemento `assembly`. Per altre informazioni, vedere [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md).  
  
4.  Come elemento figlio di `assembly` elemento, aggiungere un `fileAssociation` elemento. Il `fileAssociation` elemento dispone di quattro attributi:  
  
    -   `extension`: L'estensione di file che si desidera associare all'applicazione.  
  
    -   `description`: Descrizione del tipo di file, verrà visualizzata nella shell di Windows.  
  
    -   `progid`: Stringa che identifica il tipo di file, per contrassegnare quest'ultimo nel Registro di sistema.  
  
    -   `defaultIcon`: Un'icona da utilizzare per questo tipo di file. L'icona deve essere aggiunto come una risorsa del file nel manifesto dell'applicazione. Per altre informazioni, vedere [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
     Per un esempio di `file` e `fileAssociation` elementi, vedere [ \<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md).  
  
5.  Se si desidera associare più di un tipo di file all'applicazione, aggiungere ulteriori `fileAssociation` elementi. Si noti che il `progid` attributo deve essere diverso per ognuno.  
  
6.  Dopo aver completato con il manifesto dell'applicazione, è necessario firmare nuovamente il manifesto. È possibile farlo dalla riga di comando utilizzando Mage.exe.  
  
     `mage -Sign WindowsFormsApp1.exe.manifest -CertFile mycert.pfx`  
  
     Per ulteriori informazioni, vedere [Mage.exe (generazione manifesto e lo strumento di modifica)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)  
  
## <a name="see-also"></a>Vedere anche  
 [\<fileAssociation > elemento](../deployment/fileassociation-element-clickonce-application.md)   
 [Manifesto dell'applicazione ClickOnce](../deployment/clickonce-application-manifest.md)   
 [Mage.exe (Strumento per la generazione e la modifica di manifesti)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)