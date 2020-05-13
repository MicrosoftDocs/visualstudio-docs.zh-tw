---
title: .NET Core 支援
description: 本文件涵蓋 Visual Studio for Mac 中所支援的 .NET Core 版本
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: 6a4bc5a68a17bf3562e0f82b1f2c521f9b3f3e72
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "75735801"
---
# <a name="net-core-support"></a>.NET Core 支援

下表描述由 Visual Studio for Mac 的穩定版本和預覽版本所支援的 .NET Core 版本：

| .NET Core SDK 版本 |Visual Studio for Mac 8.1 (穩定) | Visual Studio for Mac 8.2 (穩定) | 適用于 Mac 8.3 的視覺化工作室（穩定） | 適用于 Mac 8.4 的視覺化工作室（穩定）
|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|
|v3.1 | | | |✔︎|

> [!IMPORTANT]
> 不支援 .NET 核心 SDK 的預覽版本;請更新到已發佈的版本。 安裝適用于 Mac 8.4 的 Visual Studio 時，將安裝 .NET Core v3.1 的發佈版本。

> [!IMPORTANT]
> 如果您先前使用 .NET Core v2.2.1xx 搭配 Visual Studio for Mac 8.0，則需要手動更新為受支援的 .NET Core 版本，如上表中所列。 我們建議[2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1)或[2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2)

* .NET 酷睿 v3.1 預設為 8.4 安裝。
* .NET Core v3.0 預設為 8.3 安裝。
* 安裝程式預設會安裝 .NET Core v2.1.701 (如果是 8.1 則會安裝 v2.1.700)。
* 若要下載 .NET Core 的任何其他版本，請造訪 [dotnet 頁面](https://dotnet.microsoft.com/download/dotnet-core) \(英文\)。
* 使用 .NET Core 3.0 時，預設情況下將使用 C# 版本 8。 使用 .NET 核心 2.x 時，C# 7.3 為預設值。 有關詳細資訊[，請參閱 C# 語言版本控制](/dotnet/csharp/language-reference/configure-language-version)。
* 如需安裝 Visual Studio for Mac 預覽版本的相關資訊，請參閱[安裝預覽版本](/visualstudio/mac/install-preview)指南。
