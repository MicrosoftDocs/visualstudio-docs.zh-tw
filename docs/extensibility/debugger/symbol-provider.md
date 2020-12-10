---
title: 符號提供者 |Microsoft Docs
description: 瞭解 Visual Studio 提供的符號提供者，以便讓運算式評估工具評估變數和運算式。
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 043014ebababd990c9cae03f28cb1b642d576071
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996041"
---
# <a name="symbol-provider"></a>符號提供者
運算式評估工具的執行必須存取語言編譯器所產生的符號 debug 資訊，才能評估變數和運算式。 其運作方式是使用符號提供者的介面 (SP) ，也稱為符號處理常式。

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用程式資料庫 (PDB) 符號檔案格式，為 managed 程式碼和機器碼提供 Sp。 除非您的程式需要使用以自訂格式儲存的符號，否則建議您使用提供的 SPs [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。

## <a name="implementation-notes"></a>實作附註
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Debug engine 預期會使用 Common Language Runtime (CLR) 介面來與 SPs 交談。 因此，將會使用 Visual Studio debug engine 的 SP 必須支援 CLR。 您可以在 debugref.doc （屬於的一部分）中找到所有 CLR 偵錯工具介面的完整清單 [!INCLUDE[winsdklong](../../deployment/includes/winsdklong_md.md)] 。

 如果您的 SP 只會與您的自訂「偵測引擎」搭配運作，您可以根據您的 debug engine 需求，視需要執行 SP。

## <a name="see-also"></a>另請參閱
- [偵錯工具元件](../../extensibility/debugger/debugger-components.md)
