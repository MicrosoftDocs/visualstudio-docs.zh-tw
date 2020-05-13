---
title: 語言服務篩選器的重要命令 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707618"
---
# <a name="important-commands-for-language-service-filters"></a>語言服務篩選的重要命令
如果要創建功能齊全的語言服務篩選器,請考慮處理以下命令。 命令識別碼的完整清單在託管代碼的<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>枚舉和非託管[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]代碼的 Stdidcmd.h 標頭檔中定義。 您可以在*Visual Studio SDK 安裝路徑*[VisualStudio 集成]公共_Inc 中找到 Stdidcmd.h 檔。

## <a name="commands-to-handle"></a>要處理的指令

> [!NOTE]
> 不必對下表中的每個命令進行篩選。

|Command|描述|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|使用者右鍵按一下時發送。 此命令指示是時候提供快捷功能表了。 如果不處理此命令,文本編輯器提供預設快捷功能表,而不執行任何特定於語言的命令。 要在此功能表上包含您自己的命令,請自行處理該命令並顯示快捷功能表。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常在用戶鍵入CTRL_J 時發送。 調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>的方法 以顯示語句完成框。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|在用戶鍵入字元時發送。 監視此命令以確定何時鍵入觸發器字元,並提供語句完成、方法提示和文本標記,如語法著色、大括弧匹配和錯誤標記。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>for 語句<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>完成上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>的方法和 for 方法提示上的方法。 要支援文本標記,請監視此命令以確定鍵入的字元是否需要更新標記。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|在用戶鍵入 Enter 鍵時發送。 監視此命令,通過在 上調<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>用 方法來確定何時關閉方法提示<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>視窗。 預設情況下,文本檢視處理此命令。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|在用戶鍵入"後空間"鍵時發送。 監視,通過在 上調<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>用 方法來確定何時關閉方法提示<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>視窗。 預設情況下,文本檢視處理此命令。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從功能表或快速鍵發送。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>的方法 以使用參數資訊更新提示視窗。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者懸停在變數上或將游標定位在變數上,並在 **「編輯」** 選單中選擇「IntelliSense」中的**IntelliSense****「快速資訊**」時,已發送。 通過在調用 上的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>返回 提示中的變數的類型<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。 如果調試處於活動狀態,則提示還應顯示變數的值。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常在用戶鍵入 CTRL_空格鍵時發送。 此指令告訴語言服務呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>的方法 。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從選單發送,通常是 **「編輯」** 選單中的 **「進階」中的「註釋選擇**」或 **「取消註釋選擇**」 。 **Advanced** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>指示使用者要註釋掉選取的文字;但<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>指示使用者要取消註釋所選文本。 這些命令只能由語言服務實現。|

## <a name="see-also"></a>另請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
