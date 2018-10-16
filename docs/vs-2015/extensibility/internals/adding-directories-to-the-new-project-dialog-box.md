---
title: 將目錄新增至新的 [專案] 對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fd99b6a58bb5203e7e0dfd7df95494cb258c9228
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190485"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>將目錄新增至新增專案對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當您建立新的專案類型時，您也可以註冊新的目錄中**新的專案**對話方塊來顯示它們做為範本使用。 下列程式碼範例說明如何註冊新的目錄，也稱為節點。 在此範例中，會註冊 VSPackage CLSID_Package 所公開的範本。 如此一來，左邊**新的專案**對話方塊會提供新增的節點，取決於 Folder_Label_ResID 資源的名稱。 此資源會從 VSPackage 附屬 DLL 載入。  
  
 **資料夾**值代表 Folder_Label_ResID 節點會顯示在其下的資料夾的 GUID。 在此範例中，代表 GUID**其他專案**資料夾中的**專案類型**窗格**新專案** 對話方塊。 如果**其他專案**值不存在，此標籤位於最上層。  
  
 TemplatesDir 值會指定包含專案範本的目錄的完整路徑。 這些檔案可以是.vsz 檔案或要複製的一般範本檔案。  
  
 如果您指定 TemplatesLocalizedSubDir，它必須是字串，可命名的子目錄 TemplatesDir 保存當地語系化的範本的資源識別碼。 因為[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]載入字串資源的附屬 DLL 如果您沒有帳戶，每個附屬 DLL 可包含不同的子目錄名稱。 SortPriority 值指定排序的優先順序。  
  
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
 [新增項目加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [將目錄新增至加入新項目對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

