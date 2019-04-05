---
title: 提供給加入新項目對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "58939863"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>參與新增項目對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

專案子類型可以提供完整的新目錄的項目**加入新項目**對話方塊中，藉由註冊**加入項目**下的 範本`Projects`登錄子機碼。  
  
## <a name="registering-add-new-item-templates"></a>註冊加入新項目範本  
 本章節位於**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects**在登錄中。 底下的登錄項目假設[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]假設專案子類型所彙總的專案。 項目[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]如下所列的專案。  
  
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
  
 `AddItemTemplates\TemplateDirs`子機碼包含的項目進行中可用的目錄路徑的登錄項目**加入新項目**位於對話方塊。  
  
 環境會自動載入的所有`AddItemTemplates`下的資料`Projects`登錄子機碼。 這可能包括針對基底專案實作資料，以及特定專案子類型的資料。 每個專案子類型由專案類型`GUID`。 專案子類型可以指定一組替代`Add Item`範本應該用於特定 flavored 的專案執行個體支援`VSHPROPID_ AddItemTemplatesGuid`列舉<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>在<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>傳回 GUID 的實作專案子類型的值。 如果`VSHPROPID_AddItemTemplatesGuid`屬性未指定，會使用 GUID 的基底專案。  
  
 您可以篩選中的項目**加入新項目**對話方塊中，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>專案子類型的彙總工具物件上的介面。 比方說，實作所彙總的資料庫專案的專案子類型[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]專案中，可以篩選[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]中的特定項目**加入新項目**對話方塊中，實作篩選，然後在開啟，可以加入藉由支援資料庫專案的特定項目`VSHPROPID_ AddItemTemplatesGuid`在<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>。 如需有關篩選和新增項目**加入新項目** 對話方塊中，請參閱[將項目加入 [加入新項目] 對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [通常用來擴充專案的物件 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
