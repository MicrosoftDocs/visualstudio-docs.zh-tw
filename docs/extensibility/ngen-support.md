---
title: VSIX v3 中的 Ngen 支援 |微軟文件
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cb75b9256ca937106235fa7a7d66d9cec71c9c60
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702405"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3 中的 Ngen 支援

借助 Visual Studio 2017 和新的 VSIX v3(版本 3)擴展清單格式,擴展開發人員現在可以在安裝時「ngen」其程式集。

以下是 MSDN 的摘錄,其中解釋了「ngen」的作用:

>這個機映像產生器 (*Ngen.exe)* 是提高託管應用程式效能的工具. *Ngen.exe*創建本機映像,這些映射包含編譯的特定於處理器的計算機代碼,並將它們安裝到本地電腦上的本機映射緩存中。 執行階段就可以從快取中使用原生映像，而不是使用 Just-In-Time (JIT) 編譯器來編譯原始組件。
>
>來自[Ngen.exe(本機影像產生器)](/dotnet/framework/tools/ngen-exe-native-image-generator)

為了"ngen"一個元件,VSIX 必須安裝"每台計算機的實例"。 這可以通過選取`extension.vsixmanifest`的設計器中的「所有使用者」複選框來啟用:

![檢查所有使用者](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>如何開啟 Ngen

要為程式集啟用 ngen,可以使用 Visual Studio 中的 **「屬性**」視窗。

可以設定 4 個屬性:

1. **Ngen** (布林) - 如果為 true,Visual Studio 安裝程式將"ngen"程式集。
2. **Ngen 應用程式**(字串) - Ngen 提供了使用應用程式*的應用程式.config*檔案來解決程式集依賴項的機會。 此值應設定為要使用*的應用程式。* 相對於 Visual Studio 安裝目錄)。
3. **Ngen 架構結構**(枚舉) - 用於本機編譯程式集的體系結構。 選項是: a. 沒有指定 b. X86 c. X64 d. 全部
4. **Ngen 優先權**(介於 1 和 3 之間的整數) - Ngen 優先順序等級記錄在[Ngen.exe 優先權](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)等級。

下面是 **「屬性**」 視窗的操作:

![ngen 屬性](media/ngen-in-properties.png)

這將在 VSIX 專案的 *.csproj*檔內向專案引用新增中繼資料:

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
> 如果您願意,可以直接編輯 .csproj 檔。

## <a name="extra-information"></a>額外資訊

屬性設計器更改不僅適用於專案引用,還應用於專案引用。只要專案是 .NET 程式集,也可以為專案內的項設置 Ngen 元數據(使用上述相同的方法)。
