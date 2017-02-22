---
title: "Pagina Sicurezza, Progettazione progetti | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.ProjectPropertiesSecurity"
  - "vb.XBAPProjectPropertiesSecurity"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Creazione progetti, pagina Sicurezza"
  - "Pagina sicurezza in Creazione progetti"
ms.assetid: 641d9cd3-fa07-498a-8568-3c169bb4d3d5
caps.latest.revision: 34
caps.handback.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Pagina Sicurezza, Progettazione progetti
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La pagina **Sicurezza** di **Progettazione progetti** consente di configurare le impostazioni di sicurezza dall'accesso di codice per le applicazioni distribuite tramite la distribuzione [!INCLUDE[ndptecclick](../../deployment/includes/ndptecclick_md.md)].  Per ulteriori informazioni, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Per accedere alla pagina **Sicurezza**, fare clic su un nodo di progetto in **Esplora soluzioni**, quindi scegliere **Proprietà** dal menu **Progetto**.  In **Progettazione progetti** fare clic sulla scheda **Sicurezza**.  
  
## Impostazioni sicurezza  
 **Attiva le impostazioni di sicurezza ClickOnce**  
 Specifica se le impostazioni di sicurezza devono essere attivate in fase di progettazione.  Quando questa opzione non è selezionata, tutte le altre opzioni della pagina **Sicurezza** non sono disponibili.  
  
> [!NOTE]
>  Quando si pubblica un'applicazione mediante la **Pubblicazione guidata**, questa opzione è attivata automaticamente.  
  
 Quando si seleziona questa opzione, è possibile selezionare uno dei due pulsanti di opzione: **È un'applicazione completamente attendibile** oppure **È un'applicazione parzialmente attendibile**.  
  
 Per impostazione predefinita, i progetti di applicazioni Web browser WPF hanno questa opzione selezionata.  
  
 Al contrario, per tutti gli altri tipi di progetto questa opzione è deselezionata.  
  
 **È un'applicazione completamente attendibile**  
 Se si seleziona questa opzione, l'applicazione richiederà autorizzazioni di attendibilità totale al momento dell'installazione o dell'esecuzione in un computer client.  Se possibile, evitare di utilizzare Attendibilità totale, perché all'applicazione verrà concesso un accesso illimitato a risorse quali il file system e il Registro di sistema.  
  
 Per impostazione predefinita, i  progetti di applicazioni Web browser WPF hanno questa opzione impostata su Attendibilità parziale.  
  
 Per tutti gli altri tipi di progetto, questa opzione è impostata per impostazione predefinita, su Attendibilità totale.  
  
 **È un'applicazione parzialmente attendibile**  
 Se si seleziona questa opzione, l'applicazione richiederà autorizzazioni di attendibilità parziale al momento dell'installazione o dell'esecuzione in un computer client.  *Attendibilità parziale* significa che verranno eseguite soltanto le azioni consentite con le autorizzazioni di sicurezza dell'accesso al codice richieste.  Per ulteriori informazioni sulla configurazione delle autorizzazioni di sicurezza, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 È possibile specificare le impostazioni di sicurezza di attendibilità parziale configurando le opzioni presenti nell'area **Autorizzazioni di sicurezza ClickOnce**.  
  
## Autorizzazioni di sicurezza ClickOnce  
 **Zona da cui verrà installata l'applicazione**  
 Specifica un set predefinito di autorizzazioni di sicurezza dell'accesso al codice.  Scegliere **Internet** o **Intranet locale** per un set di autorizzazioni limitato oppure **\(Personalizzato\)** per configurare un set di autorizzazioni personalizzato.  Se l'applicazione richiede più autorizzazioni di quante ne siano state concesse in una zona, viene visualizzata una richiesta di attendibilità ClickOnce per l'utente finale per la concessione delle autorizzazioni aggiuntive.  Per ulteriori informazioni sulla configurazione delle autorizzazioni di sicurezza, vedere [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md).  
  
 Per impostazione predefinita, i  progetti di applicazioni Web browser WPF hanno questa opzione impostata su **Internet**.  
  
 **Modifica XML autorizzazioni**  
 Apre il modello del manifesto dell'applicazione \(app.manifest\) per configurare le autorizzazioni per il set di autorizzazioni **\(Personalizzato\)**.  
  
 **Avanzate**  
 Apre la [Finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md) che consente di configurare le impostazioni per il debug dell'applicazione con autorizzazioni limitate.  Queste impostazioni vengono controllate durante l'esecuzione del debug e le eccezioni dell'autorizzazione indicano che l'applicazione potrebbe richiedere maggiori autorizzazioni rispetto a quelle definite in una zona.  
  
## Vedere anche  
 <xref:System.Security.Permissions.WebBrowserPermission>   
 <xref:System.Security.Permissions.MediaPermission>   
 [Sicurezza dall'accesso di codice per applicazioni ClickOnce](../../deployment/code-access-security-for-clickonce-applications.md)   
 [How to: Enable ClickOnce Security Settings](../../deployment/how-to-enable-clickonce-security-settings.md)   
 [Procedura: impostare un'area di sicurezza per un'applicazione ClickOnce](../../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Procedura: impostare le autorizzazioni personalizzate per un'applicazione ClickOnce](../../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Procedura: eseguire il debug di un'applicazione ClickOnce con autorizzazioni limitate](../../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [ClickOnce Security and Deployment](../../deployment/clickonce-security-and-deployment.md)   
 [Riferimenti alle proprietà di progetto](../../ide/reference/project-properties-reference.md)   
 [Finestra di dialogo Impostazioni di sicurezza avanzate](../../ide/reference/advanced-security-settings-dialog-box.md)