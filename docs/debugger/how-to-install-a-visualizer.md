---
title: 如何-安裝視覺化檢視 |Microsoft Docs
ms.date: 06/10/2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b070eb361bcc3fbe4f72adfff10b5e7d19649087
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2020
ms.locfileid: "85349558"
---
# <a name="how-to-install-a-visualizer"></a>如何：安裝視覺化檢視
建立視覺化檢視後，您必須安裝該視覺化檢視，使 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以使用它。 安裝視覺化檢視的程序很簡單。

> [!NOTE]
> 在 UWP 應用程式中，只支援標準文字、HTML、XML 和 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>安裝 Visual Studio 2019 的視覺化程式
  
1. 找出包含您所建立之視覺化檢視的 DLL。

   通常，如果偵錯工具端 DLL 和偵錯工具端 DLL 都指定**任何 CPU**做為目標平臺，這是最佳的做法。 偵錯工具端 DLL 必須是**任何 CPU**或**32 位**。 偵錯工具端 DLL 的目標平臺應該對應至偵錯專案進程。

2. 將[偵錯工具端](create-custom-visualizers-of-data.md#to-create-the-debugger-side)DLL （以及它所依賴的任何 dll）複製到下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. 將[調試的端](create-custom-visualizers-of-data.md#to-create-the-visualizer-object-source-for-the-debuggee-side)DLL 複製到下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\`*架構*

    - `My Documents\`*VisualStudioVersion* `\Visualizers\`*架構*

    其中的*架構*為：
    - `net2.0`適用于執行執行時間的 debuggees `.NET Framework` 。
    - `netstandard2.0`適用于使用支援的執行時間 `netstandard 2.0` （ `.NET Framework v4.6.1+` 或 `.NET Core 2.0+` ）的 debuggees。
    - `netcoreapp`適用于執行執行時間的 debuggees `.NET Core` 。 （支援 `.NET Core 2.0+` ）

   如果您想要建立獨立的視覺化檢視，則需要調試層端 DLL。 這個 DLL 包含資料物件的程式碼，可執行檔方法 <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource> 。

   如果您有多個目標物件端程式碼，則必須將偵錯工具端 DLL 放入資料夾中，以獲得最低支援的 TFM。

4. 重新啟動偵錯工作階段。

> [!NOTE]
> Visual Studio 2017 和更舊版本中的程式不同。 請參閱本文的[先前版本](how-to-install-a-visualizer.md?view=vs-2017)。
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>安裝 Visual Studio 2017 和較舊版本的視覺化程式

> [!IMPORTANT]
> 只有 Visual Studio 2017 和更舊版本才支援 .NET Framework 的視覺化檢視。

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
