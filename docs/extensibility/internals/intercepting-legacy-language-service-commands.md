---
title: 攔截舊語言服務命令 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707444"
---
# <a name="intercepting-legacy-language-service-commands"></a>攔截舊版語言服務命令
使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]時,可以具有文本視圖將處理的語言服務攔截命令。 這對於文本視圖未管理的語言特定行為很有用。 您可以透過從語言服務向文字檢視添加一個或多個命令篩選器來攔截這些命令。

## <a name="getting-and-routing-the-command"></a>取得與路由指令
 命令篩選器是<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>監視某些字元序列或鍵命令的物件。 您可以將多個命令篩選器與單一文字檢視相關聯。 每個文字檢視都維護一個命令篩選器鏈。 建立新的命令篩選器後,將篩選器添加到相應文本檢視的鏈中。

 調用<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>上<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>的方法 以將命令篩選器添加到鏈中。 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>時[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], 傳回另一個指令篩選器,您可以將指令篩選器不處理的命令傳遞給該篩選器。

 對指令處理,您有以下選項:

- 處理該命令,然後將該命令傳遞給鏈中的下一個命令篩選器。

- 處理該命令,不要將命令傳遞給下一個命令篩選器。

- 不要處理該命令,而是將該命令傳遞給下一個命令篩選器。

- 忽略該命令。 請勿在當前篩選器中處理它,也不要將其傳遞到下一個篩選器。

  有關語言服務應處理哪些命令的資訊,請參閱[語言服務篩選器的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。
