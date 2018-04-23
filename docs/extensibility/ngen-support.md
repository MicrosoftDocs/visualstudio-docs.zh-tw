---
title: VSIX v3 Ngen 支援 |Microsoft 文件
ms.custom: ''
ms.date: 11/09/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 1472e884-c74e-4c23-9d4a-6d8bdcac043b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 146df23bff14bd93558c645521f99f6099a49bde
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="ngen-support-in-vsix-v3"></a>Ngen VSIX v3 支援

使用 Visual Studio 2017 和新的 VSIX v3 （第 3 版） 延伸模組資訊清單的格式，現在擴充功能開發人員可以"ngen 」 它們的組件，在安裝期間。

以下是摘錄自 MSDN 說明哪些"ngen 」 並：

>原生映像產生器 (Ngen.exe) 是一種可以增進 Managed 應用程式效能的工具。 Ngen.exe 會建立原生映像，也就是包含已編譯之處理器特定機器碼的檔案，然後將原生映像安裝到本機電腦上的原生映像快取中。 執行階段就可以從快取中使用原生映像，而不是使用 Just-In-Time (JIT) 編譯器來編譯原始組件。
>
>從[Ngen.exe （原生映像產生器）](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx)

為了"ngen"組件，VSIX 必須安裝 「 個別執行個體每台機器 」。 這可以藉由檢查 extension.vsixmanifest 設計工具中的"all users"核取方塊啟用：

![檢查所有使用者](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>如何啟用 Ngen

若要啟用組件的 ngen，您可以使用**屬性**Visual Studio 中的視窗。

有 4 個可設定的屬性：

1. **Ngen** （布林值）-如果為 true，Visual Studio 安裝程式會將"ngen"組件。
2. **Ngen 應用程式**（字串）-Ngen 提供機會使用應用程式的 app.config 檔案以解析組件相依性。 這個值應該設定至您想要使用 （相對於 Visual Studio 安裝目錄） 的 app.config 應用程式。
3. **Ngen 架構**（列舉）-原生方式編譯組件的架構。 選項包括：。 NotSpecified b。 X86 c。 X64 d。 全部
4. **Ngen 優先順序**（介於 1 到 3 之間的整數）-Ngen 優先權層級已記錄在[Ngen.exe 優先權等級](https://msdn.microsoft.com/en-us/library/6t9t5wcf(v=vs.110).aspx#Anchor_3)。

以下就來看看**屬性** 視窗中的動作：

![ngen 內容中](media/ngen-in-properties.png)

這會將中繼資料加入至 VSIX 專案.csproj 檔案內的專案參考：

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

 >**注意：**您可以編輯.csproj 檔案直接，如果您偏好。

## <a name="extra-information"></a>額外的資訊

將屬性設計工具變更套用到不只是專案參考。您可以設定項目的 Ngen 中繼資料，以及您的專案內 （使用上面所述的相同方法） 的項目是.NET 組件一樣長。