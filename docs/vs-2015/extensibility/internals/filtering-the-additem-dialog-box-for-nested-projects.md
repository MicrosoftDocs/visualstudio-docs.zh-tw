---
title: 篩選嵌套專案的 AddItem 對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538092"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>篩選巢狀專案的 AddItem 對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當您針對嵌套專案顯示 [ **AddItem** ] 對話方塊時，父專案可以控制要在對話方塊中顯示的專案。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>介面可讓您篩選將會出現在**AddItem**對話方塊中的節點。 當子專案顯示 [ **AddItem** ] 對話方塊時，父系可以執行 `IVsFilterAddProjectItemDlg` 介面並篩選以其他方式顯示在子專案中的專案。  
  
 當專案依功能分組時，在特定的父專案下，您可以在 `IVsFilterAddProjectItemDlg` 使用者于嵌套專案的快捷方式功能表上選取 [ **加入專案專案** ] 時執行。 `IvsFilterAddProjectItemDlg displays`只執行該群組專屬的專案專案或檔案。 其他群組的專案專案會從對話方塊中篩選出來，即使它們儲存在相同的目錄中也一樣。  
  
 當使用者開啟子系的 [ **AddItem** ] 對話方塊時，會呼叫父專案的介面實作為 `IVsFilterAddProjectItemDlg` 。  
  
 `IVsFilterAddProjectItemDlg`介面也可以依類別來執行篩選。 如需詳細資訊，請參閱將 [專案加入至加入新專案對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) 以及 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [在 [加入新專案] 對話方塊中加入專案](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [巢狀專案](../../extensibility/internals/nesting-projects.md)
