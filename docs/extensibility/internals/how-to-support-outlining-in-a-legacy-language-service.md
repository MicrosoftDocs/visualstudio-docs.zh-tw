---
title: 如何:支持傳統語言服務大綱 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], collapse to definitions command
- language services, supporting Collapse to Definitions command
- hidden text, Collapse to Definitions command
ms.assetid: bb6e74c3-93e4-4ef7-afc7-1c9b342f083b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 28396d513c83ed83e2769e75a6020a98b10251b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707910"
---
# <a name="how-to-support-outlining-in-a-legacy-language-service"></a>如何:支援傳統語言服務中的大綱
大綱用於展開或摺疊文本的不同區域。 不同語言可以以不同的方式定義大綱的使用方式。 如需詳細資訊，請參閱[大綱](../../ide/outlining.md)。

 舊語言服務是作為 VSPackage 的一部分實現的,但實現語言服務功能的較新方法是使用 MEF 擴展。 要瞭解有關實現大綱的新方法的更多,請參閱[演練:大綱](../../extensibility/walkthrough-outlining.md)。

> [!NOTE]
> 我們建議您儘快開始使用新的編輯器 API。 這將提高語言服務的性能,並允許您利用新的編輯器功能。

 下面演示如何支援語言服務的此命令。

## <a name="to-support-outlining"></a>支援大綱

1. 在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage>語言服務對象上實現。

2. 調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>當前大綱會話物件以添加新大綱區域。

## <a name="robust-programming"></a>穩固程式設計
 當使用者選擇 **「摺疊到****大綱」** 功能表上的定義時,IDE<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningCapableLanguage.CollapseToDefinitions%2A>會調用 您的語言服務。

 調用此方法時,IDE 會<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>傳遞 指標(指向文本緩衝區的指標)和一個<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>(指向當前大綱會話的指標)。

 通過在`rgOutlnReg`參數中<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>指定 這些區域,可以調用多個大綱區域的方法。 參數`rgOutlnReg`是一個<xref:Microsoft.VisualStudio.TextManager.Interop.NewOutlineRegion>結構。 此過程允許您指定隱藏區域的不同特徵,例如特定區域是展開還是摺疊。

> [!NOTE]
> 小心隱藏新行字元。 隱藏文本應從第一行的開頭擴展到節中最後一行的最後一個字元,使最後一個新行字元可見。

## <a name="see-also"></a>另請參閱
- [如何:在舊語言服務中提供隱藏文字支援](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)
- [如何:在傳統語言服務中提供擴展的大綱支援](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)
