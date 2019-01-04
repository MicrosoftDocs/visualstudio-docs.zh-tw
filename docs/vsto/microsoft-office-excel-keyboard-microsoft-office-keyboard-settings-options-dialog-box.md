---
title: Microsoft Office Excel 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: db76d40db1038983cd756c5eb35549357afa53c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53926472"
---
# <a name="microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box"></a>Microsoft Office Excel 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊
  Microsoft Office Excel 和 Visual Studio 同時處理的快速鍵。 不同的命令，在 Excel 中，然後在 Visual Studio 中可以代表相同的快速鍵組合。 在 Visual Studio 中的文件層級專案中開啟 Excel 時，一次只有一個應用程式接收快顯命令。 根據預設，Visual Studio 會接收所有捷徑命令，但是您可以讓接收它們，當文件取得焦點時選取的 Excel**動態鍵盤配置**。  
  
 如果您使用未指派給應用程式中目前正在處理的快速鍵命令的快速鍵，攠摝坫會傳遞給其他應用程式。  
  
 您選取的選項會保持作用中 Excel 專案直到變更為止。 選取項目不會影響 Microsoft Office Word 專案的專案。您必須進行任何變更 word 使用的 Microsoft Office Word 鍵盤選項。  
  
## <a name="uielement-list"></a>UIElement 清單  
 **Visual Studio 鍵盤配置**  
 Visual Studio 會收到所有的快顯重要命令中，即使 Excel 具有焦點。 例如，如果您按功能鍵**F5** Excel 具有焦點，而 Visual Studio 會啟動偵錯您的解決方案。  
  
 **動態鍵盤配置**  
 只在具有焦點時，visual Studio 就會收到快顯命令。 當 Excel 具有焦點時，Excel 就會收到所有的捷徑命令。 例如，如果您按功能鍵**F5**雖然 Excel 有焦點，Excel 會開啟**移至** 對話方塊。 如果您按下**F5** Visual Studio 具有焦點，而 Visual Studio 會啟動偵錯您的解決方案。  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft Office Word 鍵盤，Microsoft Office 鍵盤設定、 [選項] 對話方塊](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)  
