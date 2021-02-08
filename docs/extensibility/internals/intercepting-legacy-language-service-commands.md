---
title: 攔截舊版語言服務命令 |Microsoft Docs
description: 瞭解如何在 Visual Studio 中使用命令篩選器來攔截舊版語言服務命令，並新增語言特定的行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6a759f0cef7329d14d7d1472d38f662c0206448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839790"
---
# <a name="intercepting-legacy-language-service-commands"></a>攔截舊版語言服務命令
使用 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，您可以讓語言服務攔截文字視圖原本會處理的命令。 這適用于文字視圖無法管理的語言特定行為。 您可以從語言服務將一或多個命令篩選器新增至文字視圖，以攔截這些命令。

## <a name="getting-and-routing-the-command"></a>取得和路由傳送命令
 命令篩選器是 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 監視特定字元序列或按鍵命令的物件。 您可以將一個以上的命令篩選器與單一文字視圖產生關聯。 每個文字視圖都會維護一鏈的命令篩選準則。 建立新的命令篩選器之後，您可以將篩選新增至適當文字視圖的鏈。

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>在上呼叫方法 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ，將您的命令篩選器新增至鏈。 當您呼叫時 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> ， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 會傳回另一個命令篩選準則，您可以傳遞命令篩選器未處理的命令。

 您有下列命令處理選項：

- 處理命令，然後將命令傳遞至鏈中的下一個命令篩選準則。

- 處理命令，並不要將命令傳遞給下一個命令篩選器。

- 請勿處理命令，但是將命令傳遞給下一個命令篩選器。

- 略過命令。 請勿在目前的篩選中處理它，也不要將它傳遞給下一個篩選準則。

  如需語言服務應處理哪些命令的相關資訊，請參閱 [語言服務篩選的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。
