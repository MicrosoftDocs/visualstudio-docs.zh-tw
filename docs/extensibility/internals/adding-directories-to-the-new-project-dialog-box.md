---
title: 將目錄新增到新項目對話框 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710238"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>將目錄新增到「新項目」對話框
創建新項目類型時,還可以在 **「新專案」** 對話框中註冊新目錄以將其顯示為範本。 以下代碼示例說明瞭如何註冊新目錄(也稱為節點)。 在此範例中,VSPackage 公開的範本*CLSID_Package*, 註冊。 因此,"**新專案"** 對話方塊的左側提供添加的節點,名稱由*Folder_Label_ResID*資源確定。 此資源從 VSPackage 衛星 DLL 載入。

 **"資料夾**"值表示顯示*Folder_Label_ResID*節點的資料夾的 GUID。 在此範例中,GUID 表示 **「新項目**」對話框「**項目類型」** 窗格中的 **「其他專案**」 。 如果 **「其他專案**」值不存在,則標籤將放置在頂層。

 該`TemplatesDir`值指定包含專案範本的目錄的完整路徑。 這些檔可以是 *.vsz*檔案或要複製的典型範本檔。

 如果指定`TemplatesLocalizedSubDir`,它必須是命名儲存本地化範本的子目錄`TemplatesDir`的 字串的資源識別碼。 由於[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]如果具有一個子目錄,則從附屬 DLL 載入字串資源,因此每個附屬 DLL 可以包含不同的子目錄名稱。 該`SortPriority`值指定排序優先順序。

```
NoRemove NewProjectTemplates
{
    NoRemove TemplateDirs
  {
    ForceRemove %CLSID_Package%
    {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
      {
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'
        val TemplatesDir = s '%Template_Path%'
        val TemplatesLocalizedSubDir = s '#100'
        val SortPriority = d 1000
      }
    }
  }
}
```

## <a name="see-also"></a>另請參閱
- [註冊項目和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [新增項目新增項目新增項目對話框](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [新增項目新增的項目中](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
