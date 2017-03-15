---
title: Comando, gruppo e il posizionamento della barra degli strumenti predefinite | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- commands [Visual Studio], default groups
- toolbars [Visual Studio], default
- commands [Visual Studio], default editor
- command groups
- commands [Visual Studio], default IDE
- commands [Visual Studio], default product
ms.assetid: 35342110-d639-4577-8367-00b21dcc6f07
caps.latest.revision: 30
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
ms.openlocfilehash: 1d418eea04791d85dd0e8d08fba23abe8dc7e054
ms.lasthandoff: 02/22/2017

---
# <a name="default-command-group-and-toolbar-placement"></a>Comando predefinito, gruppo e il posizionamento della barra degli strumenti
Per prodotto uniformità e stabilità, l'interfaccia utente consente di visualizzare determinati gruppi di comando per impostazione predefinita, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono fornite le definizioni per i comandi e i gruppi di comando. Package VS è inoltre possibile utilizzare i comandi standard e i gruppi di comandi.  
  
 I gruppi di comandi predefiniti possono essere suddivise in tre categorie: IDE comandi, i comandi di prodotto e i comandi dell'editor.  
  
## <a name="default-ide-commands"></a>Comandi IDE predefiniti  
 Barra degli strumenti IDE predefinita include comandi condivisi da tutti i prodotti contenuti in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Sono inclusi i comandi relativi alle operazioni del progetto generico, ad esempio il **salvare** comando e **Aggiungi elemento** comando. Package VS da non aggiungere o sottrarre questa barra degli strumenti, con un'unica eccezione: se il prodotto o VSPackage aggiunge una nuova finestra degli strumenti, quindi la finestra deve essere aggiunto all'elenco di finestre degli strumenti disponibili nel **visualizzazione** menu. Nuovi prodotti o i package VS può aggiungere i propri sulla barra degli strumenti.  
  
## <a name="default-product-commands"></a>Comandi di prodotto predefiniti  
 Ogni prodotto può fornire l'IDE con una propria barra degli strumenti predefinita che contiene importanti e comandi utilizzati di frequente. È consigliabile, tuttavia, per utilizzare i menu e barre degli strumenti ogni volta che è possibile esistenti e integrare con altre barre degli strumenti attività specifiche in base alle esigenze.  
  
 Il campo priorità per una barra degli strumenti determina la posizione di riga. Zero priorità posiziona la barra degli strumenti nella terza riga (riga 3), sotto la barra dei menu (riga 1) e **Standard** barra degli strumenti (riga 2). Pertanto, altre barre degli strumenti vengono visualizzati nella riga (priorità + 3). Barre degli strumenti successive vengono posizionate nella stessa riga, se c'è spazio; in caso contrario, queste vengono spostate automaticamente la riga successiva.  
  
## <a name="default-editor-commands"></a>Comandi dell'Editor predefinito  
 Un package VS che fornisce un editor personalizzato deve fornire una barra degli strumenti predefinita che contiene i più importanti e comandi utilizzati di frequente in tale editor. Barra degli strumenti editor verrà visualizzato quando l'editor è attivo e deve essere nascosto quando l'editor non è attivo. La visibilità viene controllata nel `VisibilityConstraints Element` del file vsct.  
  
 Barre degli strumenti Editor deve essere posizionati di sotto di barre degli strumenti IDE e prodotto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gruppi, menu e comandi definiti dall'IDE](../../extensibility/internals/ide-defined-commands-menus-and-groups.md)   
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
