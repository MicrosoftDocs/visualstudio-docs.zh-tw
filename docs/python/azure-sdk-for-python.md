---
title: "Azure SDK for Python |Microsoft 文件"
description: "適用於 Python 的 Azure SDK 可讓您更輕鬆地從在任何平台上執行的 Python 應用程式取用 Microsoft Azure 服務。"
ms.custom: 
ms.date: 01/22/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: 
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: f4f42f80bef2548c8caaff84df0d9a0118bfeac7
ms.sourcegitcommit: ba29e4d37db92ec784d4acf9c6e120cf0ea677e9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="azure-sdk-for-python"></a>Azure SDK for Python

Azure SDK for Python 可讓您更輕鬆地從 Windows、Mac OSX 和 Linux 上執行的應用程式使用及管理 Microsoft Azure 服務。

## <a name="installation"></a>安裝

Azure SDK 是從 [Python 封裝索引 (英文)](https://pypi.python.org/pypi/azure) 安裝。

如下所示安裝**最新的穩定版本** (支援 Python 2.7 與 3.x 或更新版本)：

```command
pip install azure
```

您也可以遵循 Azure 文件中的[安裝 Python 和 SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/)。

## <a name="documentation"></a>文件

您可以在 [azure-sdk-for-python.readthedocs.org (英文)](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html) 找到文件。

[適用於 Python 的 Azure SDK 開發人員中心](http://azure.microsoft.com/develop/python/)也有一些實用的資源，其中包括數個教學課程：

- 使用 [Django](/azure/app-service-web/web-sites-python-create-deploy-django-app)、[Flask](/azure/app-service-web/web-sites-python-create-deploy-flask-app) 和 [Bottle](/azure/app-service-web/web-sites-python-create-deploy-bottle-app) 建立 Web 應用程式。
- [Blob 儲存體](/azure/storage/storage-python-how-to-use-blob-storage)
- [表格儲存體](/azure/storage/storage-python-how-to-use-table-storage)
- [佇列儲存體](/azure/storage/storage-python-how-to-use-queue-storage)
- [DocumentDB](/azure/documentdb/documentdb-python-application)
- [服務匯流排佇列](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [服務匯流排主題/訂用帳戶](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [服務管理](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

對於沒有文件的公用 API，[SDK 的 GitHub 存放庫](https://github.com/Azure/azure-sdk-for-python)中的單元測試是很好的資訊來源：

- [儲存體單元測試 (英文)](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [服務匯流排單元測試 (英文)](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [服務管理單元測試 (英文)](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [資源管理單元測試 (英文)](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>支援

SDK 的 Git 存放庫網址如下：[https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python)。

如果您發現任何問題，或對 SDK 的使用方式有任何疑問，請[在存放庫中提出問題](https://github.com/Azure/azure-sdk-for-python/issues)。
