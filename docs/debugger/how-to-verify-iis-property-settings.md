---
title: "Procedura: verificare le impostazioni delle propriet&#224; di IIS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debug di applicazioni Web, risoluzione dei problemi"
  - "strumento di amministrazione IIS"
  - "IIS, impostazioni di proprietà"
  - "proprietà [debugger], impostazione con lo strumento di amministrazione IIS"
  - "applicazioni Web, impostazione di proprietà"
ms.assetid: 9efc50bf-02fb-4750-9b3e-f03c38f10d8b
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Procedura: verificare le impostazioni delle propriet&#224; di IIS
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile impostare le proprietà di un'applicazione Web utilizzando lo strumento di amministrazione IIS.  Per consentire l'esecuzione dell'applicazione, è necessario che tali proprietà siano impostate correttamente, pertanto la verifica di queste impostazioni è spesso un passaggio necessario nel processo di risoluzione dei problemi.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per controllare le impostazioni IIS dell'applicazione Web  
  
1.  Aprire la finestra **Strumenti di amministrazione**. Fare clic sul pulsante **Start**, scegliere **Programmi**, quindi **Strumenti di amministrazione**.  Se **Strumenti di amministrazione** non è presente nel menu **Programmi**, cercarlo nel **Pannello di controllo**.  
  
    -   In Windows 2000 selezionare **Gestione servizi Internet**.  
  
    -   In Windows XP selezionare **Internet Information Services**.  
  
    -   In Windows Server 2003 fare doppio clic su **Amministrazione server**.  
  
         Viene visualizzata la finestra **Amministrazione server**.  In **Server applicazioni** fare clic su **Gestisci questo server applicazioni**.  
  
         Viene visualizzata la finestra **Server applicazioni**.  Aprire il nodo **Gestione Internet Information Services \(IIS\)** nel riquadro di sinistra.  
  
2.  Nella finestra di dialogo fare clic sul nodo del controllo struttura ad albero per il computer.  Fare clic sul nodo **Siti Web**, quindi selezionare il nodo dell'applicazione Web.  Si tratterà di un nodo di sito Web, quindi di pari livello rispetto al nodo **Sito Web predefinito** o di un nodo di directory virtuale sottostante un nodo di sito Web.  
  
3.  Fare clic con il pulsante destro del mouse sull'applicazione Web, quindi scegliere **Proprietà** dal menu di scelta rapida.  
  
4.  Verificare le impostazioni di sicurezza dell'applicazione Web:  
  
    1.  Nella finestra **Proprietà** dell'applicazione Web fare clic sulla scheda **Sicurezza directory** e scegliere **Modifica**.  
  
    2.  Nella finestra di dialogo **Metodi di autenticazione** selezionare **Consenti accesso anonimo** e **Autenticazione Windows integrata**, se queste opzioni non sono già selezionate.  
  
    3.  Scegliere **OK** per chiudere la finestra di dialogo **Metodi di autenticazione**.  
  
5.  Per un'applicazione ATL Server verificare che il verbo DEBUG sia associato all'estensione ISAPI.  Per ulteriori informazioni, vedere [How to: Associate DEBUG Verb with Extension](http://msdn.microsoft.com/it-it/50d261d3-4bd4-41c0-b44e-3591086f121e).  
  
6.  Per un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], accertarsi che la cartella virtuale dell'applicazione disponga di un Nome applicazione impostato in **Gestione Internet Information Services \(IIS\)**, **Gestione servizi Internet** o **Internet Information Services**.  
  
    1.  Nella finestra **Proprietà** dell'applicazione Web scegliere la scheda **Directory**, se l'applicazione è contenuta in una directory virtuale, o **Home directory**, se è contenuta in un sito Web.  
  
    2.  Verificare che il nome in **Percorso locale** corrisponda al nome della directory in cui l'applicazione è stata effettivamente distribuita.  
  
    3.  In **Impostazioni applicazione** digitare il nome della directory radice che contiene l'applicazione.  
  
    4.  Scegliere **OK** per chiudere la finestra di dialogo **Proprietà**.  
  
7.  Per un'applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], fare clic sulla scheda **ASP.NET** e verificare che sia specificata la versione corretta di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
8.  Scegliere **OK** per chiudere la finestra di dialogo **Proprietà**.  
  
9. Scegliere **OK** per chiudere le finestre di dialogo **Gestione Internet Information Services \(IIS\)**, **Gestione servizi Internet** o **Internet Information Services**.  
  
## Vedere anche  
 [Risoluzione dei problemi](../debugger/debugging-web-applications-troubleshooting.md)