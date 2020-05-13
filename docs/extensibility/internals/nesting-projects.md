---
title: 巢狀專案 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 814780fa8e7e57a022a75b2e09115cfa55a1b8be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707036"
---
# <a name="nesting-projects"></a>巢狀專案
使用 VS 包的企業應用程式開發人員可以使用*專案嵌套*來方便地將[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]類似類型的專案 分組在一起。 例如,企業範本專案使用嵌套專案將專案分組到類別中。 業務外觀專案、Web UI 專案等被分組到一個類別中。

 在這種情況下,開發人員可以嵌套在每個父專案下的專案數量沒有限制,儘管開發人員可以以程式設計方式提供限制。 這種類型的分組也可以遞歸,在這種情況下,與子項目類型相同的專案可以嵌套在子項下,成為子項的子項,該子專案是父項的子專案。

 專案嵌入的固有部份[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 您必須編寫程式碼才能在子項目中啟用嵌套和子專案嵌套。 父專案是使用其自己的 GUID 創建和註冊的特殊的 VSPackage 或專案類型,其中包括實現專案嵌套所需的代碼。

 您可以在[「如何:實現嵌套專案](../../extensibility/internals/how-to-implement-nested-projects.md)」中找到有關如何嵌套專案的範例。

## <a name="nested-projects-example"></a>巢狀項目範例
 ![巢狀專案解決方案](../../extensibility/internals/media/vsnestedprojects.gif "vs 巢狀項目")巢狀項目範例

## <a name="see-also"></a>另請參閱
- [卸載並重新載入巢狀專案的考量](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [巢狀專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [實作巢狀專案的命令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [篩選巢狀專案的 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [檢查清單︰建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [內容參數](../../extensibility/internals/context-parameters.md)
- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
