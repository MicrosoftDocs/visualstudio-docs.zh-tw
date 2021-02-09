---
title: 選項對話方塊、設定、Office Excel 鍵盤
description: 瞭解如何在檔具有選取動態鍵盤配置的焦點時，讓 Microsoft Excel 接收快速鍵命令。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ExcelOptions.KeyboardMappingScheme
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Excel_Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Excel.Keyboard
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 914b86e6e2b27d18e2089d44ce97810f82294c5e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99880342"
---
# <a name="microsoft-office-excel-keyboard-settings-options-dialog-box"></a>選項對話方塊、設定、Microsoft Office Excel 鍵盤
  Microsoft Office Excel 和 Visual Studio 都處理快速鍵。 相同的快速鍵組合可以用於 Excel 和 Visual Studio 中的不同命令。 當 Excel 在 Visual Studio 的檔層級專案中開啟時，一次只有一個應用程式會收到快速鍵命令。 根據預設，Visual Studio 會接收所有快速鍵命令，但是您可以在檔具有選取 **動態鍵盤** 佈局的焦點時，讓 Excel 接收它們。

 如果您使用的快速鍵未指派給目前正在處理快速鍵的應用程式中的命令，則會將快速鍵傳遞給另一個應用程式。

 您選取的選項將會對 Excel 專案保持有效狀態，直到您變更為止。 選取範圍不會影響 Word 專案 Microsoft Office;您必須使用 Microsoft Office Word 鍵盤選項，對 Word 進行任何變更。

## <a name="uielement-list"></a>UIElement 清單
 **Visual Studio 鍵盤** 佈局Visual Studio 會接收所有快速鍵命令，即使 Excel 具有焦點也一樣。 例如，如果您在 Excel 具有焦點時按下函式按鍵 **F5** ，Visual Studio 會開始將您的方案進行偵錯工具。

 **動態鍵盤** 佈局Visual Studio 只有在具有焦點時，才會收到快速鍵命令。 當 Excel 具有焦點時，Excel 會接收所有快速鍵命令。 例如，如果您在 Excel 具有焦點時按下函式按鍵 **F5** ，excel 就會開啟 [ **移至** ] 對話方塊。 如果您在 Visual Studio 具有焦點時按 **F5** ，Visual Studio 會開始將您的解決方案進行偵錯工具。

## <a name="see-also"></a>另請參閱
- [選項對話方塊、Microsoft Office 鍵盤設定 Microsoft Office Word 鍵盤](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
