---
title: 工作流程設計工具： Debug XAML
description: 瞭解如何在 XAML 中定義工作流程，以及如何使用工作流程設計工具來對 XAML 進行 debug。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 78141b6f3c33903603d7cbb082eca6de55ee757c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971657"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>HOW TO：使用工作流程設計工具偵測 XAML

工作流程是根據 XAML 所定義的。 工作流程的 UI 呈現方式，乃是建立在定義該工作流程的 XAML 樹狀結構上。 偵錯工具的體驗類似于工作流程設計工具中的偵錯工具工作流程。 例如，在偵錯工具時，[區域變數]、[監看式] 和 [執行緒] 視窗的運作方式與工作流程設計工具偵錯工具一樣。 此外，在 XAML 偵錯期間的呼叫堆疊檢視，也是工作流程執行流程的逐行階層架構檢視。

> [!NOTE]
> 如果為工作流程的 XAML 與活動位於同一個組件中，則不會包含類別名稱中的組件部分。 如果沒有類別的這個部分 (活動) 名稱，就無法在執行時間載入 XAML。 不建議在與主要專案的同一個命名空間中定義活動，否則，XAML 在設計工具中編輯之後必須手動編輯。

## <a name="to-debug-workflow-xaml"></a>若要進行工作流程 XAML 偵錯

1. 在 Visual Studio 中開啟工作流程或活動專案。

2. 在活動或您想要進行調試的活動上設定中斷點，如 [如何：在工作流程中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)所述。

3. 以滑鼠右鍵按一下包含您工作流程定義的 .xaml 檔案，然後選取 [ **View Code**]。 在設計檢視中設定中斷點的活動之後，您會看到該活動 XAML 項目宣告的同一行上顯示中斷點。

4. 叫用偵錯工具，如 [Debug 工作流程](debugging-workflows-with-the-workflow-designer.md)中所述。

5. 當程式碼執行到您的其中一個中斷點時，該中斷點關聯的 XAML 項目會出現醒目顯示。 若要移至下一個中斷點，請使用 **F10** 或 **F11** 鍵。

## <a name="see-also"></a>另請參閱

- [如何：在工作流程中設定中斷點](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [偵錯工作流程](debugging-workflows-with-the-workflow-designer.md)
