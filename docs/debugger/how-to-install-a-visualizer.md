---
title: 如何：安裝視覺化檢視 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 1df72c6978f5ab34a86c74dbc1ea349db5aa4457
ms.sourcegitcommit: b5cb0eb09369677514ee1f44d5d7050d34c7fbc1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74491301"
---
# <a name="how-to-install-a-visualizer"></a>如何：安裝視覺化檢視
建立視覺化檢視後，您必須安裝該視覺化檢視，使 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以使用它。 安裝視覺化檢視的程序很簡單。

> [!NOTE]
> 在 UWP 應用程式中，只支援標準文字、HTML、XML 和 JSON 視覺化檢視。 不支援自訂 (使用者建立的) 視覺化檢視。

### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>安裝 Visual Studio 2019 的視覺化程式
  
1. 找出包含您已建置之視覺化檢視的 DLL。

2. 將[偵錯工具端](create-custom-visualizers-of-data.md#to-create-the-debugger-side)DLL 複製到下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. 將[調試的端](create-custom-visualizers-of-data.md#to-create-the-debuggee-side)DLL 複製到下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers\`*架構*

    - `My Documents\` *VisualStudioVersion* `\Visualizers\`*架構*

    其中的*架構*為：
    - 執行 `.NET Framework` 執行時間的 debuggees `net2.0`。
    - `netstandard2.0` 使用支援 `netstandard 2.0` （`.NET Framework v4.6.1+` 或 `.NET Core 2.0+`）的執行時間進行 debuggees。
    - 執行 `.NET Core` 執行時間的 debuggees `netcoreapp`。 （支援 `.NET Core 2.0+`）

4. 重新啟動偵錯工作階段。

### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>安裝 Visual Studio 2017 和較舊版本的視覺化程式

> [!IMPORTANT]
> 只有 Visual Studio 2017 和更舊版本才支援 .NET Framework 的視覺化檢視

1. 找出包含您已建置之視覺化檢視的 DLL。

2. 將該 DLL 複製至下列其中一個位置：

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`

3. 重新啟動偵錯工作階段。

> [!NOTE]
> 如果要使用 Managed 視覺化檢視進行遠端偵錯，請將 DLL 複製到遠端電腦上的相同路徑中。

## <a name="see-also"></a>請參閱
- [建立自訂視覺化檢視](../debugger/create-custom-visualizers-of-data.md)
- [如何：撰寫視覺化檢視](create-custom-visualizers-of-data.md)
