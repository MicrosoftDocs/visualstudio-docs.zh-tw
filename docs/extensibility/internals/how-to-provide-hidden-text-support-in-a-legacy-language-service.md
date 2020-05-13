---
title: 在舊語言服務中提供隱藏文字支援
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hidden text, supporting
- editors [Visual Studio SDK], hidden text
- language services, implementing hidden text regions
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a9d5fe85932f87eb68b6b5a0f5868ebbf8f2b5f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707933"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>如何:在舊語言服務中提供隱藏文字支援
除了大綱區域之外,還可以創建隱藏的文本區域。 隱藏文字區域可以是用戶端控制或編輯器控制,並用於完全隱藏文本區域。 編輯器將隱藏區域顯示為水平線。 例如 HTML 編輯器中的 **「僅文稿」** 檢視。

## <a name="to-implement-a-hidden-text-region"></a>實現隱藏文字區域

1. 呼叫`QueryService`<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。

     這將返回指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>的指標。

2. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, 傳入給定文字緩衝區的指標。 這將確定緩衝區是否已存在隱藏文本會話。

3. 如果一個已存在,則不需要創建一個指標,並返回指向現有<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件的指標。 使用此指標枚舉並創建隱藏的文本區域。 否則,調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>以創建緩衝區的隱藏文本會話。

     返回指向對象<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>的指標。

    > [!NOTE]
    > 呼叫`CreateHiddenTextSession`時, 可以指定隱藏文字客戶<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>端(即 。 當使用者展開或摺疊隱藏文本或大綱時,隱藏文本用戶端會通知您。

4. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>一次新增一個或多個新大綱區域,`reHidReg`在<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>( ) 參數中指定以下資訊:

    1. `hrtConcealed`<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構`iType`成員中指定值,以指示您正在建立隱藏區域,而不是大綱區域。

        > [!NOTE]
        > 隱藏區域時,編輯器會自動在隱藏區域周圍顯示行,以指示其存在。

    2. 指定區域是用戶端控制還是`dwBehavior`<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構成員中的編輯器控制。 智慧大綱實現可以包含編輯器和用戶端控制大綱和隱藏文本區域的組合。
