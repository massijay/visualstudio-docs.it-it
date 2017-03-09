---
title: "Procedura: Usare la diagnostica grafica con un dispositivo ARM | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Usare la diagnostica grafica con un dispositivo ARM
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La diagnostica grafica supporta il debug remoto di app Direct3D su dispositivi basati su ARM che eseguono Windows RT 8.1 o Windows Phone 8.1.  È possibile acquisire informazioni grafiche dall'app Direct3D mentre è in esecuzione nel dispositivo oppure usare quest'ultimo come dispositivo di riproduzione per le informazioni grafiche acquisite in precedenza.  
  
## Uso della diagnostica grafica con un dispositivo basato su ARM  
 Dato che Visual Studio non può essere eseguito su dispositivi basati su ARM, è necessario usare il debugger remoto per analizzare app che vengono eseguite su tali dispositivi.  Il debugger remoto supporta l'acquisizione e la riproduzione della grafica, consentendo in tal modo di diagnosticare errori di rendering e di valutare le prestazioni grafiche su qual tipo di dispositivi con la stessa semplicità con cui vi si esegue il debug dell'app.  
  
 Per usare le funzionalità di diagnostica grafica, abilitare prima il debug remoto nel dispositivo.  
  
#### Per abilitare il debug remoto in un dispositivo basato su ARM  
  
1.  Installare i[criteri dei kit ARM](http://msdn.microsoft.com/windows/desktop/dn469188) nel dispositivo basato su ARM.  
  
2.  Installare [Remote Tools](http://go.microsoft.com/fwlink/?LinkId=393086) nel dispositivo basato su ARM.  
  
> [!IMPORTANT]
>  Per dispositivi Windows Phone 8.1, potrebbe essere necessario registrare il proprio telefono per lo sviluppo.  Per tale operazione è necessario essere uno sviluppatore registrato.  Per altre informazioni, vedere [Come distribuire ed eseguire un'app per Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Dopo aver abilitato il debug remoto nel dispositivo, renderlo la destinazione del debug e avviare la diagnostica grafica.  
  
#### Per configurare e avviare la diagnostica grafica nel dispositivo  
  
1.  Nell'elenco **Piattaforme soluzione** selezionare **ARM**. In questo modo il dispositivo basato su ARM sarà disponibile come destinazione del debug remoto.  
  
2.  Nell'elenco a discesa **Destinazione di debug** selezionare il dispositivo ARM.  
  
3.  Dal menu, scegliere **Debug**, **Grafica**, **Avvia diagnostica** \(da tastiera: ALT\+F5\)  
  
## Vedere anche  
 [Eseguire app di Windows Store in un computer remoto](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Procedura: modificare il computer di riproduzione della diagnostica grafica](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)