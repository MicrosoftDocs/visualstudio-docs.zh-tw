---
title: 重要命令語言服務篩選 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1e7affdbcad2b935a05420a2817c5d8bda5cd9cf
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="important-commands-for-language-service-filters"></a>語言服務篩選器的重要命令
如果您想要建立功能完整的語言服務篩選條件，請考慮將處理下列的命令。 中定義的命令識別碼的完整清單<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>列舉 managed 程式碼和 Stdidcmd.h 標頭檔案 unmanaged[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]程式碼。 您可以找到 Stdidcmd.h 檔案中的*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Common\Inc。  
  
## <a name="commands-to-handle"></a>控制代碼的命令  
  
> [!NOTE]
>  您不一定要篩選下表中的每個命令。  
  
|命令|描述|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者按一下滑鼠右鍵時，就會傳送。 此命令會指出它是以提供快顯功能表的時間。 如果您不處理這個命令，文字編輯器會提供不含任何語言特有的命令的預設快顯功能表。 若要包含在此功能表命令，處理命令，並顯示快顯功能表自己。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 CTRL + J，通常傳送。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>顯示陳述式完成方塊。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|使用者所輸入的字元時傳送。 監視此命令，以判斷當輸入觸發字元，並提供陳述式完成、 方法秘訣和文字標記，例如語法著色，大括號比對，以及錯誤的標記。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>陳述式完成和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>方法的提示。 若要支援文字標記，監視這個命令來判斷正在輸入的字元是否需要您更新您的標記。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 Enter 鍵時，就會傳送。 監視此命令來判斷何時要藉由呼叫解除方法提示視窗<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。 根據預設，[文字] 檢視會處理這個命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|使用者輸入退格鍵時傳送。 判斷何時要藉由呼叫解除方法提示視窗的監視器<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。 根據預設，[文字] 檢視會處理這個命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從功能表或快速鍵傳送。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>更新提示視窗的參數資訊。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者將滑鼠停留在變數上或將游標放在變數上，選取傳送**快速諮詢**從**IntelliSense**中**編輯**功能表。 傳回類型的變數在提示中，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。 如果使用中偵錯，則提示應該也會顯示變數的值。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 CTRL + 空格鍵時，通常傳送。 此命令會告知語言服務呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常，從功能表中，傳送**註解選取範圍**或**取消註解選取範圍**從**進階**中**編輯**功能表。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 表示使用者想要標記為註解選取的文字。<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>指出使用者想要選取的文字取消註解。 這些命令可以只由語言服務實作。|  
  
## <a name="see-also"></a>另請參閱  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)