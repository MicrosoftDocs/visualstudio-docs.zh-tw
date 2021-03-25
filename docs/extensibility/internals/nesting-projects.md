---
title: 嵌套專案 |Microsoft Docs
description: 瞭解如何嵌套專案，讓使用您 VSPackage 的應用程式開發人員在 Visual Studio 中將類似的專案類型群組在一起。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project nesting
- nested projects
- projects [Visual Studio SDK], child projects
- projects [Visual Studio SDK], nesting
ms.assetid: 12cce037-9840-4761-845e-5abd5fb317b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 30b562cac794b7ab960f055fe67a5d0cc4ec871f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105063213"
---
# <a name="nesting-projects"></a>巢狀專案
使用您的 VS 封裝的企業應用程式開發人員可以 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 使用 *專案嵌套*，輕鬆地在中將類似的專案群組在一起。 例如，企業範本專案會使用嵌套專案將專案分組為類別。 商務外觀專案、Web UI 專案等會在一個類別中群組在一起。

 在此案例中，開發人員可以在每個父專案下嵌套的專案數目沒有任何限制，但開發人員可以用程式設計的方式提供限制。 這種類型的群組也可以遞迴進行，在這種情況下，與子專案相同類型的專案可以嵌套在子專案下，成為子專案的子專案，也就是父系的子專案。

 專案嵌套不是的內建部分 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 您必須撰寫程式碼，才能在子專案內啟用嵌套和子專案的嵌套。 父專案是特殊的 VSPackage 或專案類型，使用自己的 GUID 建立和註冊，其中包含執行專案嵌套所需的程式碼。

 您可以在 how [to：執行嵌套專案](../../extensibility/internals/how-to-implement-nested-projects.md)中找到如何將專案嵌套的範例。

## <a name="nested-projects-example"></a>嵌套專案範例
 ![嵌套專案方案](../../extensibility/internals/media/vsnestedprojects.gif "vsNestedProjects") 嵌套專案範例

## <a name="see-also"></a>另請參閱
- [卸載並重新載入巢狀專案的考量](../../extensibility/internals/considerations-for-unloading-and-reloading-nested-projects.md)
- [巢狀專案的精靈支援](../../extensibility/internals/wizard-support-for-nested-projects.md)
- [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [實作巢狀專案的命令處理](../../extensibility/internals/implementing-command-handling-for-nested-projects.md)
- [篩選巢狀專案的 AddItem 對話方塊](../../extensibility/internals/filtering-the-additem-dialog-box-for-nested-projects.md)
- [檢查清單：建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)
- [內容參數](../../extensibility/internals/context-parameters.md)
- [精靈檔 (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
