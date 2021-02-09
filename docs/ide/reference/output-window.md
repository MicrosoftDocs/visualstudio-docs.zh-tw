---
title: 輸出視窗
description: 深入瞭解 [輸出] 視窗，以及它如何顯示 IDE 中各種功能的狀態訊息。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0bdbaf79a3700a1ba1c0574e345093af25608e39
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932042"
---
# <a name="output-window"></a>輸出視窗

[輸出] 視窗顯示整合式開發環境 (IDE) 中各種功能的狀態訊息。 若要開啟 [輸出] 視窗，請在功能表列上選擇 [檢視] >  [輸出]，或按下 **Ctrl**+**Alt**+**O**。

## <a name="toolbar"></a>工具列

下列控制項會顯示在 [輸出] 視窗的工具列中。

### <a name="show-output-from"></a>顯示來自以下位置的輸出

顯示要檢視的一或多個輸出窗格。 根據 IDE 中的哪些工具使用 [輸出] 視窗將訊息傳遞給使用者，可能可以使用數個資訊窗格。

### <a name="find-message-in-code"></a>在程式碼中尋找訊息

將程式碼編輯器中的插入點移至包含所選取建置錯誤的行。

### <a name="go-to-previous-message"></a>移至上一個訊息

將 [輸出] 視窗中的焦點變更為上一個建置錯誤，並將程式碼編輯器中的插入點移至包含該建置錯誤的行。

### <a name="go-to-next-message"></a>移至下一個訊息

將 [輸出] 視窗中的焦點變更為下一個建置錯誤，並將程式碼編輯器中的插入點移至包含該建置錯誤的行。

### <a name="clear-all"></a>全部清除

從 [輸出] 窗格清除所有文字。

### <a name="toggle-word-wrap"></a>切換自動換行

開啟和關閉 [輸出] 窗格中的自動換行功能。 開啟自動換行時，較長項目中超出檢視區域的文字會顯示在下一行。

## <a name="output-pane"></a>輸出窗格

[顯示來自以下位置的輸出] 清單中所選取的 [輸出] 窗格會顯示來自所指出來源的輸出。

## <a name="route-messages-to-the-output-window"></a>將訊息傳送至輸出視窗

若只要建置專案就顯示 [輸出] 視窗，請在 [選項] 對話方塊的 [專案和方案] > [一般] 頁面中選取 [建置開始時顯示輸出視窗]。 然後，在開啟程式碼檔案進行編輯時，選擇 [輸出] 視窗工具列上的 [移至下一個訊息] 和 [移至上一個訊息] 以選取 [輸出] 窗格中的項目。 當您這麼做時，程式碼編輯器中的插入點會跳到發生所選取問題的程式碼行。

[命令視窗](../../ide/reference/command-window.md)中所叫用的某些 IDE 功能和命令會將其輸出傳遞給 [輸出] 視窗。 當您在 [管理外部工具](../../ide/managing-external-tools.md)中選取 [使用輸出視窗] 選項時，會將一般顯示在命令視窗中且來自外部工具的輸出 (例如 *.bat* 和 *.com* 檔案) 傳送至 [輸出] 窗格。 許多其他種類的訊息也可以顯示在 [輸出] 窗格中。 例如，針對目標資料庫檢查預存程序中的 Transact-SQL 語法時，結果會顯示在 [輸出] 視窗中。

您也可以透過程式設計方式撰寫自己的應用程式，以在執行階段將診斷訊息寫入 [輸出] 窗格。 若要執行此工作，請使用 .NET API <xref:System.Diagnostics> 命名空間中的 <xref:System.Diagnostics.Debug> 類別或 <xref:System.Diagnostics.Trace> 類別的成員。 建置方案或專案的偵錯組態時，<xref:System.Diagnostics.Debug> 類別的成員會顯示輸出；建置偵錯或發行組態時，<xref:System.Diagnostics.Trace> 類別的成員會顯示輸出。 如需詳細資訊，請參閱[輸出視窗中的診斷訊息](../../debugger/diagnostic-messages-in-the-output-window.md)。

在 C++ 中，您可以建立自訂建置步驟和建置事件，而其警告和錯誤會顯示並計入 [輸出] 窗格中。 您可以在輸出行上按 **F1**，以顯示適當的說明主題。 如需詳細資訊，請參閱[格式化自訂建置步驟的輸出](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event)。

## <a name="scroll-behavior"></a>捲動行為

如果您在 [輸出] 視窗中使用自動捲動，然後使用滑鼠或方向鍵進行巡覽，則會停止自動捲動。 若要繼續自動捲動，請按下 **Ctrl** + **End**。

## <a name="see-also"></a>另請參閱

- [輸出視窗中的診斷訊息](../../debugger/diagnostic-messages-in-the-output-window.md)
- [如何：控制輸出視窗](/previous-versions/ht6z4e28(v=vs.140))
- [編譯和建置](../../ide/compiling-and-building-in-visual-studio.md)
- [了解組建組態](../../ide/understanding-build-configurations.md)
- [類別庫概觀](/dotnet/standard/class-library-overview)