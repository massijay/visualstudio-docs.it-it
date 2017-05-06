---
title: "Procedura: aggiungere un descrittore di filtro a un metodo Finder"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiungere un filtro"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], descrittori di filtro"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], aggiungere un filtro"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], descrittori di filtro"
ms.assetid: 228a6190-8cb8-4182-b6d9-d4c656f4a164
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: aggiungere un descrittore di filtro a un metodo Finder
  I descrittori di filtro consentono ai consumer del modello di passare valori ai metodi prima che vengano eseguiti.  Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
 Uno scenario comune è quello in cui gli utenti di SharePoint desiderano recuperare istanze di un tipo di contenuto esterno corrispondenti ad alcuni criteri.  È possibile supportare questo scenario aggiungendo un descrittore di filtro a un metodo Finder.  
  
### Per aggiungere un descrittore di filtro a un metodo Finder  
  
1.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati** espandere il nodo di un metodo Finder, espandere il nodo **Parametri**, quindi aggiungere un parametro di input.  Per ulteriori informazioni, vedere [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md).  
  
2.  Nella finestra **Dettagli metodo** selezionare il descrittore di tipo del parametro.  
  
3.  Nella barra dei menu, scegliere **Visualizza**, **Finestra proprietà**.  
  
4.  Nella finestra **Proprietà** impostare la proprietà **Nome tipo** su un tipo di dati adatto al filtro.  
  
     È ad esempio possibile applicare un filtro basato sulla data dell'ordine per limitare il numero di ordini di vendita restituiti dal metodo.  Per supportare tale filtro, è necessario impostare la proprietà **Nome tipo** del descrittore di tipo su **System.DateTime**.  
  
5.  Nella finestra **Dettagli metodo** espandere il nodo **Descrittori di filtro**.  
  
6.  Nell'elenco **Aggiungi un descrittore di filtro**, scegliere **Crea descrittore di filtro**.  
  
     Verrà visualizzato un nuovo descrittore di filtro nel nodo **Descrittori di filtro**.  
  
7.  Nella barra dei menu, scegliere **Visualizza**, **Finestra proprietà**.  
  
8.  Nella finestra **Proprietà** selezionare la proprietà **Tipo**.  
  
9. Nell'elenco visualizzato per la proprietà **Tipo** selezionare il criterio di filtro desiderato.  
  
     Per creare ad esempio un filtro che utilizza una data dell'ordine per limitare il numero di ordini di vendita restituiti in un metodo Finder, selezionare **Confronto**.  Un filtro confronto assicura che un metodo finder restituisca solo le istanze che soddisfano una specifica condizione.  Per ulteriori informazioni su ogni modello di filtro, vedere [Tipi di filtri supportati da BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
10. Nella finestra **Proprietà** selezionare la proprietà **Descrittori di tipo associati**.  
  
11. Nell'elenco visualizzato per la proprietà **Descrittori di tipo associati** selezionare il descrittore di tipo creato precedentemente in questa procedura.  Il filtro verrà associato al parametro di input del metodo Finder.  
  
12. Aggiungere codice al metodo Finder che restituisce dati.  È possibile utilizzare il parametro di input come condizione in una query Select.  
  
     Nell'esempio seguente vengono restituiti ordini di vendita con la data specificata.  
  
    > [!NOTE]  
    >  Sostituire il valore del campo `ServerName` con il nome del server locale.  
  
     [!code-csharp[SP_BDC#11](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#11)]
     [!code-vb[SP_BDC#11](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#11)]  
  
## Vedere anche  
 [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)   
 [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  