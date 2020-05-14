---
title: 選項、Windows Form 設計工具、一般
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.General
helpviewer_keywords:
- Windows Forms Designer options
- Options dialog box, Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 2a72b27dc2277501d0e0957c8b89b551f4d6852d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568057"
---
# <a name="options-dialog-box-windows-forms-designer"></a>選項對話方塊：Windows 表單設計器

[Windows Form 設計工具] 選項頁面可讓您在 Visual Studio 中設定 Windows Form 設計工具的格線和其他功能的喜好設定。 從 [工具]**** 功能表，開啟 [選項]**** 對話方塊。

## <a name="code-generation-settings"></a>程式碼產生設定

**優化代碼生成**\
啟用最佳化程式碼產生。 有些控制項可能與此模式不相容。 若要讓此變更生效，必須關閉並重新開啟 Visual Studio。

## <a name="high-dpi-support"></a>高 DPI 支援

**DPI 縮放通知**\
在 Windows Form 設計工具中顯示能以 100% 縮放比例重新啟動 Visual Studio 的訊息。 如需詳細資訊，請參閱[停用 Visual Studio 中的 DPI 感知](/dotnet/framework/winforms/disable-dpi-awareness-visual-studio)。

## <a name="layout-settings"></a>配置設定

**預設網格儲存格大小**\
設定設計工具上水平和垂直格線之間的間距 (以像素為單位)。 預設大小為 8, 8。 大小上限為 200, 200。

**佈局模式**\
指定用於配置的對齊系統。 您可以選擇 [SnapToGrid] 或 [對齊線]。

**顯示網格**\
指定設計工具是否顯示調整大小的格線。 根據預設，格線為開啟。

**對齊到網格**\
決定設計工具是否會將物件和控制項貼齊至格線。 換句話說，開啟此功能時，在設計工具上對元素進行調整大小與移動都會受到 GridSize 增量的限制。 啟用 [SnapToGrid] 可讓您更輕鬆地對齊使用者介面的各種層面，但會限制可放置控制項的自由度。 根據預設，[SnapToGrid] 為開啟。

## <a name="object-bound-smart-tag-settings"></a>物件繫結智慧標籤設定

**自動打開智慧標籤**\
決定控制項和元件是否顯示智慧標籤。 並非所有控制項和元件都支援智慧標籤。

## <a name="refactoring"></a>Refactoring

**在重命名時啟用重構**\
當設定為 `true` 時，系統會在您從 [屬性] 視窗或 [文件大綱] 視窗中重新命名元件時執行重新命名重構作業。

## <a name="toolbox"></a>工具箱

**自動填滿工具箱**\
決定 [工具箱] 視窗是否會自動填入專案所建置的元件和控制項。
