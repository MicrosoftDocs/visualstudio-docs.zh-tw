---
title: 符號提供者 :微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 31b90846d9494ee046cf9dc4a3e5de9ff033ea3f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712813"
---
# <a name="symbol-provider"></a>符號提供者
運算式賦值器實現必須造訪語言編譯器生成的符號調試資訊,以便計算變數和運算式。 它通過使用符號提供程式 (SP) 的介面(也稱為符號處理程式)來這樣做。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]使用程式資料庫 (PDB) 符號檔案格式為託管代碼和本機代碼提供 SP。 除非程式非常需要使用以自訂格式儲存的符號,否則建議您使用[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]提供的 SP。

## <a name="implementation-notes"></a>實作附註
 除錯[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]引擎需要使用通用語言執行時 (CLR) 介面與 SP 進行對話。 因此,將配合 Visual Studio 調試引擎工作的 SP 必須支援 CLR。 所有 CLR 除錯介面的完整清單可以在 debugref.doc 中找到[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)],這是的一部分。

 如果您的 SP 將僅與自訂調試引擎一起使用,則可以根據調試引擎的需要,實現您認為合適的 SP。

## <a name="see-also"></a>另請參閱
- [除錯器元件](../../extensibility/debugger/debugger-components.md)
