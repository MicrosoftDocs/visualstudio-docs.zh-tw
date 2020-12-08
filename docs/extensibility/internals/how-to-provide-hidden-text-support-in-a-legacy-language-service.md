---
title: 在舊版語言服務中提供隱藏文字支援
description: 瞭解如何藉由新增編輯器控制或用戶端控制的隱藏文字區域，在舊版語言服務中提供隱藏文字支援。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 1f51f8e0c5ca268c1171804f663e5d01bd7c2530
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761305"
---
# <a name="how-to-provide-hidden-text-support-in-a-legacy-language-service"></a>如何：在舊版語言服務中提供隱藏文字支援
除了外框區域外，您還可以建立隱藏的文字區域。 隱藏的文字區域可以是由用戶端控制或編輯編輯器，而且可用來完全隱藏文字的區域。 編輯器會將隱藏的區域顯示為水平線條。 其中一個範例就是在 HTML 編輯器中只會看到 [ **腳本** ]。

## <a name="to-implement-a-hidden-text-region"></a>若要執行隱藏的文字區域

1. `QueryService`的呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 。

     這會傳回的指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> 。

2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> ，傳遞給定文字緩衝區的指標。 這會決定緩衝區是否已經有隱藏的文字會話。

3. 如果已經存在，則您不需要建立一個，而且 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 會傳回現有物件的指標。 使用這個指標來列舉和建立隱藏的文字區域。 否則，呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 以建立緩衝區的隱藏文字會話。

     傳回物件的指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 。

    > [!NOTE]
    > 當您呼叫時， `CreateHiddenTextSession` 可以指定隱藏文字用戶端 (也就是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>) 。 當使用者展開或折迭隱藏文字或大綱時，隱藏的文字用戶端會通知您。

4. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 以一次新增一個或多個新的大綱區域，在 `reHidReg` () 參數中指定下列資訊 <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> ：

    1. 在結構的成員中指定的值， `hrtConcealed` `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 表示您要建立隱藏的區域，而不是外框區域。

        > [!NOTE]
        > 隱藏隱藏區域時，編輯器會自動顯示隱藏區域周圍的行，以指出其存在。

    2. 指定區域是否在結構的成員中是由用戶端控制或編輯 `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 。 您的智慧型大綱執行可以混合使用編輯器和用戶端控制的大綱和隱藏文字區域。
