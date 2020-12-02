---
title: 教學課程 1：建立圖片檢視器
description: 瞭解如何建立可從檔案載入圖片並將它顯示在視窗中的應用程式。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1c0eea844b04cbe8ba261fd4d65a6d21fb99aa4b
ms.sourcegitcommit: df6ba39a62eae387e29f89388be9e3ee5ceff69c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2020
ms.locfileid: "96479130"
---
# <a name="tutorial-1-create-a-picture-viewer"></a>教學課程 1：建立圖片檢視器

在本教學課程中，您會建立一個應用程式，從檔案載入圖片並將它顯示在視窗中。 您將瞭解如何使用 **Windows Form 設計工具** 將控制項（例如按鈕和圖片方塊）拖曳至表單、設定其屬性，以及使用容器來順暢地調整表單的大小。 您也會開始撰寫程式碼。

> [!NOTE]
> 本教學課程涵蓋 c # 和 Visual Basic，因此著重于您所使用之程式設計語言的特定資訊。

本教學課程會逐步引導您完成下列工作：

* 建立新專案。

* 測試 (偵錯) 應用程式。

* 將基本控制項 (例如核取方塊和按鈕) 加入至表單。

* 使用版面配置將控制項放在表單上。

* 將 [開啟檔案] 和 [色彩] 對話方塊新增至表單。

* 使用 IntelliSense 和程式碼片段撰寫程式碼。

* 撰寫事件處理常式方法。

當您完成時，您的應用程式看起來應該如下圖所示：

![您在本教學課程中建立的圖片檢視器應用程式](../ide/media/express_pictureviewerdone.png)

## <a name="tutorial-links"></a>教學課程的連結

|標題|描述|
|-----------|-----------------|
|[步驟 1：建立 Windows Forms 應用程式專案](../ide/step-1-create-a-windows-forms-application-project.md)|首先，建立 Windows Forms 應用程式專案。|
|[步驟2：執行您的圖片檢視器應用程式](../ide/step-2-run-your-program.md)|執行您在上一個步驟中建立的 Windows Forms 應用程式專案。|
|[步驟 3：設定表單屬性](../ide/step-3-set-your-form-properties.md)|使用 [屬性] 視窗變更表單的外觀。|
|[步驟 4：使用 TableLayoutPanel 控制項來配置表單](../ide/step-4-lay-out-your-form-with-a-tablelayoutpanel-control.md)|新增 `TableLayoutPanel` 控制項至表單。|
|[步驟 5：將控制項新增至表單](../ide/step-5-add-controls-to-your-form.md)|將控制項 (例如 `PictureBox` 控制項和 `CheckBox` 控制項) 新增至表單。 將按鈕加入至表單。|
|[步驟 6：命名按鈕控制項](../ide/step-6-name-your-button-controls.md)|將按鈕重新命名為更有意義的名稱。|
|[步驟 7：將對話方塊元件新增至您的表單](../ide/step-7-add-dialog-components-to-your-form.md)|將一個 `OpenFileDialog` 元件和一個 `ColorDialog` 元件加入您的表單。|
|[步驟8：為顯示圖片按鈕事件處理常式撰寫程式碼](../ide/step-8-write-code-for-the-show-a-picture-button-event-handler.md)|使用 IntelliSense 工具撰寫程式碼。|
|[步驟 9：檢閱、註解及測試您的程式碼](../ide/step-9-review-comment-and-test-your-code.md)|檢閱和測試程式碼。 視需要加入註解。|
|[步驟 10：為其他按鈕及核取方塊撰寫程式碼](../ide/step-10-write-code-for-additional-buttons-and-a-check-box.md)|使用 IntelliSense 撰寫程式碼讓其他按鈕和核取方塊發揮作用。|
|[步驟 11：執行您的應用程式及嘗試其他功能](../ide/step-11-run-your-program-and-try-other-features.md)|執行您的應用程式並設定背景色彩。 嘗試其他功能，例如變更色彩、字型和框線。|

另外還有絕佳的免費影片學習資源可供您使用。 若要深入瞭解如何在 c # 中進行程式設計，請參閱 [c # 基礎：適用于絕對初學者的開發](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners)。 若要深入了解 Visual Basic 中的程式設計，請參閱 [Visual Basic 基礎：徹底初學者開發](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners) \(英文\)。

## <a name="next-steps"></a>後續步驟

若要開始本教學課程，請從 **[步驟1：建立 Windows Forms 應用程式專案](../ide/step-1-create-a-windows-forms-application-project.md)** 開始。

## <a name="see-also"></a>另請參閱

* [其他 c # 教學課程](../get-started/csharp/index.yml)
* [Visual Basic 教學課程](../get-started/visual-basic/index.yml)
* [C + + 教學課程](/cpp/get-started/tutorial-console-cpp)