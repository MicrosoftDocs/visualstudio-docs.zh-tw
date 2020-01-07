---
title: Modeling SDK for Visual Studio - 網域指定的語言
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
ms.openlocfilehash: 2abb209943ff14969f71ebdca6982020f30a5d47
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/01/2020
ms.locfileid: "75590198"
---
# <a name="modeling-sdk-for-visual-studio---domain-specific-languages"></a>Modeling SDK for Visual Studio - 網域指定的語言

藉由使用 Visual Studio 的模型 SDK，您可以建立功能強大的模型型開發工具，讓您可以將其整合到 Visual Studio。 同樣地，您可以建立一個或多個模型定義，並將這些定義整合成一組工具。

MSDK 的核心就是模型定義，您可建立模型定義代表商業領域的概念。 您可以使用各種工具（例如圖表視圖）來括住模型、產生程式碼和其他成品的功能、用於轉換模型的命令，以及與 Visual Studio 中的程式碼和其他物件互動的能力。 當您開發模型時，可以將它與其他模型和工具組合成強大的工具組，做為開發工作的重心。

MSDK 可讓您透過網域指定的語言 (DSL) 的形式迅速開發模型。 一開始是使用專用的編輯器一併定義結構描述或抽象語法與圖形標記法。 VMSDK 會從這個定義產生：

- 模型實作，這個實作具有在交易為基礎的存放區中執行的強類型 API。

- 樹狀檔案總管。

- 圖形編輯器，使用者可在這個編輯器中檢視您定義的模型或模型的一部分。

- 序列化方法，這類方法會將模型儲存為可讀取的 XML。

- 使用文字範本化產生程式碼和其他成品的功能。

您可以自訂及擴充這些功能。 您的擴充功能會進行整合，整合後仍然可以更新 DSL 定義和重新產生功能，而不會遺失您的擴充功能。

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

[相關的 blog 文章](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)
