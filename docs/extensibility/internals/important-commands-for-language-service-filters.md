---
title: 語言服務篩選的重要命令 |Microsoft Docs
description: 瞭解在 Visual Studio 中建立功能完整的語言服務篩選器時，應該支援的重要命令。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5d27f1c3057266d1b167999f3178a3e554a78ddb
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069552"
---
# <a name="important-commands-for-language-service-filters"></a>語言服務篩選的重要命令
如果您想要建立功能完整的語言服務篩選器，請考慮處理下列命令。 命令識別碼的完整清單定義于 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> managed 程式碼的列舉和非受控碼的 Stdidcmd .h 標頭檔中 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 。 您可以在 *VISUAL STUDIO SDK 安裝路徑*\VisualStudioIntegration\Common\Inc. 中找到 Stdidcmd .h 檔案。

## <a name="commands-to-handle"></a>要處理的命令

> [!NOTE]
> 對於下表中的每個命令而言，並不是必要的。

|命令|描述|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者以滑鼠右鍵按一下時傳送。 此命令表示提供快捷方式功能表是時候。 如果您未處理此命令，文字編輯器會提供預設快捷方式功能表，而不會有任何特定語言的命令。 若要在此功能表上包含您自己的命令，請處理命令並自行顯示快捷方式功能表。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常會在使用者輸入 CTRL + J 時傳送。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>在上呼叫方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ，以顯示語句完成方塊。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入字元時傳送。 監視這個命令以判斷何時輸入觸發程式字元，並提供語句完成、方法提示和文字標記，例如語法著色、括弧對稱和錯誤標記。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>在 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> for 語句完成和上的方法上呼叫方法提示的方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> 。 若要支援文字標記，請監視這個命令以判斷所輸入的字元是否需要您更新標記。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 Enter 鍵時傳送。 監視這個命令，藉由在上呼叫方法，判斷何時要關閉方法提示視窗 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 。 根據預設，文字視圖會處理此命令。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入倒退鍵時傳送。 在上呼叫方法，以判斷何時要關閉方法提示視窗 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> 。 根據預設，文字視圖會處理此命令。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從功能表或快速鍵傳送。 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>在上呼叫方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ，以使用參數資訊來更新提示視窗。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者將游標停留在變數上，或將游標放在變數上，並從 [**編輯**] 功能表中的 **IntelliSense** 選取 [**快速** 諮詢] 時傳送。 藉由在上呼叫方法，在提示中傳回變數的類型 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。 如果是使用中的偵錯工具，提示也應該顯示變數的值。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常會在使用者輸入 CTRL + 空格鍵時傳送。 此命令會指示語言服務 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> 在上呼叫方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 。|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從功能表傳送，通常 **會在 [** **編輯**] 功能表中 **批註選取** 或 **取消批註選取專案**。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 表示使用者想要將選取的文字加上批註; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 表示使用者想要取消選取的文字。 這些命令只能由語言服務來執行。|

## <a name="see-also"></a>另請參閱
- [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)
