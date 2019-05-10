---
title: Modeling SDK for Visual Studio - 網域指定的語言
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b955dc6f79c689ca30d8d9876d0888b14127490
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476522"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modeling SDK for Visual Studio - 網域指定的語言

藉由使用 Modeling SDK for Visual Studio 中，您可以建立功能強大的模型為基礎的開發工具，您可以整合到 Visual Studio。 同樣地，您可以建立一個或多個模型定義，並將這些定義整合成一組工具。

MSDK 的核心就是模型定義，您可建立模型定義代表商業領域的概念。 您可以用各種不同的工具，例如圖表檢視，讓您產生程式碼和其他成品，轉換模型的命令和程式碼和 Visual Studio 中的其他物件互動的功能使用的模型。 當您開發模型時，可以將它與其他模型和工具組合成強大的工具組，做為開發工作的重心。

MSDK 可讓您透過網域指定的語言 (DSL) 的形式迅速開發模型。 一開始是使用專用的編輯器一併定義結構描述或抽象語法與圖形標記法。 VMSDK 會從這個定義產生：

- 模型實作，這個實作具有在交易為基礎的存放區中執行的強類型 API。

- 樹狀檔案總管。

- 圖形編輯器，使用者可在這個編輯器中檢視您定義的模型或模型的一部分。

- 序列化方法，這類方法會將模型儲存為可讀取的 XML。

- 使用文字範本化產生程式碼和其他成品的功能。

您可以自訂及擴充這些功能。 您的擴充功能會進行整合，整合後仍然可以更新 DSL 定義和重新產生功能，而不會遺失您的擴充功能。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[相關部落格文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)