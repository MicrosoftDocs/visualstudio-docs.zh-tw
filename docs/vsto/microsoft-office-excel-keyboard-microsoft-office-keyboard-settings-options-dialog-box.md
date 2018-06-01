---
title: Microsoft Office Excel 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: fc71c699dfea11b8654791efdd52e4c0751a9762
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692443"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊
  Microsoft Office Excel 和 Visual Studio 同時處理快顯的索引鍵。 針對不同的命令，在 Excel 中，然後在 Visual Studio 中，可以獨立相同快速鍵組合。 在 Visual Studio 中的文件層級專案中開啟 Excel 時，一次只有一個應用程式接收快顯命令。 根據預設，Visual Studio 會收到所有捷徑命令，但您可以建立 Excel 文件選取具有焦點時，接收這些**動態鍵盤配置**。  
  
 如果您使用未指派給目前正在處理的快速鍵的應用程式中命令的快速鍵，攠摝坫會傳遞給其他應用程式。  
  
 您選取的選項會保持作用中的 Excel 專案直到變更為止。 選取項目不會影響 Microsoft Office Word 專案的專案。您必須進行任何變更 word 使用 Microsoft Office Word 鍵盤選項。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **Visual Studio 鍵盤配置**  
 Visual Studio 會收到所有捷徑命令，即使 Excel 具有焦點。 例如，如果您按功能鍵**F5** Excel 具有焦點，而 Visual Studio 會啟動偵錯您的方案。  
  
 **動態鍵盤配置**  
 Visual Studio 會在有焦點時，才收到快顯命令。 當 Excel 具有焦點時，Excel 就會收到所有的捷徑命令。 例如，如果您按功能鍵**F5** Excel 焦點時，會開啟 Excel**移至** 對話方塊。 如果您按下**F5** Visual Studio 具有焦點，而 Visual Studio 會啟動偵錯您的方案。  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft Office Word 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
  
  