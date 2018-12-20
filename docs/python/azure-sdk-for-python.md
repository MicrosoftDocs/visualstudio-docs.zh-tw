---
title: Azure SDK for Python
description: 適用於 Python 的 Azure SDK 可讓您更輕鬆地從在任何平台上執行的 Python 應用程式取用 Microsoft Azure 服務。
ms.date: 12/06/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
- azure
ms.openlocfilehash: b9c8f5193e55d86ea4ff5e4d68fb7a66a1044d2e
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062880"
---
# <a name="consume-azure-services-using-the-azure-sdk-for-python"></a>使用 Azure SDK for Python 自訂 Azure 服務

Azure SDK for Python 可讓您更輕鬆地從 Windows、MacOS 和 Linux 上所執行的應用程式使用及管理 Microsoft Azure 服務。

## <a name="installation"></a>安裝

Azure SDK 是從 [Python 封裝索引 (英文)](https://pypi.python.org/pypi/azure) 安裝。

如下所示安裝**最新的穩定版本** (支援 Python 2.7 與 3.x 或更新版本)：

```command
pip install azure
```

您也可以遵循 Azure 文件中的[安裝 Python 和 SDK](https://docs.microsoft.com/azure/python-how-to-install/)。

## <a name="documentation"></a>文件

[適用於 Python 的 Azure SDK 開發人員中心](https://docs.microsoft.com/python/azure/?view=azure-python)也有一些實用的資源，其中包括數個教學課程：

- [在 Linux 的 Azuyre App Service 上建立 Web 應用程式](/azure/app-service/containers/quickstart-python)。
- [Blob 儲存體](/azure/storage/blobs/storage-quickstart-blobs-python)
- [表格儲存體](/azure/cosmos-db/table-storage-how-to-use-python)
- [佇列儲存體](/azure/storage/storage-python-how-to-use-queue-storage)
- [Azure Cosmos DB](/azure/cosmos-db/sql-api-python-application)
- [服務匯流排佇列](/azure/service-bus-messaging/service-bus-python-how-to-use-queues)
- [服務匯流排主題/訂用帳戶](/azure/service-bus-messaging/service-bus-python-how-to-use-topics-subscriptions)
- [服務管理](/azure/cloud-services/cloud-services-python-how-to-use-service-management)

對於沒有文件的公用 API，[SDK GitHub 存放庫](https://github.com/Azure/azure-sdk-for-python) \(英文\) 中的單元測試是很好的資訊來源：

- [儲存體單元測試 (英文)](https://github.com/Azure/azure-storage-python/tree/master/tests)
- [服務匯流排單元測試 (英文)](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicebus/tests)
- [服務管理單元測試](https://github.com/Azure/azure-sdk-for-python/tree/master/azure-servicemanagement-legacy/tests)

## <a name="support"></a>支援

SDK 的 GitHub 存放庫位於 [https://github.com/Azure/azure-sdk-for-python](https://github.com/Azure/azure-sdk-for-python)。

如果您發現任何問題，或對 SDK 的使用方式有任何疑問，請[在存放庫中提出問題](https://github.com/Azure/azure-sdk-for-python/issues)。
