---
title: 篩選巢狀專案 AddItem 對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50a9491dad92e4f1dd090a6de1ebf48ef1b88085
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>篩選巢狀專案 AddItem 對話方塊
當您顯示**AddItem**巢狀專案中，父專案 對話方塊可以控制哪些項目會顯示在對話方塊中。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>介面可讓您篩選會在節點**AddItem**  對話方塊。 當子專案顯示**AddItem**對話方塊中，可以實作父`IVsFilterAddProjectItemDlg`介面和篩選器會顯示在子系的專案中的項目。  
  
 當專案在專案特定父系下的函式分組時，您可以實作`IVsFilterAddProjectItemDlg`當使用者選取**加入專案項目**中巢狀專案的捷徑功能表上。 實作`IvsFilterAddProjectItemDlg displays`只有專案項目，或該群組的特定檔案。 其他群組的專案項目會從篩選掉對話方塊中，即使它們儲存在相同的目錄。  
  
 當使用者開啟**AddItem**對話方塊子系，父專案實作`IVsFilterAddProjectItemDlg`介面稱為。  
  
 `IVsFilterAddProjectItemDlg`介面也可以實作依類別篩選。 如需詳細資訊，請參閱[將項目加入新項目 對話方塊加入](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)和[註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)