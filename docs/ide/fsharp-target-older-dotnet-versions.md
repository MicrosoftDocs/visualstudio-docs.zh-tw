---
title: 針對 F# 以舊版 .NET Framework 為目標
description: 了解在 Visual Studio 中使用 F# 時，如何以舊版 .NET Framework 為目標。
ms.date: 07/11/2018
ms.topic: troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
monikerRange: vs-2017
ms.openlocfilehash: fe9d87a5cdea04251d7ab30b6e9e0fed6b0c4b31
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99945522"
---
# <a name="target-older-versions-of-net-f"></a>以舊版 .NET 為目標 (F#)

如果您在 Windows 8.1 上安裝了 Visual Studio 時，嘗試於 F# 專案中以 .NET Framework 2.0、3.0 或 3.5 為目標，則可能會出現下列錯誤：

**此專案需要 2.0 的　F# 執行階段，但並未安裝該執行階段。**

在下列條件組合下，已知會發生此錯誤：

- 在 Windows 8.1 上安裝了 Visual Studio。

- 在安裝 Visual Studio 之前，未啟用 .NET Framework 3.5。

- 您的專案以 .NET Framework 2.0、3.0 或 3.5 為目標。

當您安裝 Visual Studio 時，它會偵測已安裝的 .NET Framework 版本。 只有在已安裝並啟用 .NET Framework 3.5 時，Visual Studio 才會安裝 F# 2.0 執行階段。

## <a name="resolve-the-error"></a>解決錯誤

若要解決這個錯誤，您可以執行下列其中一項：

- 以較新版本的 .NET Framework 為目標。

- 在 Windows 8.1 上啟用 .NET Framework 3.5，然後透過修復 Visual Studio 安裝來安裝 F# 2.0 執行階段。 執行此動作的步驟如下。

### <a name="to-enable-the-net-framework-35-on-windows-81"></a>在 Windows 8.1 上啟用 .NET Framework 3.5

1. 在 [開始] 畫面上鍵入 **控制台**。

   當您鍵入時，**控制台** 圖示會出現在 [應用程式] 標題下方。

2. 選擇 **控制台** 圖示，選擇 **程式集** 圖示，然後選擇 [開啟或關閉 Windows 功能] 連結。

3. 確定已選取 [.NET Framework 3.5 (含 .NET 2.0 及 3.0)] 核取方塊，然後選擇 [確定] 按鈕。 您不需要為 .NET Framework 選用元件的任何子節點選取核取方塊。

   如果尚未啟用 .NET Framework 3.5，則會加以啟用。

### <a name="to-install-the-f-20-runtime"></a>安裝 F# 2.0 執行階段

請遵循[修復 Visual Studio 的步驟](../install/repair-visual-studio.md)。

## <a name="see-also"></a>另請參閱

- [F# 指南 (.NET Framework)](/dotnet/fsharp/)
- [Visual Studio 中的 F#](fsharp-visual-studio.md)
