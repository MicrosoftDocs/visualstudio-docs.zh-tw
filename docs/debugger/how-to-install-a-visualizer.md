---
title: 如何:安裝可視化工具 |微軟文件
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
ms.openlocfilehash: 499d644cc8374b070cedaf058b0e4dc17d155bdc
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880256"
---
# <a name="how-to-install-a-visualizer"></a>如何：安裝視覺化檢視
建立視覺化檢視後，您必須安裝該視覺化檢視，使 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中可以使用它。 安裝視覺化檢視的程序很簡單。

> [!NOTE]
> 在 UWP 應用程式中,僅支援標準文本、HTML、XML 和 JSON 視覺化工具。 不支援自訂 (使用者建立的) 視覺化檢視。

::: moniker range=">=vs-2019"
### <a name="to-install-a-visualizer-for-visual-studio-2019"></a>為 Visual Studio 2019 安裝視覺化工具
  
1. 找到包含您建置的視覺化工具的 DLL。

   通常,最好調試器端 DLL 和調試器端 DLL 都指定**任何 CPU**作為目標平臺。 除錯器端 DLL 必須是任何**CPU**或**32 位**元 。 調試端 DLL 的目標平台應對應於調試器過程。

2. 將[除錯器端](create-custom-visualizers-of-data.md#to-create-the-debugger-side)DLL(及其所依賴的任何 DLL)複製到以下任一位置:

    - *VisualStudioInstallPath* `\Common7\Packages\Debugger\Visualizers`

    - `My Documents\` *VisualStudioVersion* `\Visualizers`
    
3. 將[除錯基端](create-custom-visualizers-of-data.md#to-create-the-debuggee-side)DLL 複製到以下任一位置:

    - *視覺化工作室安裝路徑*`\Common7\Packages\Debugger\Visualizers\`*架構*

    - `My Documents\`*視覺化工作室版本*`\Visualizers\`*框架*

    *框架*可以是:
    - `net2.0`用於運行運行時的`.NET Framework`調試器。
    - `netstandard2.0`用於使用支援`netstandard 2.0`(`.NET Framework v4.6.1+``.NET Core 2.0+`或 ) 的執行時的除錯器。
    - `netcoreapp`用於運行運行時的`.NET Core`調試器。 (`.NET Core 2.0+`支援 )

4. 重新啟動偵錯工作階段。

> [!NOTE]
> 在 Visual Studio 2017 及更高級版中,該過程有所不同。 請參考本文[的早期版本](how-to-install-a-visualizer.md?view=vs-2017)。
::: moniker-end

::: moniker range="vs-2017"
### <a name="to-install-a-visualizer-for-visual-studio-2017-and-older"></a>為 Visual Studio 2017 及更進階版安裝視覺化工具

> [!IMPORTANT]
> Visual Studio 2017 及更舊版僅支援 .NET 框架可視化工具。

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
