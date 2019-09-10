---
title: 教學課程 1：建立圖片檢視器
ms.date: 08/30/2019
ms.assetid: 3071d6df-2b2f-4e95-ab68-bef727323136
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.devlang:
- csharp
- vb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1506f4303cf5344c4035642cfdd3e42c98396b02
ms.sourcegitcommit: bd4e45f1697a8fbfdbc0a7c6b531c8f7b9fb8a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808770"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>教學課程 1：建立圖片檢視器

在本教學課程中，您會建立一個從檔案載入圖片並將它顯示在視窗中的應用程式。 您將瞭解如何使用**Windows Form 設計工具**將控制項（例如按鈕和圖片方塊）拖曳至表單、設定其屬性，以及使用容器來順暢地調整表單大小。 您也會開始撰寫程式碼。

> [!NOTE]
> 本教學課程中同時涵蓋 Visual C# 和 Visual Basic，所以請將焦點放在您使用的程式語言專屬資訊。

本教學課程將逐步引導您完成下列工作：

* 建立新的專案。

* 測試 (偵錯) 應用程式。

* 將基本控制項 (例如核取方塊和按鈕) 加入至表單。

* 使用版面配置將控制項放在表單上。

* 將 [開啟檔案] 和 [色彩] 對話方塊新增至表單。

* 使用 IntelliSense 和程式碼片段來撰寫程式碼。

* 撰寫事件處理常式方法。

當您完成時，您的程式看起來應該類似下圖：

![您在本教學課程中建立的圖片檢視器應用程式](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>教學課程的連結

|標題|描述|
|-----------|-----------------|
|[步驟 1：建立 Windows Forms 應用程式專案](../ide/step-1-create-a-windows-forms-application-project.md)|從建立 Windows Forms 應用程式專案開始。|
|[步驟 2：執行您的應用程式](../ide/step-2-run-your-program.md)|執行您在上一個步驟中建立的 Windows Forms 應用程式。|
|[步驟 3：設定表單屬性](../ide/step-3-set-your-form-properties.md)|使用 [屬性] 視窗變更表單的外觀。|
|[步驟 4：使用 TableLayoutPanel 控制項來配置表單](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|新增 `TableLayoutPanel` 控制項至表單。|
|[步驟 5：將控制項新增至表單](../ide/step-5-add-controls-to-your-form.md)|將控制項 (例如 `PictureBox` 控制項和 `CheckBox` 控制項) 新增至表單。 將按鈕加入至表單。|
|[步驟 6：命名按鈕控制項](../ide/step-6-name-your-button-controls.md)|將按鈕重新命名為更有意義的名稱。|
|[步驟 7：將對話方塊元件新增至表單](../ide/step-7-add-dialog-components-to-your-form.md)|將一個 `OpenFileDialog` 元件和一個 `ColorDialog` 元件加入您的表單。|
|[步驟 8：為顯示圖片按鈕事件處理常式撰寫程式碼](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|使用 IntelliSense 工具撰寫程式碼。|
|[步驟 9：檢閱、註解及測試您的程式碼](../ide/step-9-review-comment-and-test-your-code.md)|檢閱和測試程式碼。 視需要加入註解。|
|[步驟 10：為其他按鈕及核取方塊撰寫程式碼](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|使用 IntelliSense 撰寫程式碼讓其他按鈕和核取方塊發揮作用。|
|[步驟 11：執行您的程式並嘗試其他功能](../ide/step-11-run-your-program-and-try-other-features.md)|執行程式並設定背景色彩。 嘗試其他功能，例如變更色彩、字型和框線。|

## <a name="next-steps"></a>後續步驟

若要開始本教學課程， **請從[步驟1開始：建立 Windows Forms 應用程式專案](../ide/step-1-create-a-windows-forms-application-project.md)。**

## <a name="see-also"></a>另請參閱

* [其他C#教學課程](/visualstudio/get-started/csharp/)
* [Visual Basic 教學課程](/visualstudio/get-started/visual-basic/)
* [C++教程](../ide/getting-started-with-cpp-in-visual-studio.md)
