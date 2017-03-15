---
title: "Procedura: configurare l&#39;analisi del codice per un&#39;applicazione Web ASP.NET | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.propertypages.asp"
ms.assetid: b3000b31-fd9d-489e-81a2-a4bee49453ba
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedura: configurare l&#39;analisi del codice per un&#39;applicazione Web ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] e [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] è possibile scegliere da un elenco di *set di regole* di analisi codice da applicare all'applicazione Web [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  Il set di regole predefinito è il set Regole minime consigliate Microsoft.  È possibile selezionare un altro set di regole da applicare al sito Web.  
  
### Per configurare un set di regole per un progetto del framework di pagine ASP.NET  
  
1.  Selezionare il sito Web in **Esplora soluzioni**.  
  
2.  Scegliere **Configura analisi codice per il sito Web** dal menu **Analizza** .  
  
3.  Se è stata selezionata la soluzione e questa dispone di più di un progetto, selezionare la configurazione di compilazione e il sistema operativo di destinazione dagli elenchi **Configurazione** e **Piattaforma**.  
  
4.  Per ogni progetto nella soluzione fare clic sulla colonna **Set di regole**, quindi fare clic sul nome del set di regole da eseguire.  
  
5.  Per impostazione predefinita, l'analisi codice viene eseguita su tutti i progetti nella soluzione.  Per disabilitare o abilitare l'analisi codice per un particolare progetto, attenersi alla seguente procedura:  
  
    1.  Fare clic con il pulsante destro del mouse sul nome del progetto, quindi scegliere Proprietà.  
  
    2.  Selezionare o deselezionare la casella di controllo **Abilita analisi codice**.  È inoltre possibile eseguire manualmente l'analisi codice selezionando **Esegui analisi del codice su sito Web** dal menu **Analizza**.  
  
6.  Nell'elenco a discesa **Esegui il set di regole**, attenersi alla seguente procedura:  
  
    -   Selezionare il set di regole che si desidera utilizzare.  
  
    -   Selezionare **\<Sfoglia...\>** per specificare un set di regole personalizzato esistente non incluso nell'elenco.  
  
    -   Definire un set di regole personalizzato.  Per ulteriori informazioni, vedere [Creazione di set di regole personalizzate](../code-quality/creating-custom-code-analysis-rule-sets.md).