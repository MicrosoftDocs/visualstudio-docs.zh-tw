---
title: 原始檔控制執行時間詳細資料 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705045"
---
# <a name="source-control-runtime-details"></a>原始檔控制的執行階段詳細資料
當使用者將專案中的檔案新增至原始檔控制，或透過 automation 控制器（例如 wizard），將專案加入至原始檔控制。 專案未指定其本身是在原始檔控制之下;它支援原始檔控制，但必須手動新增。

## <a name="registering-with-a-source-control-package"></a>向原始檔控制套件註冊
 當專案中的檔案新增至原始檔控制時，環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> 以提供四個不透明的字串，做為原始檔控制系統用的 cookie。 將這些字串儲存在專案檔中。 您應藉由呼叫，將這些字串傳遞至原始檔控制 Stub (管理原始檔控制封裝) 的 Visual Studio 元件 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> 。 然後，這會載入適當的原始檔控制封裝，並將呼叫轉送至的實作為 `IVsSccManager2::RegisterSccProject` 。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
