---
title: 巢狀專案的精靈支援 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add Item wizard
- nested projects, wizard support
- New Project wizard
ms.assetid: 1b496acc-b326-4cdb-bb48-e3b5c6f12e05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7f37700d908167ebef8c071021558822bdce173
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703199"
---
# <a name="wizard-support-for-nested-projects"></a>巢狀專案的精靈支援
IDE 運行嵌套專案的父專案可以實現的兩個嚮導:**新專案**嚮導和 **「添加專案**」嚮導。

 如果使用者通過選擇 **「新增專案**」並按下「檔案」功能表上**的「新專案**」,或者透過選擇「解決方案資源管理器中的 **」添加**和右鍵按一次**新專案**「來啟動**新專案**精靈,則 IDE 將運行**AddProject**命令,父專案的**AddProject**命令的實現返回範本專案檔,或返回具有一組上下文參數的嚮導 (.vsz) 檔。

 同樣,父專案的**AddItem**嚮導的實現返回具有一組不同上下文參數的 .vsz 檔。

 有關嚮導的詳細資訊,請參閱[嚮導 (。Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md),[內容與](../../extensibility/internals/context-parameters.md)[註冊項目與專案樣本](../../extensibility/internals/registering-project-and-item-templates.md)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>
- [巢狀專案](../../extensibility/internals/nesting-projects.md)
