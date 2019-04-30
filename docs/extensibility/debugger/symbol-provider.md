---
title: 符號提供者 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ea31d6bcd8c055756a49c46f8fb4b3f377aaade8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62912891"
---
# <a name="symbol-provider"></a>符號提供者
運算式評估工具實作必須存取以評估變數和運算式語言編譯器所產生的符號偵錯資訊。 它會藉由使用介面的符號提供者 (SP)，也稱為符號處理常式。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 提供 managed 程式碼，以及使用程式資料庫 (PDB) 符號的檔案格式的原生程式碼的預存程序。 除非沒有強式需要為您的程式使用自訂的格式儲存的符號，而是建議您在使用所提供的預存程序[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。

## <a name="implementation-notes"></a>實作注意事項
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，預存程序，使用 Common Language Runtime (CLR) 介面與預期的偵錯引擎。 如此一來，Visual Studio 偵錯引擎會使用預存程序必須支援的 CLR。 所有 CLR 偵錯介面的完整清單可在 debugref.doc，也就是組件的[!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)]。

 如果您的預存程序只會使用您自訂的偵錯引擎，您可以在根據您的偵錯引擎的需求適當地實作預存程序。

## <a name="see-also"></a>另請參閱
- [偵錯工具元件](../../extensibility/debugger/debugger-components.md)