---
title: 在 [加入新專案] 對話方塊中加入目錄 |Microsoft Docs
description: 瞭解如何使用登入指令檔登錄目錄，將目錄新增至 Visual Studio 中的 [加入新專案] 對話方塊。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 131c04d1025885c59a884220a61098b2c85dd5a1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079146"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>將目錄新增至加入新專案對話方塊
下列程式碼範例示範如何為 [ **加入新專案** ] 對話方塊註冊一組新的目錄。 每個專案的 [ **加入新專案** ] 對話方塊的目錄都是不同的。 因此，這些目錄會在 [ **專案** ] 子機碼下註冊（可在 **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects** 中找到）。

## <a name="registry-script"></a>登入指令檔

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 `%Template_Path%`值指定包含專案範本的目錄完整路徑。 這些範本可以是 *.vsz* 檔案或要複製的典型範本檔案。

 `SortPriority`值指定排序優先權。

## <a name="add-items-to-an-existing-project"></a>將專案加入至現有的專案
 您也可以將專案加入至現有的專案。 例如， [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 您可以在專案中，將專案加入至 *\<root> \Program Files\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* 資料夾。 在此情況下， `%GUID_Project%` 是 c # 專案的 GUID ( {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} ) 。

 您也可以藉由程式設計專案子類型來擴充現有的專案。 您可以使用專案子類型來擴充專案，而不需要撰寫新的專案類型。 如需專案子類型的詳細資訊，請參閱 [專案子類型](../../extensibility/internals/project-subtypes.md)。

## <a name="see-also"></a>另請參閱
- [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [在 [加入新專案] 對話方塊中加入專案](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [將目錄新增至新增專案對話方塊](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
