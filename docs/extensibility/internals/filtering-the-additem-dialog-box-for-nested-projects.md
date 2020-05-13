---
title: 篩選嵌套專案的「新增項目」對話框 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708389"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>篩選嵌套項目的「新增項目」對話框
當您為嵌套項目顯示 **「添加專案」** 對話框時,父專案可以控制對話框中顯示的專案。

 該<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>介面允許您篩選將在 **「新增項目」** 對話方塊中的節點。 當子項目顯示 **「添加項目**」對話框時,父項可以`IVsFilterAddProjectItemDlg`實現介面和篩選器項,否則這些項將顯示在子項的專案中。

 當專案按特定父專案下的函數分組時,可以在用戶選擇嵌套`IVsFilterAddProjectItemDlg`專案中的快捷功能表上**添加專案項**時實現。 僅`IvsFilterAddProjectItemDlg displays`實現特定於該組的專案項或檔。 其他組的專案項從對話框中篩選出來,即使它們存儲在同一目錄中也是如此。

 當使用者為子級打開 **「添加專案**」對話框時,將調用父專案`IVsFilterAddProjectItemDlg`的介面實現。

 介面`IVsFilterAddProjectItemDlg`還可以按類別實現篩選。 有關詳細資訊,請參閱[將專案新增到「新增新項目」對話框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)和[註冊項目和專案樣本](../../extensibility/internals/registering-project-and-item-templates.md)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [新增項目新增項目新增項目對話框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [註冊項目和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [巢狀專案](../../extensibility/internals/nesting-projects.md)
