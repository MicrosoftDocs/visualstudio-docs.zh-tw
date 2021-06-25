---
title: 將目錄新增至 [新增專案] 對話方塊 |Microsoft Docs
description: 在 Visual Studio 中，瞭解如何將目錄新增至 [新增專案] 對話方塊，讓您可以建立新的專案類型，並顯示這些專案以做為範本使用。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 44554c8bd7b758f1bf191d1a4bef9ba07941191d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901834"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>將目錄新增至新增專案對話方塊
當您建立新的專案類型時，您也可以在 [ **新增專案** ] 對話方塊中註冊新的目錄，以顯示它們作為範本使用。 下列程式碼範例說明如何註冊新的目錄（也稱為節點）。 在此範例中，會註冊 VSPackage 所公開的範本（ *CLSID_Package*）。 如此一來，[ **新增專案** ] 對話方塊的左側會提供加入的節點，以及由 *Folder_Label_ResID* 資源決定的名稱。 此資源是從 VSPackage 附屬 DLL 載入的。

 **資料夾** 值代表顯示 *Folder_Label_ResID* 節點的資料夾 GUID。 在此範例中，GUID 代表 [**新增專案**] 對話方塊的 [**專案類型**] 窗格中的 [**其他專案**] 資料夾。 如果 [ **其他專案** ] 值不存在，標籤就會位於最上層。

 `TemplatesDir`值指定包含專案範本的目錄完整路徑。 這些檔案可以是 *.vsz* 檔案或要複製的一般範本檔案。

 如果您指定 `TemplatesLocalizedSubDir` ，它必須是名稱為的子目錄的資源識別碼，該字串會 `TemplatesDir` 保留當地語系化的範本。 由於 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 從附屬 dll 載入字串資源（如果有的話），因此每個附屬 dll 都可以包含不同的子目錄名稱。 `SortPriority`值指定排序優先權。

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
- [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)
- [在 [加入新專案] 對話方塊中加入專案](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [將目錄新增至加入新專案對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
