---
title: "Eseguire uno unit test come processo a 64 bit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "unit test, creazione"
  - "unit test, esecuzione"
ms.assetid: d23a9ee7-58e3-4e8b-a38c-b2207ea73fea
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "mlearned"
manager: "douge"
---
# Eseguire uno unit test come processo a 64 bit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si dispone di un computer a 64 bit, è possibile eseguire unit test e acquisire informazioni di code coverage utilizzando un processo a 64 bit.  
  
## Esecuzione di uno unit test come processo a 64 bit  
  
#### Per eseguire uno unit test come processo a 64 bit  
  
1.  Se il codice o i test sono stati compilati come 32 bit\/x86, ma si desidera eseguirli come processo a 64 bit, ricompilarli come **Qualsiasi CPU** o, facoltativamente, come **64 bit**.  
  
    > [!TIP]
    >  Per la flessibilità massima, è necessario compilare i progetti di test con la configurazione **Qualsiasi CPU**.  È quindi possibile l'esecuzione su entrambi gli agenti a 32 e 64 bit.  Non vi sono vantaggi nella compilazione di progetti di test con la configurazione a **64 bit**.  
  
2.  Dal menu di Visual Studio, scegliere **Test**, quindi scegliere **Impostazioni** e quindi scegliere **Architettura processori**.  Scegliere **x64** per eseguire i test come processo a 64 bit.  
  
     \-oppure\-  
  
     Specificare `<TargetPlatform>x64</TargetPlatform>` in un file .runsettings.  Un vantaggio di questo metodo consiste nel specificare i gruppi di impostazioni in file diversi e passare rapidamente da impostazioni diverse.  È inoltre possibile copiare le impostazioni tra soluzioni.  Per ulteriori informazioni, vedere [Configurazione di unit test usando un file con estensione runsettings](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md).  
  
## Vedere anche  
 [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)   
 [Eseguire unit test del codice](../test/unit-test-your-code.md)   
 [Specifica delle impostazioni test di Visual Studio](/devops-test-docs/test/specifying-test-settings-for-visual-studio-tests)