---
title: 'Procedura: Escludere progetti da una compilazione | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
caps.latest.revision: 6
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
ms.sourcegitcommit: 47057e9611b824c17077b9127f8d2f8b192d6eb8
ms.openlocfilehash: ab5283e92c8ab4bee74f9d6e3c7ae66e67b7a1e8
ms.contentlocale: it-it
ms.lasthandoff: 05/13/2017

---
# <a name="how-to-exclude-projects-from-a-build"></a>Procedura: escludere progetti da una compilazione
È possibile compilare una soluzione senza compilare tutti i progetti contenuti al suo interno. Ad esempio, si può escludere un progetto che causa l'interruzione della compilazione. Sarà possibile compilare il progetto in seguito, dopo avere esaminato e risolto i problemi.  
  
 Per escludere un progetto è possibile procedere in due modi:  
  
-   Rimuoverlo temporaneamente dalla configurazione della soluzione attiva.  
  
-   Creare una configurazione di soluzione che non includa il progetto.  
  
 Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../ide/understanding-build-configurations.md).  
  
### <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>Per rimuovere temporaneamente un progetto dalla configurazione della soluzione attiva.  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Gestione configurazione**.  
  
2.  Nella tabella **Contesti progetto** individuare il progetto da escludere dalla compilazione.  
  
3.  Nella colonna **Compilazione** del progetto deselezionare la casella di controllo.  
  
4.  Scegliere il pulsante **Chiudi** e quindi ricompilare la soluzione.  
  
### <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>Per creare una configurazione di soluzione che esclude un progetto  
  
1.  Nella barra dei menu scegliere **Compilazione**, **Gestione configurazione**.  
  
2.  Nell'elenco **Configurazione soluzione attiva** **scegliere \<Nuova**.  
  
3.  Nella casella **Nome** immettere un nome per la configurazione della soluzione.  
  
4.  Nell'elenco **Copia impostazioni da** scegliere la configurazione di soluzione su cui si vuole basare la nuova configurazione (ad esempio **Debug**) e quindi scegliere il pulsante **OK**.  
  
5.  Nella finestra di dialogo **Configuration Manager** deselezionare la casella di controllo **Compilazione** per il progetto da escludere e quindi scegliere il pulsante **Chiudi**.  
  
6.  Sulla barra degli strumenti **Standard** verificare che la nuova configurazione della soluzione compaia come configurazione attiva nella casella **Configurazioni soluzione**.  
  
7.  Sulla barra dei menu scegliere **Compila**, **Ricompila soluzione**.  
  
## <a name="see-also"></a>Vedere anche  
 [Understanding Build Configurations](../ide/understanding-build-configurations.md)  (Informazioni sulle configurazioni delle compilazioni)  
 [Procedura: Creare e modificare le configurazioni](../ide/how-to-create-and-edit-configurations.md)   
 [Procedura: Compilare più configurazioni contemporaneamente](../ide/how-to-build-multiple-configurations-simultaneously.md)
