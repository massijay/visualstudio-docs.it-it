---
title: "Area test 5: Modifica controllo del codice sorgente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente [Visual Studio SDK], modifica"
  - "origine plug-in del controllo, la modifica controllo del codice sorgente"
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Area test 5: Modifica controllo del codice sorgente
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Controllo del codice sorgente del plug\-in test responsabilità modifica il controllo del codice sorgente tramite la **Modifica controllo del codice sorgente** comando.  
  
 **Modifica controllo del codice sorgente** comando fornisce quattro funzioni di base per l'utente:  
  
-   **Operazione di binding:**  
  
     Consente di stabilire o ristabilire un collegamento di controllo di origine tra un progetto\/soluzione e l'archivio versione.  
  
-   **Annullamento del binding:**  
  
     Rimuove una progetto\/soluzione dal controllo del codice sorgente in una singola connessione.  
  
-   **Connessione\/disconnessione:**  
  
 Attiva o disattiva stato connesso o non in linea della soluzione controllato, le indicazioni riportata nella zona 3. Per altre informazioni, vedere [Area test 3: Estrazione \/ Annulla estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).  
  
## Accedere al Menu comando  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] percorso menu ambiente di sviluppo integrato viene utilizzato nei test case.  
  
 Modifica controllo del codice sorgente:**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**.  
  
## Test case  
 Di seguito sono specifici test case per il **Modifica controllo del codice sorgente** comando area di test.  
  
### Caso 5a: associazione  
 Operazione di binding consente all'utente di aggiungere informazioni di controllo codice sorgente per i progetti selezionati e le soluzioni. L'utente è in genere viene richiesto di identificare un progetto nel controllo del codice sorgente in cui questi devono essere aggiunti. L'utente non può creare un nuovo progetto nel controllo del codice sorgente come parte di questa operazione \(contrasto con Aggiungi al controllo del codice sorgente\).  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Associare a un percorso vuoto|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire **Modifica controllo del codice sorgente** la finestra di dialogo \(**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**\).<br />4.  Fare clic su **disassociare**.<br />5.  Accettare la finestra di dialogo di avviso se viene visualizzato.<br />6.  Selezionare tutti gli elementi.<br />7.  Fare clic su **Binding**.<br />8.  Selezionare un percorso vuoto in un archivio di controllo di origine.<br />9. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />10. Fare clic su **Continua con le associazioni** nella finestra di dialogo di conferma.<br />11. Fare clic su **OK** nella finestra di dialogo Avviso Se viene visualizzata.<br />12. Archivia i file. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />13. Aprire soluzioni dal controllo del codice sorgente in una nuova posizione.|`Result from Step 12:`<br /><br /> Soluzioni e progetti sono associati a e scritte nella destinazione di nuovo nell'archivio delle versioni.<br /><br /> Vengono archiviati i file di soluzione e progetto.<br /><br /> Gerarchia di progetto dell'archivio versione corrisponde gerarchia di cartelle del progetto su disco.<br /><br /> `Result from Step 13:`<br /><br /> Tutti gli elementi di progetto vengono scaricati.|  
|Associare alla posizione che è sincronizzato con client|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Creare un duplicato del progetto e soluzione nell'archivio delle versioni \(condividere e creare un Branch se utilizza [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />4.  Aprire **Modifica controllo del codice sorgente** la finestra di dialogo \(**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**\).<br />5.  Separa tutte.<br />6.  Fare clic su **OK** per chiudere **Modifica controllo del codice sorgente** la finestra di dialogo.<br />7.  Riaprire **Modifica controllo del codice sorgente** la finestra di dialogo.<br />8.  Selezionare tutto.<br />9. Fare clic su **Binding**.<br />10. Selezionare il percorso del progetto e soluzione sottoposte a branching \(ottenuto nel passaggio 3\)<br />11. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />12. Ottenere più recente in modo ricorsivo per tutti gli elementi.|Contenuto del file dopo l'operazione get è esattamente come prima l'operazione get.|  
|Associare alla posizione che non è sincronizzato con client|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Creare un duplicato del progetto e soluzione nell'archivio delle versioni \(condividere e creare un Branch se utilizza [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]\).<br />4.  Modificare i file del progetto nell'archivio delle versioni sottoposte a branching.<br />5.  Aprire **Modifica controllo del codice sorgente** la finestra di dialogo \(**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**\).<br />6.  Separa tutte.<br />7.  Fare clic su **OK** per chiudere **Modifica controllo del codice sorgente** la finestra di dialogo.<br />8.  Riaprire **Modifica controllo del codice sorgente** la finestra di dialogo.<br />9. Selezionare tutto.<br />10. Fare clic su **Binding**.<br />11. Passare al percorso per soluzioni e progetti in precedenza a branching.<br />12. Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />13. Accettare la finestra di dialogo di avviso se viene visualizzato.<br />14. Ottenere ricorsiva più recente per tutti gli elementi.|I file che sono stati modificati nel passaggio 4 sono inoltre modificati localmente.|  
|Associare soluzione mai sotto il controllo del codice sorgente|1.  Creare una cartella vuota nel controllo del codice sorgente.<br />2.  Creare un progetto client.<br />3.  Aprire **Modifica controllo del codice sorgente** la finestra di dialogo \(**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**\).<br />4.  Associare la soluzione in un percorso vuoto nel controllo del codice sorgente.<br />5.  Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />6.  Fare clic su **Continua con le associazioni** nella finestra di dialogo di conferma.<br />7.  Fare clic su **OK** nella finestra di dialogo Avviso Se viene visualizzata.|Soluzione viene aggiunta al controllo del codice sorgente.<br /><br /> Soluzioni e progetti sono stati estratti.|  
|Annullare l'operazione di binding|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4.  Separa tutte.<br />5.  Fare clic su **OK** per chiudere la finestra di dialogo. Se questo passaggio ha esito positivo, andare al passaggio successivo.<br />6.  Riaprire la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />7.  Associare alla posizione non correlati.<br />8.  Fare clic su **Annulla**.|`Result from Step 5:`<br /><br /> La soluzione non è più in controllo del codice sorgente<br /><br /> `Result from Step 8:`<br /><br /> Soluzione è ancora non in controllo del codice sorgente.|  
  
