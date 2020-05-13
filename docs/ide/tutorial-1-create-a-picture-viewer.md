---
title: 教學課程 1：建立圖片檢視器
ms.date: 10/16/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f1431d56516c749004cef1b35ada482a6c53446
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/20/2020
ms.locfileid: "77579718"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>教學課程 1：建立圖片檢視器

在本教程中，您將構建一個應用，該應用從檔中載入圖片並將其顯示在視窗中。 您將瞭解如何使用 Windows**表單設計器**將按鈕和圖片框等控制項拖動到表單上，設置其屬性，並使用容器平滑調整表單的大小。 您也會開始撰寫程式碼。

> [!NOTE]
> 本教程將介紹 C# 和 Visual Basic，因此請關注特定于您使用的程式設計語言的資訊。

本教程將引導您完成以下任務：

* 建立新專案。

* 測試 (偵錯) 應用程式。

* 將基本控制項 (例如核取方塊和按鈕) 加入至表單。

* 使用佈局在表單上定位控制項。

* 將 [開啟檔案]**** 和 [色彩]**** 對話方塊新增至表單。

* 使用 IntelliSense 和程式碼片段編寫代碼。

* 撰寫事件處理常式方法。

完成後，你的應用應類似于下圖：

![您在本教程中創建的圖片檢視器應用](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>教學課程的連結

|Title|描述|
|-----------|-----------------|
|[第 1 步：創建 Windows 表單應用專案](../ide/step-1-create-a-windows-forms-application-project.md)|首先創建 Windows 表單應用專案。|
|[第 2 步：運行圖片檢視器應用](../ide/step-2-run-your-program.md)|運行您在上一步中創建的 Windows 表單應用專案。|
|[第 3 步：設置表單內容](../ide/step-3-set-your-form-properties.md)|使用 [屬性]**** 視窗變更表單的外觀。|
|[第 4 步：使用表佈局面板控制項佈局表單](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|新增 `TableLayoutPanel` 控制項至表單。|
|[第 5 步：將控制項添加到表單](../ide/step-5-add-controls-to-your-form.md)|將控制項 (例如 `PictureBox` 控制項和 `CheckBox` 控制項) 新增至表單。 將按鈕加入至表單。|
|[第 6 步：命名按鈕控制項](../ide/step-6-name-your-button-controls.md)|將按鈕重新命名為更有意義的名稱。|
|[步驟 7：將對話方塊元件新增至您的表單](../ide/step-7-add-dialog-components-to-your-form.md)|將一個 `OpenFileDialog` 元件和一個 `ColorDialog` 元件加入您的表單。|
|[步驟 8：為顯示圖片按鈕事件處理常式撰寫程式碼](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|使用 IntelliSense 工具編寫代碼。|
|[步驟 9：檢閱、註解和測試您的程式碼](../ide/step-9-review-comment-and-test-your-code.md)|檢閱和測試程式碼。 視需要加入註解。|
|[步驟 10：為其他按鈕和核取方塊編寫代碼](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|使用 IntelliSense 撰寫程式碼讓其他按鈕和核取方塊發揮作用。|
|[第 11 步：運行應用並嘗試其他功能](../ide/step-11-run-your-program-and-try-other-features.md)|運行應用並設置背景顏色。 嘗試其他功能，例如變更色彩、字型和框線。|

也有偉大的，免費的視頻學習資源可供你使用。 要瞭解有關 C# 中程式設計的更多詳細資訊，請參閱[C# 基礎知識：絕對初學者的開發](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)。 若要深入了解 Visual Basic 中的程式設計，請參閱 [Visual Basic 基礎：徹底初學者開發](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) \(英文\)。

## <a name="next-steps"></a>後續步驟

要開始本教程，請從步驟 1 開始**[：創建 Windows 表單應用程式專案](../ide/step-1-create-a-windows-forms-application-project.md)**。

## <a name="see-also"></a>另請參閱

* [更多 C# 教程](/visualstudio/get-started/csharp/)
* [Visual Basic 教學課程](/visualstudio/get-started/visual-basic/)
* [C++教程](/cpp/get-started/tutorial-console-cpp)
