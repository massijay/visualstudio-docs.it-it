---
title: "Pi&#249; soluzioni DSL in una soluzione unica | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Pi&#249; soluzioni DSL in una soluzione unica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile creare un pacchetto di diversi linguaggi specifici di dominio come parte di un'unica soluzione, in modo che vengano installati insieme.  
  
 Esistono varie tecniche per integrare più linguaggi specifici di dominio.  Per altre informazioni, vedere [L'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md), [Procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md) e [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).  
  
### Per compilare più di un linguaggio specifico di dominio nella stessa soluzione  
  
1.  Creare due o più soluzioni DSL e un progetto VSIX, quindi aggiungere tutti i progetti a un'unica soluzione.  
  
    -   Per creare un nuovo progetto VSIX: nella finestra di dialogo **Nuovo progetto** selezionare **Visual C\#**, **Extensibility**, **Progetto VSIX**.  
  
    -   Creare due o più soluzioni DSL nella directory della soluzione VSIX.  
  
         Per ogni linguaggio specifico di dominio, aprire una nuova istanza di Visual Studio.  Creare il nuovo linguaggio specifico di dominio e specificare la stessa cartella soluzione della soluzione VSIX.  
  
         Assicurarsi di creare ogni linguaggio specifico di dominio con un'estensione di file diversa.  
  
    -   Modificare i nomi dei pacchetti **Dsl** e **DslPackage** in modo che siano tutti diversi.  Ad esempio, `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   In ogni **DslPackage\*\\source.extension.tt**, aggiornare questa riga con il nome del progetto Dsl corretto:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   Nella soluzione VSIX aggiungere i progetti Dsl\* e DslPackage\*.  
  
         Può essere utile inserire ogni coppia in una specifica cartella soluzione.  
  
2.  Combinare i manifesti VSIX dei linguaggi specifici di dominio:  
  
    1.  Aprire *ProgettoVsix***\\source.extension.manifest**.  
  
    2.  Per ogni linguaggio specifico di dominio, scegliere **Aggiungi contenuto** e aggiungere:  
  
        -   Il progetto `Dsl*` come **componente MEF**  
  
        -   Il progetto `DslPackage*` come **componente MEF**  
  
        -   Il progetto `DslPackage*` come **pacchetto VS**  
  
3.  Compilare la soluzione.  
  
 Il progetto VSIX risultante installerà entrambi i linguaggi specifici di dominio.  È possibile testarli usando F5 oppure distribuire *ProgettoVsix***\\bin\\Debug\\\*.vsix**.  
  
## Vedere anche  
 [L'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md)