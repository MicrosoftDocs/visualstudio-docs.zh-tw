---
title: .NET Core 支援
description: 本文件涵蓋 Visual Studio for Mac 中所支援的 .NET Core 版本
author: sayedihashimi
ms.author: sayedha
ms.date: 01/08/2020
ms.assetid: 8B8CEBE8-00DA-4AD1-8193-77F58B57F244
ms.openlocfilehash: 6a4bc5a68a17bf3562e0f82b1f2c521f9b3f3e72
ms.sourcegitcommit: d04441e3c5f2eff3a63f7aca35ccf7ecac90fb44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75735801"
---
# <a name="net-core-support"></a>.NET Core 支援

下表描述由 Visual Studio for Mac 的穩定版本和預覽版本所支援的 .NET Core 版本：

| .NET Core SDK 版本 |Visual Studio for Mac 8.1 (穩定) | Visual Studio for Mac 8.2 (穩定) | Visual Studio for Mac 8.3 （穩定） | Visual Studio for Mac 8.4 （穩定）
|---------|---------|---------|---------|---------|
|v2.1.0 - v2.1.5xx | | | | |
|v2.1.600 + |✔︎|✔︎|✔︎|✔︎|
|v2.2.1 - v2.2.1xx | | | | |
|v2.2.200 + |✔︎|✔︎|✔︎|✔︎|
|v3.0 | | |✔︎|✔︎|
|v3.1 | | | |✔︎|

> [!IMPORTANT]
> 不支援 .NET Core SDK 的預覽版本;請更新為發行版本。 安裝 Visual Studio for Mac 8.4 時，將會安裝 .NET Core 3.1 版的已發行版本本。

> [!IMPORTANT]
> 如果您先前使用 .NET Core v2.2.1xx 搭配 Visual Studio for Mac 8.0，則需要手動更新為受支援的 .NET Core 版本，如上表中所列。 建議您使用 [2.1.700](https://dotnet.microsoft.com/download/dotnet-core/2.1) \(英文\) 或 [2.2.300](https://dotnet.microsoft.com/download/dotnet-core/2.2) \(英文\)

* 8\.4 預設會安裝 .NET Core 3.1 版。
* 8\.3 預設會安裝 .NET Core v3.0。
* 安裝程式預設會安裝 .NET Core v2.1.701 (如果是 8.1 則會安裝 v2.1.700)。
* 若要下載 .NET Core 的任何其他版本，請造訪 [dotnet 頁面](https://dotnet.microsoft.com/download/dotnet-core) \(英文\)。
* 使用 .NET Core 3.0 時， C#預設會使用第8版。 C#7.3 是使用 .NET Core 2.x 時的預設值。 如需詳細資訊，請參閱[ C#語言版本](/dotnet/csharp/language-reference/configure-language-version)設定。
* 如需安裝 Visual Studio for Mac 預覽版本的相關資訊，請參閱[安裝預覽版本](/visualstudio/mac/install-preview)指南。
