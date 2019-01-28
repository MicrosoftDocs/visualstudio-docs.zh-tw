---
title: 將目錄新增至加入新項目對話方塊 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 787eb0fd3cf865eb4b800c9470cf0c3d77d45975
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958390"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>將目錄新增至 [加入新項目] 對話方塊
下列程式碼範例示範如何註冊一組新的目錄**加入新項目** 對話方塊。 目錄**加入新項目** 對話方塊中有不同的每個專案。 因此，目錄會註冊底下**專案**子機碼，位於**HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**。
  
## <a name="registry-script"></a>登錄指令碼  
  
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
  
 `%Template_Path%`值會指定包含專案範本的目錄的完整路徑。 這些範本可以是 *.vsz*檔案或要複製的典型的範本檔案。  
  
 `SortPriority`值指定排序的優先順序。  
  
## <a name="add-items-to-an-existing-project"></a>將項目加入至現有的專案  
 您也可以在現有的專案中加入項目。 例如，對於[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案中，您可以將項目加入 *\<根 > \Program Files\Microsoft Visual Studio\VC #\CSharpProjectItems\LocalProjectItems* 資料夾。 在此情況下，`%GUID_Project%`是 C# 專案 ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}) 的 GUID。  
  
 您也可以程式設計專案子類型，以擴充現有的專案。 與專案子類型，您可以擴充專案，而不需要撰寫新的專案類型。 如需有關專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [將項目新增至 [加入新項目] 對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [將目錄新增至 [新增專案] 對話方塊](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)