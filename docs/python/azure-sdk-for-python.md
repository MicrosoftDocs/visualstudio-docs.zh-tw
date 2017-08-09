---
title: "Azure SDK for Python |Microsoft 文件"
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
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: c64d1abc2266b7e2edbb2c81a46c53c39eb9a85a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/18/2017

---

# <a name="azure-sdk-for-python"></a>Azure SDK for Python

Azure SDK for Python 可讓您更輕鬆地從 Windows、Mac OSX 和 Linux 上執行的應用程式使用及管理 Microsoft Azure 服務。

## <a name="installation"></a>安裝

Azure SDK 是從 [Python 封裝索引 (英文)](https://pypi.python.org/pypi/azure) 安裝。

安裝**最新的穩定版本** (支援 Python 2.7 與 3.3 或更新版本)，如下所示：

```bash
pip install azure
```

您也可以遵循 Azure 文件中的[安裝 Python 和 SDK](https://azure.microsoft.com/documentation/articles/python-how-to-install/)。

## <a name="documentation"></a>文件

您可以在 [azure-sdk-for-python.readthedocs.org (英文)](http://azure-sdk-for-python.readthedocs.org/en/latest/index.html) 找到文件。

[Azure SDK for Python 開發人員中心](http://azure.microsoft.com/develop/python/)也有一些實用的資源，包括教學課程，例如：

  - 使用 [Django](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)、[Flask](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-flask-app) 和 [Bottle](https://docs.microsoft.com/azure/app-service-web/web-sites-python-create-deploy-bottle-app) 建立 Web 應用程式。
  - [Blob 儲存體](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-blob-storage)
  - [表格儲存體](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-table-storage)
  - [佇列儲存體](https://docs.microsoft.com/azure/storage/storage-python-how-to-use-queue-storage)
  - [DocumentDB](https://docs.microsoft.com/azure/documentdb/documentdb-python-application)
  - [服務匯流排佇列](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
  - [服務匯流排主題/訂用帳戶](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
  - [服務管理](https://docs.microsoft.com/azure/cloud-services/cloud-services-python-how-to-use-service-management)

對於沒有文件的公用 API，[SDK 的 GitHub 存放庫 (英文)](https://github.com/Azure/azure-sdk-for-python) 中的單元測試是很好的資訊來源：

- [儲存體單元測試 (英文)](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [服務匯流排單元測試 (英文)](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [服務管理單元測試 (英文)](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)
- [資源管理單元測試 (英文)](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-mgmt/tests)

## <a name="support"></a>支援

SDK 的 Git 存放庫網址如下：[https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python)。

如果您發現任何問題，或對 SDK 的使用方式有任何疑問，請[在存放庫中提出問題](https://github.com/Azure/azure-sdk-for-python/issues)。
