---
title: "Più DSL in un'unica soluzione | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: "3"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: b55d1d5ec8e84c8d16681ffd0ac738291e1bc39d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="multiple-dsls-in-one-solution"></a>Più soluzioni DSL in una soluzione unica
È possibile creare un pacchetto di diversi linguaggi specifici di dominio come parte di un'unica soluzione, in modo che vengano installati insieme.  
  
 Esistono varie tecniche per integrare più linguaggi specifici di dominio. Per ulteriori informazioni, vedere [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) e [procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md) e [personalizzazione copia comportamento](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Per compilare più di un linguaggio specifico di dominio nella stessa soluzione  
  
1.  Creare due o più soluzioni DSL e un progetto VSIX, quindi aggiungere tutti i progetti a un'unica soluzione.  
  
    -   Per creare un nuovo progetto VSIX: nel **nuovo progetto** finestra di dialogo Seleziona **Visual c#**, **estendibilità**, **progetto VSIX**.  
  
    -   Creare due o più soluzioni DSL nella directory della soluzione VSIX.  
  
         Per ogni linguaggio specifico di dominio, aprire una nuova istanza di Visual Studio. Creare il nuovo linguaggio specifico di dominio e specificare la stessa cartella soluzione della soluzione VSIX.  
  
         Assicurarsi di creare ogni linguaggio specifico di dominio con un'estensione di file diversa.  
  
    -   Modificare i nomi del **Dsl** e **DslPackage** progetti in modo che siano diversi. Ad esempio: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   In ogni **DslPackage\*\source.extension.tt**, aggiornare la riga per il nome del progetto Dsl corretto:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   Nella soluzione VSIX, aggiungere Dsl * e DslPackage\* progetti.  
  
         Può essere utile inserire ogni coppia in una specifica cartella soluzione.  
  
2.  Combinare i manifesti VSIX dei linguaggi specifici di dominio:  
  
    1.  Aprire *YourVsixProject***\source.extension.manifest**.  
  
    2.  Per ogni DSL, scegliere **aggiungere contenuto** e aggiungere:  
  
        -   `Dsl*`il progetto come un **componente MEF**  
  
        -   `DslPackage*`il progetto come un **componente MEF**  
  
        -   `DslPackage*`il progetto come un **Package VS**  
  
3.  Compilare la soluzione.  
  
 Il progetto VSIX risultante installerà entrambi i linguaggi specifici di dominio. È possibile eseguirne il test usando F5 o distribuire *YourVsixProject***\bin\Debug\\\*VSIX**.  
  
## <a name="see-also"></a>Vedere anche  
 [Integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Procedura: aggiungere un gestore di trascinamento e rilascio](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)