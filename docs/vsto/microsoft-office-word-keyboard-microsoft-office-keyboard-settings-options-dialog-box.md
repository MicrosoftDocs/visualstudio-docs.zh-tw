---
title: Office Word 鍵盤，鍵盤設定、 [選項] 對話方塊
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
ms.openlocfilehash: 5180aa2f4c5022cedcba2c5377d2ff2ac14ffb28
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66835986"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊
  Microsoft Office Word 和 Visual Studio 同時處理的快速鍵。 不同的命令，在 Word 中，並在 Visual Studio 中可以代表相同的快速鍵組合。 在 Visual Studio 中的文件層級專案中開啟 Word 時，一次只有一個應用程式接收快顯命令。 根據預設，Visual Studio 會接收所有捷徑命令，但是您可以讓 Word 文件藉由選取具有焦點時，接收它們**動態鍵盤配置**。

 如果您使用未指派給應用程式中目前正在處理的快速鍵命令的快速鍵，攠摝坫會傳遞給其他應用程式。

 您選取的選項會保持作用中 Word 專案直到變更為止。 選取項目不會影響 Microsoft Office Excel 專案的專案。您必須使用 Microsoft Office Excel 鍵盤選項進行適用於 Excel 的任何變更。

## <a name="uielement-list"></a>UIElement 清單
 **Visual Studio 鍵盤配置**Visual Studio 會收到所有捷徑命令，即使在 Word 文件具有焦點。 例如，如果您按功能鍵**F5**文件具有焦點，而 Visual Studio 會啟動偵錯您的解決方案。

 **動態鍵盤配置**Visual Studio 接收快顯命令，只在具有焦點時。 當 Word 文件具有焦點時，Word 就會收到所有的捷徑命令。 例如，如果您按功能鍵**F5**雖然 Word 文件具有焦點，Word 會開啟**尋找和取代**對話方塊，其中包含**移至**選取的索引標籤。 如果您按下**F5** Visual Studio 具有焦點，而 Visual Studio 會啟動偵錯您的解決方案。

## <a name="see-also"></a>另請參閱
- [Microsoft Office Excel 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)
