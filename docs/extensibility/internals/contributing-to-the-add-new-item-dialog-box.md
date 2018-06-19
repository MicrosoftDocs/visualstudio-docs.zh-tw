---
title: 提供給加入新項目對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6d8b35537828f99fe3683e03feac3960d6ca4adc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129218"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>提供給加入新項目對話方塊
專案子類型可提供完整的新目錄的項目**加入新項目**註冊對話方塊**加入項目**下的 範本`Projects`登錄子機碼。  
  
## <a name="registering-add-new-item-templates"></a>註冊加入新項目範本  
 本章節位於**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects**登錄中。 下列的登錄項目假設[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]假設專案子類型所彙總的專案。 項目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如下所列的專案。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs`子機碼包含與其中的項目進行中可用的目錄路徑的登錄項目**加入新項目**位於對話方塊。  
  
 環境會自動載入所有`AddItemTemplates`下的資料`Projects`登錄子機碼。 這可以包含基底專案實作的資料，以及適用於特定專案子類型的資料。 每個專案子類型由專案類型`GUID`。 專案子類型可以指定一組替代`Add Item`支援特定式的專案執行個體應該使用範本`VSHPROPID_ AddItemTemplatesGuid`來自列舉<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>中<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>實作以傳回 GUID專案子類型的值。 如果`VSHPROPID_AddItemTemplatesGuid`未指定屬性，基底的專案會使用 GUID。  
  
 您可以篩選中的項目**加入新項目**對話方塊中，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>專案子類型的彙總工具物件上的介面。 比方說，彙總實作資料庫專案的專案子類型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案中，可以篩選[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]特定項目從**加入新項目**，實作篩選，然後在對話方塊開啟，可以加入資料庫專案的特定項目支援`VSHPROPID_ AddItemTemplatesGuid`中<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>。 如需有關篩選和加入項目至**加入新項目**對話方塊中，請參閱[將項目加入新項目 對話方塊加入](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [通常用來擴充專案的物件 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)