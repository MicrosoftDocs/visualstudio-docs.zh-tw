---
title: 重要的命令，語言服務篩選器 |Microsoft Docs
ms.date: 11/04/2016
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
ms.openlocfilehash: e9f4c568722700ab4521f8a34a0639e78b9f550b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53891692"
---
# <a name="important-commands-for-language-service-filters"></a>語言服務篩選的重要命令
如果您想要建立功能完整的語言服務篩選器，請考慮處理下列的命令。 在定義命令識別碼的完整清單<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>managed 程式碼和 Stdidcmd.h 標頭的列舉檔案未受管理[!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]程式碼。 您可以找到 Stdidcmd.h 檔案中的*Visual Studio SDK 安裝路徑*\VisualStudioIntegration\Common\Inc。  
  
## <a name="commands-to-handle"></a>控制代碼的命令  
  
> [!NOTE]
>  它並不一定要篩選為下表中的每個命令。  
  
|命令|描述|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者按一下滑鼠右鍵時，就會傳送。 此命令會指示就可以開始提供的快顯功能表。 如果您並未處理這個命令，文字編輯器會提供預設的捷徑功能表，而不需要任何語言特有的命令。 若要包含在此功能表命令，處理這個命令，並自行顯示捷徑功能表。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 CTRL + J，通常是傳送。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>顯示陳述式完成方塊。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入字元時，就會傳送。 監視此命令，以判斷當輸入觸發程序的字元，並提供陳述式完成、 方法秘訣和文字的標記，例如語法著色，大括號比對和錯誤標記。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>陳述式完成和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>方法秘訣。 若要支援文字標記，來監視此命令，以判斷是否要鍵入的字元，您必須更新您的標記。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 Enter 鍵時，就會傳送。 監視此命令來判斷何時要關閉方法提示視窗，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。 根據預設，[文字] 檢視會處理這個命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入退格鍵時，就會傳送。 用於決定何時要關閉藉由呼叫的方法提示視窗的監視器<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>。 根據預設，[文字] 檢視會處理這個命令。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|從功能表或快速鍵傳送。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>若要使用的參數資訊來更新 [提示] 視窗。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者將滑鼠指標停留在變數上，或將游標置於變數，並選取時，傳送**快速諮詢**從**IntelliSense**中**編輯**功能表。 傳回變數的型別提示中，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。 如果您已啟用偵錯，提示應該也會顯示變數的值。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|當使用者輸入 CTRL + 空格鍵時，通常傳送。 此命令會告知要呼叫的語言服務<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|通常，從功能表中，傳送**註解選取範圍**或是**取消註解選取範圍**從**進階**中**編輯**功能表。 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> 表示使用者想要標記為註解選取的文字;<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>表示使用者想要取消註解選取的文字。 這些命令可以只由語言服務實作。|  
  
## <a name="see-also"></a>另請參閱  
 [開發舊版語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)