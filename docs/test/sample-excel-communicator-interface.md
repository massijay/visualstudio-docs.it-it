---
title: "Interfaccia Excel Communicator di esempio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1dbf1090-762c-4824-82dd-2d7c2c6f00b6
caps.latest.revision: 11
ms.author: "mlearned"
manager: "douge"
caps.handback.revision: 11
---
# Interfaccia Excel Communicator di esempio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'interfaccia `IExcelUICommunication` di esempio viene utilizzata nell'oggetto `ExcelUICommunicator` nel progetto `ExcelAddIn`.  
  
## Interfaccia IExcelUICommunication  
 Questa interfaccia consente di definire i punti di comunicazione tra l'oggetto `CodedUIExtension`, che è in esecuzione nel processo del test codificato dell'interfaccia utente, e l'oggetto `ExcelCodedUIAddIn` che è in esecuzione nel processo di [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)].  
  
 L'assembly `ExcelCodedUIAddinHelper` dispone di una classe `ExcelUICommunicator` che deriva da questa interfaccia e consente di utilizzare il modello a oggetti di Excel per elaborare i metodi.  
  
 Tramite alcuni metodi è possibile ottenere le informazioni richieste da Excel e quindi creare e restituire uno degli oggetti informazioni, quale l'oggetto `CellInformation`.  
  
 Altri metodi consentono di utilizzare un oggetto informazioni fornito, di trovare il controllo corrispondente in Excel e di eseguire il processo sul controllo.  Ad esempio, il metodo `ScrollIntoView` consente di scorrere il foglio di lavoro in modo che la cella designata sia visibile.  
  
## Comunicazione di CodedUIExtensibilitySample e ExcelCodedUIAddinHelper  
 L'assembly `ExcelCodedUIAddinHelper` viene eseguito nel processo di Excel e dispone della classe `UICommunicator` tramite cui viene implementata l'interfaccia `IExcelUITestCommunication` e si ottengono o si impostano le informazioni necessarie direttamente dall'interfaccia utente di Excel.  
  
 L'assembly `CodedUIExtensibilitySample` viene eseguito nel processo del test codificato dell'interfaccia utente di Visual Studio.  Questo assembly dispone della classe `Communicator` che consente di aprire un canale .NET Remoting. Fornisce una proprietà `Instance` in cui viene utilizzata l'interfaccia `IExcelUICommunication` per utilizzare l'oggetto `UICommunicator` nell'assembly `ExcelCodedUIAddinHelper` per passare tra i due assembly richieste e oggetti informazioni, quale un oggetto `CellInformation`.  
  
## Vedere anche  
 [Estensione di test codificati dell'interfaccia utente e registrazioni delle azioni per supportare Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)   
 [Componente aggiuntivo di Excel di esempio per i test codificati dell'interfaccia utente](../test/sample-excel-add-in-for-coded-ui-testing.md)   
 [Estensione di esempio per i test codificati dell'interfaccia utente per Excel](../test/sample-coded-ui-test-extension-for-excel.md)