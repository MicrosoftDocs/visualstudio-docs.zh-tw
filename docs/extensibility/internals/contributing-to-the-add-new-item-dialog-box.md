---
title: 參與 [加入新專案] 對話方塊 |Microsoft Docs
description: 在 [專案] 登錄子機碼下註冊 [新增專案範本]，以瞭解如何參與 Visual Studio 中的 [加入新專案] 對話方塊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3fdc5705cad0ec696a520350042d7f18aaec146
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884633"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>[加入新專案] 對話方塊
專案子類型可以在 [**專案**] 登錄子機碼下註冊 [新增 **專案**] 範本，為 [**加入新專案**] 對話方塊提供完整的新目錄。

## <a name="register-add-new-item-templates"></a>註冊新增專案範本
 此區段位於登錄的 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** 下。 下列登錄專案會假設 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案是由假設專案子類型所匯總。 專案的專案如下所 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 示。

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

 **AddItemTemplates\TemplateDirs** 子機碼包含登錄專案，其中包含可在 [**加入新專案**] 對話方塊中提供之專案的目錄路徑。

 環境會自動載入 **Projects** 登錄子機碼下的所有 **AddItemTemplates** 資料。 此資料可以包含基底專案的資料，以及特定專案子類型類型的資料。 每個專案子類型都是由專案類型 **GUID** 所識別。 專案子類型可以指定要針對特定的 flavored 專案實例使用替代的 **新增專案** 樣板集合，方法是 `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> 在實值中支援列舉 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> ，以傳回專案子類型的 GUID 值。 如果 `VSHPROPID_AddItemTemplatesGuid` 未指定屬性，則會使用基底專案 GUID。

 您可以在 [ **加入新專案** ] 對話方塊中，藉由在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> 專案子類型匯總工具物件上執行介面，來篩選項目。 例如，藉由匯總專案來執行資料庫專案的專案子類型 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ，可以藉 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 由執行篩選來篩選 [ **加入新專案** ] 對話方塊中的特定專案，然後藉由在中支援來加入資料庫專案特定專案 `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> 。 如需在 [ **加入新專案** ] 對話方塊中篩選和加入專案的詳細資訊，請參閱將 [專案加入至加入新](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)專案對話方塊。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [通常用來擴充專案的物件 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
