---
title: VSIX v3 中的 Ngen 支援 |Microsoft Docs
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
ms.openlocfilehash: 3b5f9c7b297d98836ca3e5c017d2a0d440a30470
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495475"
---
# <a name="ngen-support-in-vsix-v3"></a>VSIX v3 中的 Ngen 支援

使用 Visual Studio 2017 和新的 VSIX v3 （第 3 版） 擴充功能資訊清單格式，延伸模組開發人員可以現在"ngen 」 它們的組件，在安裝階段。

以下是摘錄自解釋哪些"ngen 」 用途的 MSDN:

>原生映像產生器 (*Ngen.exe*) 是一種工具，可改善 managed 應用程式的效能。 *Ngen.exe*建立原生映像，這是包含已編譯的處理器特定機器碼，檔案並將它們安裝至本機電腦的原生映像快取。 執行階段就可以從快取中使用原生映像，而不是使用 Just-In-Time (JIT) 編譯器來編譯原始組件。
>
>從[Ngen.exe （原生映像產生器）](/dotnet/framework/tools/ngen-exe-native-image-generator)

為了 「 ngen"的組件，VSIX 必須安裝 「 每個執行個體每台電腦 」。 這可藉由檢查的 [所有使用者] 核取方塊來啟用`extension.vsixmanifest`設計工具：

![檢查所有的使用者](media/check-all-users.png)

## <a name="how-to-enable-ngen"></a>如何啟用 Ngen

若要啟用組件的 ngen，您可以使用**屬性**Visual Studio 中的視窗。

有 4 個可設定的屬性：

1. **Ngen** （布林值）-如果為 true，Visual Studio 安裝程式會 「 ngen"組件。
2. **Ngen 應用程式**（字串）-Ngen 提供使用的應用程式的機會*app.config*檔案以解析組件相依性。 此值應該設定為應用程式其*app.config*您想要使用 （相對於 Visual Studio 安裝目錄中）。
3. **Ngen 架構**（列舉）-原生方式編譯您的組件的架構。 選項包括：。 NotSpecified b。 X86 c。 X64 d。 全部
4. **Ngen 優先順序**（1 到 3 之間的整數）-Ngen 優先權層級已記錄在[Ngen.exe 優先權等級](/dotnet/framework/tools/ngen-exe-native-image-generator#priority-levels)。

以下就來看看**屬性**作用中的視窗：

![ngen 屬性](media/ngen-in-properties.png)

這會將中繼資料加入 VSIX 專案的專案參考 *.csproj*檔案：

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

 >**注意：** 您可以編輯.csproj 檔案直接，如果您偏好。

## <a name="extra-information"></a>額外的資訊

屬性設計工具變更適用於不只是專案參考;您可以在您的專案，以及設定 Ngen 中繼資料的項目 （使用上面所述的相同方法） 只要項目是.NET 組件。