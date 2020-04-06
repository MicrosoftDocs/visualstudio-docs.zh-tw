---
title: 源代碼管理執行時詳細資訊 |微軟文件
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705045"
---
# <a name="source-control-runtime-details"></a>原始檔控制的執行階段詳細資料
當使用者將專案中的檔案添加到原始碼管理或透過自動化控制器(如精靈)時,專案將添加到原始程式碼管理。 專案本身未指定它處於原始程式碼控制之下;因此,專案本身並未指定專案處於原始程式碼管理之下。它支援原始碼管理,但必須手動添加到原始程式碼管理中。

## <a name="registering-with-a-source-control-package"></a>註冊原始碼管理員
 將專案中的檔案添加到原始碼管理時,環境將呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>為您提供四個不透明字串,這些字串被原始程式碼管理系統用作 Cookie。 將這些字串儲存在專案檔中。 在啟動項目類型時,這些字串應傳遞到源控制存根(管理原始程式碼管理套件的可視化 Studio 元件),透過調<xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>用 啟動專案類型。 這反過來載入適當的源碼管理包,並將呼叫轉到其實現`IVsSccManager2::RegisterSccProject`。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [支援原始檔控制](../../extensibility/internals/supporting-source-control.md)
