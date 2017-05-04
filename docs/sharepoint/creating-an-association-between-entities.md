---
title: "Creazione di un&#39;associazione tra entit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.BDC.Association_Dialog"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], associare tipi di contenuto esterno"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], associazioni tra entità"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creare un'associazione"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], entità correlate"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], associare tipi di contenuto esterno"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], associazioni tra entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], creare un'associazione"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], entità correlate"
ms.assetid: c908448c-13d3-4d2f-89ad-8d709b2958fb
caps.latest.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Creazione di un&#39;associazione tra entit&#224;
  È possibile definire relazioni tra entità nel modello di integrazione applicativa dei dati mediante la creazione di associazioni.  In Visual Studio vengono generati metodi che forniscono informazioni su ogni associazione agli utenti del modello.  Questi metodi possono essere utilizzati da web part di SharePoint, elenchi o applicazioni personalizzate per visualizzare relazioni dei dati in un'interfaccia utente.  
  
## Creazione di un'associazione  
 Per creare un'associazione scegliendo il controllo **Associazione** nella **Casella degli strumenti** di Visual Studio, selezionare la prima entità \(detta entità di origine\), quindi selezionare la seconda entità \(detta entità di destinazione\).  È possibile definire i dettagli dell'associazione nell'**Editor di associazione**.  Per ulteriori informazioni, vedere [Procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## Metodi di associazione  
 Applicazioni come le web part di integrazione applicativa dei dati di SharePoint utilizzano associazioni mediante la chiamata ai metodi nella classe di servizio di un'entità.  È possibile aggiungere metodi alla classe di servizio di un'entità selezionandoli nell'**Editor di associazione**.  
  
 Per impostazione predefinita, l'**Editor di associazione** aggiunge un metodo di tipo AssociationNavigator alle entità di origine e di destinazione.  Un metodo di tipo AssociationNavigator nell'entità di origine consente agli utenti di recuperare un elenco di entità di destinazione.  Un metodo di tipo AssociationNavigator nell'entità di destinazione consente agli utenti di recuperare l'entità di origine correlata all'entità di destinazione.  
  
 È necessario aggiungere il codice a ognuno di questi metodi per restituire le informazioni corrette.  È inoltre possibile aggiungere altri tipi di metodi per supportare scenari più avanzati.  Per ulteriori informazioni su ognuno di questi metodi, vedere [Operazioni supportate](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## Tipi di associazioni  
 È possibile creare due tipi di associazioni nella finestra di progettazione dell'integrazione applicativa dei dati: associazioni basate su chiave esterna e associazioni senza chiave esterna.  
  
### Associazione basata su chiave esterna  
 È possibile creare un'associazione basata su chiave esterna creando una relazione tra un identificatore nell'entità di origine e i descrittori di tipo definiti nell'entità di destinazione.  Questa relazione consente a coloro che utilizzano il modello di fornire un'interfaccia utente avanzata per gli utenti.  Ad esempio, un form di Outlook che consente un utente di creare un ordine di vendita in cui vengono visualizzati i clienti in un elenco a discesa oppure un elenco di ordini di vendita in SharePoint che consente agli utenti di aprire una pagina del profilo di un cliente.  
  
 Per creare un'associazione basata su chiave esterna, è necessario mettere in relazione identificatori e descrittori di tipo che condividono lo stesso nome e lo stesso tipo.  È possibile, ad esempio, creare un'associazione basata su chiave esterna tra un'entità `Contact` e un'entità `SalesOrder`.  L'entità `SalesOrder` restituisce un descrittore di tipo `ContactID` come parte del parametro restituito dal metodo Finder o Finder specifico.  Entrambi i descrittori di tipo vengono visualizzati nell'**Editor di associazione**.  Per creare una relazione basata su chiave esterna tra l'entità `Contact` e l'entità `SalesOrder`, selezionare l'identificatore `ContactID` accanto ad ognuno di questi campi.  
  
 Aggiungere codice al metodo di tipo AssociationNavigator dell'entità di origine in modo che restituisca una raccolta di entità di destinazione.  Nell'esempio seguente vengono restituiti gli ordini di vendita per un contatto.  
  
 [!code-csharp[SP_BDC#7](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#7)]  
  
 Aggiungere codice al metodo di tipo AssociationNavigator dell'entità di destinazione in modo che restituisca un'entità di origine.  Nell'esempio seguente viene restituito il contatto correlato all'ordine di vendita.  
  
 [!code-csharp[SP_BDC#8](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderservice.vb#8)]  
  
### Associazione senza chiave esterna  
 È possibile creare un'associazione senza eseguire il mapping di identificatori ai descrittori di tipo di campo.  Creare questo tipo di associazione quando l'entità di origine non dispone di una relazione diretta con l'entità di destinazione.  Ad esempio, una tabella `SalesOrderDetail` non dispone di una chiave esterna di cui viene eseguito il mapping a una chiave primaria in una tabella `Contact`.  
  
 Se si desidera visualizzare informazioni nella tabella `SalesOrderDetail` correlate a una tabella `Contact`, è possibile creare un'associazione senza chiave esterna tra l'entità `Contact` e l'entità `SalesOrderDetail`.  
  
 Nel metodo di tipo AssociationNavigator dell'entità `Contact` è possibile restituire le entità `SalesOrderDetail` unendo le tabelle o chiamando una stored procedure.  
  
 Nell'esempio seguente vengono restituiti dettagli di tutti gli ordini di vendita mediante l'unione delle tabelle.  
  
 [!code-csharp[SP_BDC#9](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#9)]  
  
 Nel metodo di tipo AssociationNavigator dell'entità `SalesOrderDetail` restituire l'entità `Contact` correlata.  Nell'esempio che segue viene illustrato quanto descritto.  
  
 [!code-csharp[SP_BDC#10](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## Vedere anche  
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)  
  
  