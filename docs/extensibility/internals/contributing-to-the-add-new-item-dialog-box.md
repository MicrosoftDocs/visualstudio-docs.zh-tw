---
title: 向「添加新項目」對話框投稿 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709282"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>參與「新增項目」對話框
專案子型態可以透過在**專案**註冊表子鍵下註冊 **「新增專案」** 樣本,為「**新增新專案」** 對話方塊提供完整的專案新目錄。

## <a name="register-add-new-item-templates"></a>註冊新增新項目範本
 此部分位於**HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_8.0\註冊表中的專案**下。 下面的註冊表項假定由假設[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]的專案子類型聚合的專案。 專案條目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如下。

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

 **AddItemTemplates_TemplateDirs**子鍵包含註冊表項,其中包含目錄的路徑,其中放置了"**添加新專案"** 對話框中提供的項。

 環境在**專案**註冊表子鍵下自動載入所有**AddItemTemplates**資料。 此數據可以包括基礎項目實現的數據以及特定專案子類型類型的數據。 每個專案子類型由專案類型**GUID**標識。 專案子類型可以指定一組備用的**Add Item**範本應用於特定調味品專案實例,`VSHPROPID_ AddItemTemplatesGuid`透過<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>支援實現中的枚舉來返回專案子類型的 GUID 值。 如果未指定`VSHPROPID_AddItemTemplatesGuid`該屬性,則使用基礎專案 GUID。

 您可以透過在項目子型態聚合器物件上實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>介面來 篩選「**新增新項目」** 對話方塊中的項目。 例如,通過[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]聚合專案來實現資料庫專案的專案子類型可以通過實現篩選來篩選"**添加新專案"**`VSHPROPID_ AddItemTemplatesGuid`<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]對話方塊中的特定項,進而可以通過 在中支援添加資料庫專案特定的項。 有關篩選項目並將專案加入新**項目「** 對話框的詳細資訊,請參閱」[將項目新增到「新增新項目」 對話框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)。

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [通常用於延伸項目的物件的 CATID](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
