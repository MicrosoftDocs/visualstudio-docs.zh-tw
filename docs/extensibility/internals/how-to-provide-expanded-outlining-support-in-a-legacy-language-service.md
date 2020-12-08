---
title: 提供語言服務中的大綱支援 |Microsoft Docs
description: 瞭解如何藉由新增編輯器控制的大綱區域和用戶端控制的大綱區域，在舊版語言服務中提供展開大綱的支援。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], outlining support
- language services, supporting outlining
- outlining, supporting
ms.assetid: df759e89-8193-418c-8038-6626304d387b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9397ff17ba80368a86ba03260b3c5af3759bfe8d
ms.sourcegitcommit: 2f964946d7044cc7d49b3fc10b413ca06cb2d11b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/07/2020
ms.locfileid: "96761357"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>如何：在舊版語言服務中提供展開大綱支援
有兩個選項可以擴充您語言的大綱支援，除了支援 [折迭 **至定義** ] 命令以外。 您可以新增編輯器控制的大綱區域，以及新增用戶端控制的大綱區域。

## <a name="adding-editor-controlled-outline-regions"></a>新增編輯器控制的大綱區域
 您可以使用此方法來建立大綱區域，然後允許編輯器處理區域是否展開、折迭等等。 在提供大綱支援的兩個選項中，此選項是最不健全的選項。 針對此選項，您可以使用在指定的文字範圍中建立新的外框區域 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> 。 建立此區域之後，其行為會由編輯器控制。 您可以使用下列程式來執行編輯器控制的大綱區域。

### <a name="to-implement-an-editor-controlled-outline-region"></a>若要執行編輯器控制的大綱區域

1. 呼叫 `QueryService`<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     這會傳回的指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> 。

2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> ，傳遞給定文字緩衝區的指標。 這會傳回 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 緩衝區的物件指標。

3. <xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A>針對的 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 指標呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession> 。

4. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A> ，一次新增一個或多個新的外框區域。

     這個方法可讓您指定要外框的文字範圍、是否移除或保留現有的外框區域，以及大綱區域是否預設為展開或折迭。

## <a name="add-client-controlled-outline-regions"></a>新增用戶端控制的大綱區域
 您可以使用此方法來執行 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 與語言服務所使用的用戶端控制 (或智慧型) 大綱 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 。 管理本身大綱的語言服務會監視文字緩衝區內容，以在舊的大綱區域無效時予以終結，並視需要建立新的外框區域。

### <a name="to-implement-a-client-controlled-outline-region"></a>若要執行用戶端控制的大綱區域

1. `QueryService`的呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager> 。 這會傳回的指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager> 。

2. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A> ，傳遞給定文字緩衝區的指標。 這會決定緩衝區是否已經有隱藏的文字會話。

3. 如果文字會話已經存在，則您不需要建立一個，而且 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 會傳回現有物件的指標。 使用此指標來列舉和建立大綱區域。 否則，呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 以建立緩衝區的隱藏文字會話。 傳回物件的指標 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> 。

    > [!NOTE]
    > 當您呼叫時， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> 可以指定隱藏文字用戶端 (也就是 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>) 的物件。 當使用者展開或折迭隱藏的文字或外框區域時，此用戶端會通知您。

4. 呼叫 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> 結構) 參數：在結構的成員中指定的值， <xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE> `iType` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 表示您要建立外框區域，而不是隱藏的區域。 指定區域是否在結構的成員中是由用戶端控制或編輯的 `dwBehavior` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 。 您的智慧型大綱執行可以混合使用編輯器和用戶端控制的大綱區域。 指定在結構的成員中折迭大綱區域（例如 "..."）時所顯示的橫幅文字。 `pszBanner` <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> 編輯器的隱藏區域預設橫幅文字為「...」。
