---
title: 將目錄新增至新的 [專案] 對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e81d09c2a4e97ca5f3da112e593b04b219e6314
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328009"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>將目錄新增至 [新增專案] 對話方塊
當您建立新的專案類型時，您也可以註冊新的目錄中**新的專案**對話方塊來顯示它們做為範本使用。 下列程式碼範例說明如何註冊新的目錄，也稱為節點。 在範例中，VSPackage，所公開的範本*CLSID_Package*，註冊。 如此一來，左邊**新的專案**對話方塊會提供加入的節點名稱，取決於*Folder_Label_ResID*資源。 此資源會從 VSPackage 附屬 DLL 載入。

 **資料夾**的值代表所在資料夾的 GUID *Folder_Label_ResID*節點會顯示。 在此範例中，代表 GUID**其他專案**資料夾中的**專案類型**窗格**新專案** 對話方塊。 如果**其他專案**值不存在，此標籤位於最上層。

 `TemplatesDir`值會指定包含專案範本的目錄的完整路徑。 這些檔案可以是 *.vsz*檔案或要複製的一般範本檔案。

 如果您指定`TemplatesLocalizedSubDir`，它必須是字串，可命名的子目錄的資源識別碼`TemplatesDir`保存當地語系化的範本。 因為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入字串資源的附屬 DLL 如果您沒有帳戶，每個附屬 DLL 可包含不同的子目錄名稱。 `SortPriority`值指定排序的優先順序。

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
- [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [將項目新增至 [加入新項目] 對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [將目錄新增至 [加入新項目] 對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)