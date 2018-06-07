---
title: 選項對話方塊、 Microsoft Office Word 鍵盤，Microsoft Office 鍵盤設定、 |Microsoft 文件
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9edd5cd987eb6a4e93b02c8e774adefbc7f969d2
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34572107"
---
# <a name="microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Word 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊
  Microsoft Office Word 和 Visual Studio 同時處理快顯的索引鍵。 針對不同的命令，在 Word 和 Visual Studio 中，可以獨立相同快速鍵組合。 在 Visual Studio 中的文件層級專案中開啟 Word 時，一次只有一個應用程式接收快顯命令。 根據預設，Visual Studio 會收到所有捷徑命令，但您可以讓 Word 文件選取具有焦點時，接收這些**動態鍵盤配置**。  
  
 如果您使用未指派給目前正在處理的快速鍵的應用程式中命令的快速鍵，攠摝坫會傳遞給其他應用程式。  
  
 您選取的選項會保持作用中的 Word 專案直到變更為止。 選取項目不會影響 Microsoft Office Excel 專案的專案。您必須使用 Microsoft Office Excel 鍵盤選項進行適用於 Excel 的任何變更。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **Visual Studio 鍵盤配置**  
 Visual Studio 會收到所有捷徑命令，即使 Word 文件具有焦點。 例如，如果您按功能鍵**F5**文件具有焦點，而 Visual Studio 會啟動偵錯您的方案。  
  
 **動態鍵盤配置**  
 Visual Studio 會在有焦點時，才收到快顯命令。 當 Word 文件具有焦點時，Word 就會收到所有的捷徑命令。 例如，如果您按功能鍵**F5**時的 Word 文件具有焦點，Word 會開啟**尋找和取代**對話方塊**移至**選取的索引標籤。 如果您按下**F5** Visual Studio 具有焦點，而 Visual Studio 會啟動偵錯您的方案。  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft Office Excel 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  