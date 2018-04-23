---
title: 將目錄加入至新的 [專案] 對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c4ad992785fdf8ab5ffdd3faa7043e2a0ee5411b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>將目錄加入至新的 [專案] 對話方塊
當您建立新的專案類型時，您也可以註冊新的目錄中**新專案**對話方塊來顯示它們做為範本使用。 下列程式碼範例說明如何註冊新的目錄，也就是節點。 在範例中，會註冊 VSPackage CLSID_Package 所公開的範本。 如此一來，左邊**新專案**對話方塊提供 [加入] 節點，取決於 Folder_Label_ResID 資源的名稱。 此資源是從 VSPackage 附屬 DLL 載入。  
  
 **資料夾**值代表的資料夾 Folder_Label_ResID 節點會顯示在其下的 GUID。 在此範例中，代表 GUID**其他專案**資料夾中的**專案類型**窗格**新專案** 對話方塊。 如果**其他專案**值不存在，此標籤位於最上層。  
  
 TemplatesDir 值會指定包含的專案範本之目錄的完整路徑。 這些檔案可以是.vsz 檔案或要複製的典型的範本檔案。  
  
 如果您指定 TemplatesLocalizedSubDir，它必須是命名的子目錄 TemplatesDir 保存當地語系化之範本字串的資源識別碼。 因為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入字串資源的附屬 DLL 如果有的話，每個附屬 DLL 可包含不同的子目錄名稱。 SortPriority 值指定排序的優先順序。  
  
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
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [將目錄新增至加入新項目對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)