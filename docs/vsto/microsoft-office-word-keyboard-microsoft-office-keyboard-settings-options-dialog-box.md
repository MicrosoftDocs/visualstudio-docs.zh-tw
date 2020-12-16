---
title: 選項對話方塊、設定、Office Word 鍵盤
description: 瞭解如何在檔具有選取動態鍵盤配置的焦點時，讓 Microsoft Word 接收快速鍵命令。
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Microsoft_Office_Tools.Microsoft_Office_Word.Keyboard
- VS.ToolsOptionsPages.Microsoft_Office_Keyboard_Settings.Microsoft_Office_Word_Keyboard
- VST.WordOptions.KeyboardMappingScheme
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- keyboard shortcuts, Office development in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: bf4cfbaf23ad9c1e545af25614722cd52c493df7
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528444"
---
# <a name="microsoft-office-word-keyboard-settings-options-dialog-box"></a>選項對話方塊、設定、Microsoft Office Word 鍵盤
  Microsoft Office Word 和 Visual Studio 都處理快速鍵。 相同的快速鍵組合可用於 Word 和 Visual Studio 中的不同命令。 當 Word 在 Visual Studio 的檔層級專案中開啟時，一次只有一個應用程式會收到快速鍵命令。 根據預設，Visual Studio 會接收所有快速鍵命令，但是您可以在檔具有選取 **動態鍵盤** 佈局的焦點時，讓 Word 接收它們。

 如果您使用的快速鍵未指派給目前正在處理快速鍵的應用程式中的命令，則會將快速鍵傳遞給另一個應用程式。

 您選取的選項將會對 Word 專案保持有效，直到您變更為止。 選取範圍不會影響 Excel 專案 Microsoft Office;您必須使用 Microsoft Office Excel 鍵盤選項對 Excel 進行任何變更。

## <a name="uielement-list"></a>UIElement 清單
 **Visual Studio 鍵盤** 佈局Visual Studio 會接收所有快速鍵命令，即使 Word 檔具有焦點也一樣。 例如，如果您在檔具有焦點時按下函式按鍵 **F5** ，Visual Studio 會開始對您的方案進行偵錯工具。

 **動態鍵盤** 佈局Visual Studio 只有在具有焦點時，才會收到快速鍵命令。 當 Word 檔具有焦點時，Word 就會收到所有快速鍵命令。 例如，如果您在 Word 檔具有焦點時按下函式按鍵 **F5** ，word 就會開啟 [ **尋找和取代** ] 對話方塊，並選取 [ **移至** ] 索引標籤。 如果您在 Visual Studio 具有焦點時按 **F5** ，Visual Studio 會開始將您的解決方案進行偵錯工具。

## <a name="see-also"></a>另請參閱
- [選項對話方塊、Microsoft Office 鍵盤設定 Microsoft Office Excel 鍵盤](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