### Caso 5b: separare  
 Rimuovere il binding Rimuove informazioni sul controllo di codice di origine da progetti e la propria soluzione. La soluzione e progetti interessati sono basati su una combinazione di selezione dell'utente e come gli elementi sono stati aggiunti al controllo del codice sorgente.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Separare soluzione contenente un File System o il progetto Web IIS locale e il progetto di un client|1.  Creare un File System o un progetto Web IIS locale.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto client alla soluzione.<br />4.  Se richiesto, accettare controllare della soluzione.<br />5.  Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />6.  Fare clic su **disassociare**.<br />7.  Fare clic su **OK** per chiudere la finestra di dialogo.<br />8.  Tenta di estrarre soluzioni, progetti, elementi di soluzione, gli elementi di progetto.|Soluzioni e progetti non sono sotto controllo del codice sorgente.<br /><br /> Non vengono visualizzati i comandi di menu di controllo di origine.|  
|Annullamento del binding Annulla|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />4.  Fare clic su **separare tutti**.<br />5.  Fare clic su **Annulla**.|Soluzione consiste nel controllo del codice sorgente.|  
  
### Caso 5C: riassociare  
 Riassociazione è semplicemente una combinazione di separazione e binding, ovvero il processo di riassociazione di una progetto\/soluzione era precedentemente in controllo del codice sorgente che è stato associato.  
  
|Operazione|Passi di test|Per verificare i risultati previsti|  
|----------------|-------------------|-----------------------------------------|  
|Riassociare soluzioni e progetti senza chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />4.  Fare clic su **disassociare**.<br />5.  Selezionare tutte le righe.<br />6.  Fare clic su **Binding**.<br />7.  Fare clic su **OK** per chiudere la **Modifica controllo del codice sorgente** la finestra di dialogo.<br />8.  Se richiesto, accetta l'estrazione.|Soluzioni e progetti sottoposti al controllo del codice sorgente.|  
|Riassociare progetto solo senza chiudere **Modifica controllo del codice sorgente** la finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere l'origine controllo utilizzando solo il progetto \(File \-\> origine controllo \-\> Aggiungi progetti selezionati a controllo del codice sorgente.<br />3.  Aprire la finestra di dialogo Modifica controllo del codice sorgente.<br />4.  Rimuovere il binding solo il progetto.<br />5.  Associare solo il progetto.|Soluzione rimane non controllata.<br /><br /> Progetto rimane controllato.|  
|Riassociare soluzione solo senza chiudere **Modifica controllo del codice sorgente** la finestra di dialogo|1.  Creare un progetto.<br />2.  Aggiungere solo la soluzione al controllo di origine utilizzando \(**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**.<br />3.  Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />4.  Separare solo la soluzione \(non chiudere **Modifica controllo del codice sorgente** la finestra di dialogo.\)<br />5.  Associare solo la soluzione.<br />6.  Fare clic su **OK** per chiudere la finestra di dialogo.<br />7.  Estrarre soluzioni e gli elementi di soluzione \(se presente.\)|Soluzione rimane controllata.<br /><br /> Progetto rimane non controllato.|  
|Riassociare progetto\/soluzione solo quando è nella stessa directory|1.  Creare un progetto.<br />2.  Aggiungere solo il progetto al controllo di origine usando \(**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**.<br />3.  Chiudere la soluzione.<br />4.  Creare una nuova soluzione con almeno due progetti.<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  Aggiungere il progetto creato nel passaggio 1 dal controllo del codice sorgente.<br />7.  Se richiesto, accettare l'estrazione della soluzione.<br />8.  Controllare nell'intera soluzione.<br />9. Aprire il **Modifica controllo del codice sorgente** la finestra di dialogo.<br />10. Selezionare il progetto aggiunto \(dal passaggio 6\) e fare clic su **Separa**.<br />11. Fare clic su **OK** per chiudere la finestra di dialogo.<br />12. Se richiesto, accettare l'estrazione.<br />13. Riaprire **Modifica controllo del codice sorgente** la finestra di dialogo.<br />14. Selezionare il progetto aggiunto \(dal passaggio 6\) e fare clic su **Binding**.<br />15. Selezionare il percorso originale.|Soluzioni e progetti rimangono controllati.|  
  
## Vedere anche  
 [Guida per i test per il Plug\-in di controllo codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)