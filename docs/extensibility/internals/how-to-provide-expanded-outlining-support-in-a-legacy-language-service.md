---
title: 在語言服務中提供概述支援 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 37deafa92477289a2124ecee101dd254e68ef01d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707961"
---
# <a name="how-to-provide-expanded-outlining-support-in-a-legacy-language-service"></a>如何:在傳統語言服務中提供擴展的大綱支援
除了支援 **「摺疊到定義」** 命令之外,還有兩個選項可以擴展對語言的支援。 您可以添加編輯器控制的大綱區域,並添加用戶端控制的大綱區域。

## <a name="adding-editor-controlled-outline-regions"></a>新增編輯器控制的大綱區域
 使用此方法創建大綱區域,然後允許編輯器處理區域是否展開、摺疊等。 在提供大綱支援的兩個選項中,此選項最不健壯。 對於此選項,使用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>在指定的文本範圍內創建新的大綱區域。 創建此區域後,其行為由編輯器控制。 使用以下過程實現編輯器控制的大綱區域。

### <a name="to-implement-an-editor-controlled-outline-region"></a>實現編輯器控制的大綱區域

1. 通話`QueryService`<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>

     這將返回指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>的指標。

2. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, 傳入給定文字緩衝區的指標。 這將返回指向緩衝區<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件的指標。

3. 調用<xref:System.Runtime.InteropServices.Marshal.QueryInterface%2A><xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession><xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession>指向的指標。

4. 調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsOutliningSession.AddOutlineRegions%2A>一次添加一個或多個新大綱區域。

     此方法允許您指定要大綱的文本範圍、是否刪除或保留現有大綱區域,以及大綱區域是默認情況下展開還是摺疊。

## <a name="add-client-controlled-outline-regions"></a>新增用戶端控制的大綱區域
 使用此方法實現用戶端控制(或智慧)大綱,如[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]和[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]語言服務所使用的大綱。 管理自己的大綱的語言服務會監視文本緩衝區內容,以便在舊大綱區域無效時銷毀它們,並根據需要創建新的大綱區域。

### <a name="to-implement-a-client-controlled-outline-region"></a>實現用戶端控制的大綱區域

1. 呼叫`QueryService`<xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>。 這將返回指向<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>的指標。

2. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, 傳入給定文字緩衝區的指標。 這將確定緩衝區是否已存在隱藏文本會話。

3. 如果文本會話已存在,則無需創建一個會話,並返回指向現有<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>物件的指標。 使用此指標枚舉並創建輪廓區域。 否則,調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>以創建緩衝區的隱藏文本會話。 返回指向對象<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>的指標。

    > [!NOTE]
    > 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A>時 ,可以指定隱藏文字用戶端<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>(即物件)。 當使用者展開或摺疊隱藏文本或大綱區域時,此用戶端將通知您。

4. 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A>結構)參數:在<xref:Microsoft.VisualStudio.TextManager.Interop.HIDDEN_REGION_TYPE>`iType`<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構成員中指定 值以指示您正在創建大綱區域,而不是隱藏區域。 指定區域是用戶端控制還是`dwBehavior`<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構成員中的編輯器控制。 智慧大綱實現可以包含編輯器和用戶端控制的大綱區域的組合。 指定在大綱區域摺疊時顯示的橫幅文本,如`pszBanner`<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>結構成員中的"..."。 編輯對隱藏區域的預設橫幅文本為"..."。
