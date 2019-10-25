---
title: 原始檔控制執行時間詳細資料 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d2469bc25fabd9659e09d6ca841ebc44a743cca
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723400"
---
# <a name="source-control-runtime-details"></a>原始檔控制的執行階段詳細資料
當使用者將專案中的檔案加入至原始檔控制，或透過 automation 控制器（例如 wizard）時，會將專案新增至原始檔控制。 專案不會針對其本身指定其在原始檔控制之下;它支援原始檔控制，但必須以手動方式加入。

## <a name="registering-with-a-source-control-package"></a>向原始檔控制封裝進行註冊
 當專案中的檔案加入至原始檔控制時，環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>，以提供您四個不透明的字串，供原始檔控制系統用來做為 cookie。 將這些字串儲存在您的專案檔中。 呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> 時，應該將這些字串傳遞至原始檔控制存根（管理原始檔控制封裝的 Visual Studio 元件）。 這會接著載入適當的原始檔控制封裝，並將呼叫轉送到其 `IVsSccManager2::RegisterSccProject` 的執行。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)