---
title: 支援嵌套專案的 Wizard |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e498f21499f4b07bf77bb79829fc6d92227f1f2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721426"
---
# <a name="wizard-support-for-nested-projects"></a>巢狀專案的精靈支援
IDE 會執行兩個可供執行嵌套專案之父專案的嚮導： [**新增專案**嚮導] 和 [**加入專案**] [wizard]。

 如果使用者選取 [新增**專案**]，然後按一下 [檔案] 功能表上的 [**新增**專案 **]，或**選取 [新增] 並以滑鼠右鍵按一下方案總管中的 [**新專案**] 來啟動 **[新增專案**]，IDE 就會執行**AddProject**命令和父專案的**AddProject**命令執行會傳回範本專案檔，或包含一組內容參數的 wizard （.vsz）檔案。

 同樣地，父專案的**AddItem**程式執行程式會傳回具有一組不同內容參數的 .vsz 檔案。

 如需有關嚮導的詳細資訊，請參閱[Wizard （.Vsz）](../../extensibility/internals/wizard-dot-vsz-file.md)檔案、[內容參數](../../extensibility/internals/context-parameters.md)和[註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)。

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [巢狀專案](../../extensibility/internals/nesting-projects.md)