---
title: MSBuild 目標 Framework 和目標平台 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c55ce57adb5b86941b5953732d57a642eb4f943
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350832"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild 目標 Framework 和目標平台

您可以建置專案，以在特定 .NET Framework 版本的「目標 Framework」**，以及特定軟體架構的「目標平台」** 上執行。  例如，您可以將應用程式設為目標，以便在與80x86 處理器系列（"x86"）相容的32位平臺上，于 .NET Framework 2.0 上執行。 目標 Framework 和目標平台的組合稱為「目標內容」**。

> [!IMPORTANT]
> 本文說明指定目標 Framework 的舊方式。 SDK 樣式專案可啟用不同的 TargetFrameworks，例如 netstandard。 如需詳細資訊，請參閱[目標 Framework](/dotnet/standard/frameworks)。

## <a name="target-framework-and-profile"></a>目標 Framework 和設定檔

 目標 Framework 是專案被建置來於其上執行的特定 .NET Framework 版本。 由於目標 Framework 啟用由該版 Framework 獨佔的編譯器功能和組件參考，因此需要目標 Framework 的規格。

 以下是目前可供使用的 .NET Framework 版本：

- .NET Framework 2.0 (包含在 Visual Studio 2005 中)

- .NET Framework 3.0 （包含在 Windows Vista 中）

- .NET Framework 3.5 （包含在 Visual Studio 2008）

- .NET Framework 4.5.2

- .NET Framework 4.6 （包含在 Visual Studio 2015）

- .NET Framework 4.6.1

- .NET Framework 4.6.2

- .NET Framework 4.7

- .NET Framework 4.7.1

- .NET Framework 4.7.2

- .NET Framework 4.8

組件清單中每一個組件所參考的 .NET Framework 版本各自不同。 例如，除非您專案是以 .NET Framework 3.0 (含) 以上版本為目標，否則您無法建置 Windows Presentation Foundation (WPF) 應用程式。

目標 Framework 是在專案檔的 `TargetFrameworkVersion` 屬性中指定。 您可以在 Visual Studio 整合式開發環境 (IDE) 中，使用專案屬性頁來變更專案的目標 Framework。 如需詳細資訊，請參閱[如何：以 .NET Framework 版本為目標](../ide/visual-studio-multi-targeting-overview.md)。 `TargetFrameworkVersion` 的可用值包括 `v2.0`、`v3.0`、`v3.5`、`v4.5.2`、`v4.6`、`v4.6.1`、`v4.6.2`、`v4.7`、`v4.7.1`、`v4.7.2` 和 `v4.8`。

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 「目標設定檔」** 是目標 Framework 的子集。 例如，.NET Framework 4 用戶端設定檔不包含 MSBuild 組件的參考。

 > [!NOTE]
 > 目標設定檔僅適用于[可移植的類別庫](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library)。

 目標設定檔是在專案檔的 `TargetFrameworkProfile` 屬性中指定。 您可以在 IDE 中，使用專案屬性頁中的目標 Framework 控制項來變更目標設定檔。

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>目標平台

 「平台」** 是定義特定執行階段環境的軟硬體組合。 例如，

- `x86` 指定在 Intel 80x86 處理器或其對等項目上執行的 32 位元 Windows 作業系統。

- `x64` 指定在 Intel x64 處理器或其對等項目上執行的 64 位元 Windows 作業系統。

- `Xbox` 指定 Microsoft Xbox 360 平台。

「目標平台」** 是建置專案以在其上方執行的目標特定平台。 目標平台是在專案檔的 `PlatformTarget` 建置屬性中指定。 您可以在 IDE 中，使用專案屬性頁或 [組態管理員]**** 來變更目標平台。

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

「目標組態」** 是目標平台的子集。 例如，`x86` `Debug` 組態不包含大部分的程式碼最佳化。 目標組態是在專案檔的 `Configuration` 建置屬性中指定。 您可以使用專案屬性頁或 [組態管理員]**** 來變更目標組態。

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
</PropertyGroup>

```

## <a name="see-also"></a>另請參閱

- [多目標](../msbuild/msbuild-multitargeting-overview.md)
