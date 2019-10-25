---
title: 語言服務篩選的重要命令 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0e2e605a0725c2f88922d3e3ce899263171bc4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726933"
---
# <a name="important-commands-for-language-service-filters"></a>語言服務篩選的重要命令
如果您想要建立功能完整的語言服務篩選器，請考慮處理下列命令。 命令識別碼的完整清單定義于 managed 程式碼的 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 列舉和非受控 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 程式碼的 Stdidcmd 標頭檔中。 您可以在*VISUAL STUDIO SDK 安裝路徑*\VisualStudioIntegration\Common\Inc. 中找到 Stdidcmd 檔案。

## <a name="commands-to-handle"></a>要處理的命令

> [!NOTE]
> 您不一定要篩選下表中的每個命令。

|命令|描述|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者以滑鼠右鍵按一下時傳送。 此命令表示提供快捷方式功能表的時機。 如果您未處理此命令，文字編輯器會提供預設的快捷方式功能表，但不含任何語言特定的命令。 若要在此功能表上包含您自己的命令，請處理命令，並自行顯示快捷方式功能表。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常會在使用者輸入 CTRL + J 時傳送。 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 上的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法，以顯示語句完成框。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入字元時傳送。 監視此命令以判斷何時輸入觸發程式字元，並提供語句完成、方法提示和文字標記，例如語法著色、括弧對稱和錯誤標記。 針對語句完成，在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法，並在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 上針對方法提示進行 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> 方法。 若要支援文字標記，請監視此命令以判斷要輸入的字元是否需要您更新標記。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者鍵入 Enter 鍵時傳送。 監視此命令，以判斷何時要在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 方法來關閉方法提示視窗。 根據預設，文字視圖會處理此命令。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 Backspace 鍵時傳送。 [監視]，藉由在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> 方法，判斷何時關閉方法提示視窗。 根據預設，文字視圖會處理此命令。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從功能表或快速鍵傳送。 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 上的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 方法，以使用參數資訊來更新提示視窗。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者將滑鼠指標停留在變數上，或將游標置於變數上，並從 [**編輯**] 功能表中的**IntelliSense**選取 [**快速**諮詢] 時傳送。 藉由在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> 方法，傳回提示中的變數類型。 如果正在使用調試，秘訣也應該顯示變數的值。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常會在使用者輸入 CTRL + 空格鍵時傳送。 此命令會告訴語言服務在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 上呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 方法。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|在 [**編輯**] 功能表中從功能表傳送，通常是**批註選取**或**取消選取**[ **Advanced** ]。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 表示使用者想要將選取的文字加上批註;<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 表示使用者想要取消選取文字的批註。 這些命令只能由語言服務執行。|

## <a name="see-also"></a>請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)