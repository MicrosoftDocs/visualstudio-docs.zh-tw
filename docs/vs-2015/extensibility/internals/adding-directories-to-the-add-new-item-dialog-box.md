---
title: 在 [加入新專案] 對話方塊中加入目錄 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203921"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>將目錄新增至新增項目對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

下列程式碼範例示範如何為 [ **加入新專案** ] 對話方塊註冊一組新的目錄。 每個專案的 [ **加入新專案** ] 對話方塊的目錄都是不同的。 因此，這些目錄會在 [專案] 子機碼下註冊，可在下列專案中找到 \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> ：  
  
## <a name="the-registry-script"></a>登入指令檔  
  
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
  
 Template_Path 值會指定包含專案範本之目錄的完整路徑。 這些範本可以是 .vsz 檔案或要複製的典型範本檔案。  
  
 SortPriority 值指定排序優先權。  
  
## <a name="adding-items-to-an-existing-project"></a>將專案加入至現有的專案  
 您也可以將專案加入至現有的專案。 例如， [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 您可以在專案中，將專案新增至 \<root> \Program FILES\MICROSOFT Visual Studio \VC # \CSharpProjectItems\LocalProjectItems 資料夾。 在此情況下， `%GUID_Project%` 是 c # 專案的 GUID ( {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC} ) 。  
  
 您也可以藉由程式設計專案子類型來擴充現有的專案。 您可以使用專案子類型來擴充專案，而不需要撰寫新的專案類型。 如需專案子類型的詳細資訊，請參閱 [專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
## <a name="see-also"></a>另請參閱  
 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [在 [加入新專案] 對話方塊中加入專案](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [將目錄新增至新增專案對話方塊](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
