---
title: "Procedura: impostare gli attributi CLR in un elemento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.EditAttributesDialog"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, attributi personalizzati"
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 19
---
# Procedura: impostare gli attributi CLR in un elemento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli attributi personalizzati sono attributi speciali che possono essere aggiunti a diagrammi, forme, connettori e gli elementi del dominio. È possibile aggiungere qualsiasi attributo che eredita la `System.Attribute` classe.  
  
### <a name="to-add-a-custom-attribute"></a>Per aggiungere un attributo personalizzato  
  
1.  Nel **Esplora DSL**, selezionare l'elemento a cui si desidera aggiungere un attributo personalizzato.  
  
2.  Nel **proprietà** finestra, accanto al **attributi personalizzati** proprietà, fare clic su Sfoglia (**...**) icona.  
  
     Il **Modifica attributi** verrà visualizzata la finestra di dialogo.  
  
3.  Nel **nome** colonna, fare clic su **\< Aggiungi attributo>** e digitare il nome dell'attributo. Premere INVIO.  
  
4.  La riga sotto il nome dell'attributo Mostra le parentesi. In questa riga digitare un tipo di parametro per l'attributo (ad esempio, `string`), quindi premere INVIO.  
  
5.  Nel **proprietà Name** colonna, digitare un nome appropriato, ad esempio, `MyString`.  
  
6.  Fare clic su **OK**.  
  
     Il **attributi personalizzati** proprietà Visualizza ora l'attributo nel formato seguente:  
  
     `[` *AttributeName* `(` *ParameterName* `=` *Tipo* `)]`  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario sugli strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)