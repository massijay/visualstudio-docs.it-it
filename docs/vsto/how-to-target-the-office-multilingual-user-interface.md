---
title: "Procedura: utilizzare l&#39;interfaccia utente multilingue (MUI) di Office | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "globalizzazione [sviluppo per Office in Visual Studio], destinazione dell'interfaccia utente"
  - "localizzazione [sviluppo per Office in Visual Studio], destinazione dell'interfaccia utente"
  - "MUI [sviluppo per Office in Visual Studio]"
  - "Multilingual User Interface [sviluppo per Office in Visual Studio]"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], globalizzazione"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], localizzazione"
ms.assetid: b1f03164-f0cf-42e3-942b-8cf90c242ffb
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# Procedura: utilizzare l&#39;interfaccia utente multilingue (MUI) di Office
  L'interfaccia utente multilingue \(MUI, Multilingual User Interface\) costituisce una funzionalità di Microsoft Office che offre all'utente finale la possibilità di modificare la lingua dell'interfaccia utente.  Un utente che utilizza un'interfaccia utente in inglese, ad esempio, può modificarne la lingua in modo da utilizzare lo spagnolo.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Se l'applicazione è destinata a utenti che utilizzano più lingue di Office, è possibile aggiungere codice per modificare automaticamente la lingua delle stringhe dell'interfaccia utente in base alla lingua utilizzata in Office sul computer dell'utente, a condizione che vi siano installate le risorse corrette.  
  
### Per verificare l'impostazione corrente dell'interfaccia utente di Office  
  
1.  Utilizzare la proprietà <xref:System.Threading.Thread.CurrentUICulture%2A> del thread corrente.  Impostare la lingua delle stringhe dell'interfaccia utente in modo che corrisponda a quella utilizzata nella versione di Office attualmente in esecuzione nel computer dell'utente.  
  
     [!code-csharp[Trin_VstcoreCreatingExcel#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/CS/Sheet1.cs#10)]
     [!code-vb[Trin_VstcoreCreatingExcel#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreCreatingExcel/VB/Sheet1.vb#10)]  
  
## Vedere anche  
 [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)   
 [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)  
  
  