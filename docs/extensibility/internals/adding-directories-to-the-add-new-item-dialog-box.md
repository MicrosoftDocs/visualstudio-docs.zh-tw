---
title: 新增目錄，以加入新項目對話方塊 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 14
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 878c06e1965b5a96510df0e1b28175972546e227
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>新增目錄，以加入新項目對話方塊
下列程式碼範例示範如何註冊一組新的目錄**加入新項目** 對話方塊。 目錄**加入新項目**對話方塊會針對每個專案不同。 因此，專案子機碼下，在中找到登錄目錄\<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>登錄指令碼  
  
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
  
 Template_Path 值會指定包含的專案範本之目錄的完整路徑。 .Vsz 檔案或要複製的典型的範本檔案，可以使用這些範本。  
  
 SortPriority 值指定排序的優先順序。  
  
## <a name="adding-items-to-an-existing-project"></a>將項目加入至現有的專案  
 您也可以在現有的專案中加入項目。 例如，對於[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案中，您可以將項目加入\<根目錄 > \Program Files\Microsoft Visual Studio \VC#\CSharpProjectItems\LocalProjectItems 資料夾。 在此情況下`%GUID_Project%`是 C# 專案 ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}) 的 GUID。  
  
 您也可以擴充現有的專案，以程式設計方式編寫專案子類型。 與專案子類型，您可以擴充的專案而不需要撰寫新的專案類型。 如需專案子類型的詳細資訊，請參閱[專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
## <a name="see-also"></a>請參閱  
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [將目錄新增至新增專案對話方塊](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)