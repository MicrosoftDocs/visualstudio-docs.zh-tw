---
title: VSIX v3 中的 Ngen 支援 |Microsoft Docs
description: 瞭解如何啟用原生映射產生器，這是延伸模組開發人員可用來改善受控應用程式效能的工具。
ms.custom: SEO-VS-2020
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 064176a0a28e3621e796bf60ede552f9cda155b0
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864027"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3 中的 Ngen 支援

在 Visual Studio 2017 和新的 VSIX v3 (第3版) 延伸模組資訊清單格式中，延伸模組開發人員現在可以在安裝時將其元件「ngen」。

以下是 MSDN 的摘錄，說明 "ngen" 的功能：

>原生映射產生器 (*Ngen.exe*) 是改善受控應用程式效能的工具。 *Ngen.exe* 會建立原生映射，也就是包含已編譯之處理器特定機器碼的檔案，並將它們安裝在本機電腦上的原生映射快取中。 執行階段就可以從快取中使用原生映像，而不是使用 Just-In-Time (JIT) 編譯器來編譯原始組件。
>
>從[Ngen.exe (原生映射](/dotnet/framework/tools/ngen-exe-native-image-generator)產生器) 

為了「ngen」元件，必須將 VSIX 安裝為「每個實例的每部電腦」。 您可以勾選設計工具中的 [所有使用者] 核取方塊來啟用此功能 `extension.vsixmanifest` ：

![檢查所有使用者](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>如何啟用 Ngen

若要為元件啟用 ngen，您可以使用 Visual Studio 中的 [ **屬性** ] 視窗。

可以設定的屬性有4個：

1. **Ngen** (布林值) -如果為 true，Visual Studio 安裝程式會將 "Ngen" 設為元件。
2. **Ngen 應用程式** (字串) -Ngen 提供了一個機會，可以使用應用程式的 *app.config* 檔來解析元件相依性。 此值應該設定為您想要使用 *app.config* (相對於 Visual Studio 安裝目錄) 的應用程式。
3. **Ngen 架構** (enum) -以原生方式編譯元件的架構。 選項為： a。 NotSpecified b。 X86 c。 X64 d。 全部
4. **Ngen 優先權** (介於1和 3) 之間的整數-ngen 優先權層級記載于 [Ngen.exe 優先權層](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)級。

以下就來看看 [ **屬性** ] 視窗的作用：

![屬性中的 ngen](media/ngen-in-properties.png)

這會將中繼資料加入至 VSIX 專案 *.csproj* 檔案內的專案參考：

```xml
 <ProjectReference Include="..\ClassLibrary1\ClassLibrary1.csproj">
    <Project>{69a979f1-eba2-43e7-9346-0e56e803508b}</Project>
    <Name>ClassLibrary1</Name>
    <Ngen>True</Ngen>
    <NgenApplication>vsn.exe</NgenApplication>
    <NgenArchitecture>X86</NgenArchitecture>
    <NgenPriority>2</NgenPriority>
</ProjectReference>
```

> [!NOTE]
> 如果您想要的話，也可以直接編輯 .csproj 檔案。

## <a name="extra-information"></a>額外資訊

屬性設計工具變更只適用于專案參考;只要專案是 .NET 元件，您也可以使用) 上述的相同方法，來設定專案內專案的 Ngen 中繼資料 (。
