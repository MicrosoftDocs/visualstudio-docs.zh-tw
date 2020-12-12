---
title: Modeling SDK for Visual Studio - 網域指定的語言
description: 您可以使用模型化 SDK 進行 Visual Studio，以建立功能強大的模型型開發工具，讓您可以整合到 Visual Studio。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a032e5f6b3f9eda302f65a4d04b196ef55a225f6
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360776"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modeling SDK for Visual Studio - 網域指定的語言

您可以使用模型化 SDK 進行 Visual Studio，建立功能強大的模型式開發工具，以便整合到 Visual Studio。 同樣地，您可以建立一個或多個模型定義，並將這些定義整合成一組工具。

MSDK 的核心就是模型定義，您可建立模型定義代表商業領域的概念。 您可以使用各種不同的工具來括住模型，例如圖表 view、產生程式碼和其他成品的能力、用於轉換模型的命令，以及在 Visual Studio 中與程式碼和其他物件互動的能力。 當您開發模型時，可以將它與其他模型和工具組合成強大的工具組，做為開發工作的重心。

MSDK 可讓您透過網域指定的語言 (DSL) 的形式迅速開發模型。 一開始是使用專用的編輯器一併定義結構描述或抽象語法與圖形標記法。 VMSDK 會從這個定義產生：

- 模型實作，這個實作具有在交易為基礎的存放區中執行的強類型 API。

- 樹狀檔案總管。

- 圖形編輯器，使用者可在這個編輯器中檢視您定義的模型或模型的一部分。

- 序列化方法，這類方法會將模型儲存為可讀取的 XML。

- 使用文字範本化產生程式碼和其他成品的功能。

您可以自訂及擴充這些功能。 您的擴充功能會進行整合，整合後仍然可以更新 DSL 定義和重新產生功能，而不會遺失您的擴充功能。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[相關部落格文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
