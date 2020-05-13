---
title: 將目錄新增到「新增新項目」對話框 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710258"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>新增項目新增的項目中
以下代碼示例演示如何為 **「添加新專案」** 對話方塊註冊一組新的目錄。 **"添加新項目"** 對話框的目錄對於每個專案都不同。 因此,目錄在 **「項目**子鍵」下註冊,HKEY_LOCAL_MACHINE_SOFTWARE_Microsoft_VisualStudio_8.0Exp_**專案**。

## <a name="registry-script"></a>註冊表文稿

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

 該`%Template_Path%`值指定包含專案範本的目錄的完整路徑。 這些範本可以是 *.vsz*檔案或要複製的原型樣本檔。

 該`SortPriority`值指定排序優先順序。

## <a name="add-items-to-an-existing-project"></a>新增專案到現有項目
 您還可以將項添加到現有專案。 例如,對於[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案,您可以將專案新增到*\<根>_程式檔\微軟可視化工作室_VC_CSharpProject專案_本地項目專案資料夾*。 在這種情況下,`%GUID_Project%`是 C# 專案的 GUID (#FAE04EC0-301F-11D3-BF4B-00C04F79EFBC])。

 還可以通過程式設計專案子類型來擴展現有專案。 使用專案子類型,無需編寫新的專案類型即可擴展專案。 有關項目子型態的詳細資訊,請參考[專案子型態](../../extensibility/internals/project-subtypes.md)。

## <a name="see-also"></a>另請參閱
- [註冊項目和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [新增項目新增項目新增項目對話框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [將目錄新增到「新項目」對話框](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
