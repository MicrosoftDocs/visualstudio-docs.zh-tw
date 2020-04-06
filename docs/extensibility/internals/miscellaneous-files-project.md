---
title: 雜項檔案專案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707090"
---
# <a name="miscellaneous-files-project"></a>其他檔案專案
當使用者打開專案項時,IDE 會分配給「雜項檔」專案不是解決方案中任何項目的成員的任何項。

 專案在確定用戶打開專案項時使用哪個編輯器方面發揮著重要作用。 專案可以設計為使用特定於專案的編輯器或標準編輯器打開某些檔。

 特定於專案的編輯器通常要求使用者具有特殊知識或使用專案的特殊介面。 有關詳細資訊,請參閱[如何:開啟特定於項目的編輯器](../../extensibility/how-to-open-project-specific-editors.md)。

 標準編輯器可以在任何項目中打開特定擴展名的任何檔。 用戶可以為專案自定義一些標準編輯器(如[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]文字編輯器),但仍保留其公共字元。 使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>方法創建標準編輯器。

 如果解決方案中沒有專案回應它可以打開專案項,IDE 會提供一個名為"雜項檔"專案的特殊專案,該專案將打開任何檔。

 此特殊專案提供在專案上下文之外打開檔。 在處理<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A>該方法期間,「雜項檔」項目始終以非常低的優先順序回應。 因此,雜項檔項目始終生成給任何可以打開檔的更高優先順序的專案。

 "雜項檔"專案不要求使用者使用 **"新項目**"對話框顯式創建它。 此外,雜項檔專案不會永久管理項目成員的清單。 它使用可選功能為每個使用者記錄最近使用的檔案的清單。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [如何︰開啟專案特定的編輯器](../../extensibility/how-to-open-project-specific-editors.md)
- [如何︰開啟標準編輯器](../../extensibility/how-to-open-standard-editors.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [新增專案與專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)
