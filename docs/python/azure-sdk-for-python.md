---
title: Azure SDK per Python | Microsoft Docs
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d30fddae-8e2f-4f50-90d3-8ed2cd35c7a6
caps.latest.revision: 11
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: c00adbbabf0d3b82acb17f4a269dfc693246bc69
ms.openlocfilehash: 89de0d11791dbf13b9d4fcfcea8168b443d2777b
ms.contentlocale: it-it
ms.lasthandoff: 08/01/2017

---

# <a name="azure-sdk-for-python"></a>Azure SDK per Python

Azure SDK per Python semplifica l'uso e la gestione dei servizi di Microsoft Azure dalle applicazioni eseguite in Windows, Mac, OSX e Linux.

## <a name="installation"></a>Installazione

Azure SDK può essere installato da [Python Package Index](https://pypi.python.org/pypi/azure) (Indice dei pacchetti Python).

Installare la **versione stabile più recente** che supporta Python 2.7 e 3.3+, come indicato di seguito:

```bash
pip install azure
```

È anche possibile seguire le indicazioni in [Installazione di Python e dell'SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/) nella documentazione di Azure.

## <a name="documentation"></a>Documentazione

La documentazione è disponibile in [azure-sdk-for-python.readthedocs.org](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html).

Anche nella sezione [Azure SDK per Python del Centro per sviluppatori Python](http://azure.microsoft.com/develop/python/) sono disponibili numerose risorse utili, incluse alcune esercitazioni come:

  - Creazione di app Web con [Django](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-django-app) [Flask](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-flask-app) e [Bottle](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-bottle-app).
  - [Archiviazione - BLOB](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-blob-storage)
  - [Archiviazione - Tabelle](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-table-storage)
  - [Archiviazione - Code](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-queue-storage)
  - [DocumentDB](https://docs.microsoft.com/azure/documentdb/documentdb-python-application)
  - [Come usare le code del bus di servizio](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
  - [Come usare gli argomenti e le sottoscrizioni del bus di servizio](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
  - [Gestione dei servizi](https://docs.microsoft.com/azure/cloud-services/cloud-services-python-how-to-use-service-management)

Per le API pubbliche senza documentazione, gli unit test nel [repository GitHub dell'SDK](https://github.com/Azure/azure-sdk-for-python) rappresentano una buona fonte di informazioni:

- [Unit test per l'archiviazione](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [Unit test per il bus di servizio](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [Unit test per la gestione dei servizi](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [Unit test per la gestione delle risorse](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>Supporto

Il repository GIT per l'SDK è disponibile all'indirizzo [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python).

Per qualsiasi problema o domanda relativi all'uso dell'SDK, [registrare i problemi nel repository](https://github.com/Azure/azure-sdk-for-python/issues).

