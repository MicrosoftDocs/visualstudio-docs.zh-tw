---
title: HOW TO：使用文字標記 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - using text markers
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7f847fa2ba58c8d3278a4ecec1c7d7ddc204f27e
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/22/2019
ms.locfileid: "56707493"
---
# <a name="how-to-use-text-markers"></a>HOW TO：使用文字標記
文字標記可以套用至編輯<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>物件。

## <a name="procedures"></a>程序

### <a name="to-apply-text-markers"></a>若要套用文字標記

1.  取得的執行個體<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>類別。

    > [!NOTE]
    >  核心編輯器會自動將標準文字標記套用至任何已編輯的文件，它應該不需要明確地套用標準文字標記。

2.  取得您想要藉由呼叫的標記的標記類型識別碼<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>方法使用`GUID`您想要使用的文字標記。

    > [!NOTE]
    >  請勿使用`GUID`VSPackage 或提供文字標記的服務。

3.  使用標記類型識別碼取得藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>方法做為參數來呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>来套用到指定的文字區域的文字標記的方法。

### <a name="to-add-features-to-text-markers"></a>若要將功能加入至文字標記

1. 它可能會想要將其他功能加入至文字標記，例如工具提示、 特殊的操作功能表中或處理常式的特殊情況。 方法如下：

2. 建立物件，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。

3. 如果需要額外的功能，實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>，而<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>實作的相同物件上的介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。

4. 傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>建立要呼叫的介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法用來將文字標記套用至指定的文字區域。

5. 將內容功能表支援加入文字標記區域時，必須建立功能表。

    如需有關如何建立內容功能表，請參閱[快顯功能表](../extensibility/context-menus.md)。

6. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境呼叫的方法提供的介面，例如<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>方法，或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>所需的方法。

## <a name="see-also"></a>另請參閱
- [在舊版的 API 中使用文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)
- [如何：新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)
- [如何：建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)
- [如何：實作錯誤標記](../extensibility/how-to-implement-error-markers.md)