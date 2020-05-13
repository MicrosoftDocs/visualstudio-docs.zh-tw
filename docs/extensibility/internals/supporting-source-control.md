---
title: 支援原始碼管理 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], supporting
ms.assetid: 567acde3-354e-4f39-8d99-0ef86c103396
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84de3120783528d209b1475477aee5087edac42b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704735"
---
# <a name="supporting-source-control"></a>支援原始檔控制
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]支援專案或編輯器的檔簽出、簽入和其他原始程式碼管理操作。 作為原始碼管理用戶端,[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]它旨在與原始碼管理套件([!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]如 )進行互動,該包為動態定義的檔案集提供存檔、版本控制和控制功能。

## <a name="in-this-section"></a>本節內容
- [原始檔控制套件的模型](../../extensibility/internals/model-for-source-control-packages.md)

 描述項目類型為支援原始程式碼管理而必須實現的介面。

- [設計決策](../../extensibility/internals/source-control-design-decisions.md)

 提供答案更改實現項目類型的方式的問題。

- [設定詳細資訊](../../extensibility/internals/source-control-configuration-details.md)

 描述支援原始碼管理如何改變項目類型的實現。

- [專案和編輯器適用的其他方針](../../extensibility/internals/additional-source-control-guidelines-for-projects-and-editors.md)

 討論項目類型和編輯器的最佳做法。

- [執行階段詳細資料](../../extensibility/internals/source-control-runtime-details.md)

 描述當使用者將專案添加到原始程式碼管理系統時如何註冊專案。

## <a name="reference"></a>參考
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>向環境或原始程式碼管理包指示檔即將在記憶體中更改或保存。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2>允許專案和層次結構在原始程式碼管理中註冊自己並獲取有關原始程式碼管理狀態的資訊。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2>在專案系統中實現,為專案檔和專案項提供原始程式碼管理。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocuments2>專案用於查詢環境以獲取在解決方案中添加、刪除或重命名檔或目錄的許可權。

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackProjectDocumentsEvents2>通知用戶端對專案檔或目錄所做的更改。

## <a name="related-sections"></a>相關章節
- [專案類型](../../extensibility/internals/project-types.md)

 提供專案概述,作為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]集成開發環境 (IDE) 的基本構建基塊。 連結指向其他主題,這些主題解釋了專案如何控制構建和編譯代碼。
