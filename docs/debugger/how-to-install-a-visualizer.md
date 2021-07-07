---
title: 安裝視覺化 |Microsoft Docs
description: 瞭解如何安裝視覺化檢視，使其可用於 Visual Studio 中的偵錯工具使用。
ms.custom: SEO-VS-2020
ms.date: 07/02/2021
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, visualizers
- visualizers, installing
ms.assetid: 3310ef43-515c-4d97-b0f9-51047247d3da
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 611347acfe48e561653d644097d56d029b6a4fa6
ms.sourcegitcommit: 4cd3eb514e9fa48e586279e38fe7c2e111ebb304
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2021
ms.locfileid: "113298253"
---
# <a name="how-to-install-a-visualizer"></a>如何：安裝視覺化檢視
建立視覺化檢視後，您必須安裝該視覺化檢視，使 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以使用它。 安裝視覺化檢視的程序很簡單。

> [!NOTE]
> 在 UWP 應用程式中，只支援標準文字、HTML、XML 和 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>安裝 Visual Studio 2019 的視覺化程式

1. 找出包含您所建立之視覺化的 DLL。

   一般而言，如果偵錯工具端 DLL 和偵錯工具端 DLL 都指定 **任何 CPU** 做為目標平臺，這是最好的做法。 偵錯工具端 DLL 必須是 **任何 CPU** 或 **32** 位。 偵錯工具端 DLL 的目標平臺應該對應至偵錯工具進程。

   >[!NOTE]
   > 偵錯工具端的視覺化檢視會載入 Visual Studio 進程，因此它必須是 .NET Framework DLL。 偵錯工具端可以是 .NET Framework 或 .NET Standard，視 Visual Studio 中正在進行的進程而定。

2. 將 [偵錯工具端](create-custom-visualizers-of-data.md#to-create-the-debugger-side) DLL (以及相依于) 的任何 dll 複製到下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. 將偵錯工具的 [側邊](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side) DLL 複製到下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\`*架構*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\`*架構*

    其中的 *架構* 為：
    - `net2.0` 適用于執行執行時間的 debuggees `.NET Framework` 。
    - `netstandard2.0` 適用于使用支援 `netstandard 2.0` (或) 之執行時間的 debuggees `.NET Framework v4.6.1+` `.NET Core 2.0+` 。
    - `netcoreapp` 適用于執行執行時間的 debuggees `.NET Core` 。  (支援 `.NET Core 2.0+`) 

   如果您想要建立獨立的視覺化程式，則必須要有偵錯工具端的 DLL。 此 DLL 包含資料物件的程式碼，可執行檔方法 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 。

   如果您要將偵錯工具端程式碼設為多個目標，則必須將偵錯工具端 DLL 放到資料夾中，以獲得最低支援的 TFM。

4. 重新啟動偵錯工作階段。

> [!NOTE]
> Visual Studio 2017 及更舊版本中的程式不同。 請參閱本文的 [先前版本](how-to-install-a-visualizer.md?view=vs-2017&preserve-view=true) 。
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>若要安裝適用于 Visual Studio 2017 及更舊版本的視覺化檢視

> [!IMPORTANT]
> Visual Studio 2017 及更舊版本僅支援 .NET Framework 的視覺化檢視。

1. 找出包含您已建置之視覺化檢視的 DLL。

2. 將該 DLL 複製至下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. 重新啟動偵錯工作階段。

> [!NOTE]
> 如果要使用 Managed 視覺化檢視進行遠端偵錯，請將 DLL 複製到遠端電腦上的相同路徑中。
::: moniker-end

## <a name="see-also"></a>另請參閱
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
- [如何：撰寫視覺化檢視](create-custom-visualizers-of-data.md)
