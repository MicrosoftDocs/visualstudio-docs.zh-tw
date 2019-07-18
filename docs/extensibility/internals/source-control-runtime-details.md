---
title: 原始檔控制執行階段詳細資料 |Microsoft Docs
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
ms.openlocfilehash: 1e84fd82c5da5deea2d718baf67799e5bf877131
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322554"
---
# <a name="source-control-runtime-details"></a>原始檔控制的執行階段詳細資料
當使用者將檔案加入專案中加入原始檔控制，或透過自動化控制站，例如精靈時，專案會加入原始檔控制。 專案未指定為其本身，是在原始檔控制它支援原始檔控制，但必須以手動方式新增至它。

## <a name="registering-with-a-source-control-package"></a>使用原始檔控制套件註冊
 當您的專案中的檔案新增至原始檔控制時，環境會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>為您提供四個為 cookie 由原始檔控制系統的不透明字串。 將這些字串儲存在您的專案檔中。 這些字串應該傳遞至原始檔控制虛設常式 （管理原始檔控制套件的 Visual Studio 元件） 在啟動時的專案類型呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>。 這接著會載入適當的原始檔控制封裝，並會轉送它的實作呼叫`IVsSccManager2::RegisterSccProject`。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)