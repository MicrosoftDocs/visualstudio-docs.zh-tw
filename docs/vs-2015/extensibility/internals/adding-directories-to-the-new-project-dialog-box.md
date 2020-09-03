---
title: 將目錄新增至 [新增專案] 對話方塊 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a8a9eeca4dc455c4f16e3551541454483138a993
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203871"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>將目錄新增至新增專案對話方塊
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

當您建立新的專案類型時，您也可以在 [ **新增專案** ] 對話方塊中註冊新的目錄，以顯示它們作為範本使用。 下列程式碼範例說明如何註冊新的目錄（也稱為節點）。 在此範例中，會註冊 VSPackage CLSID_Package 公開的範本。 如此一來，[ **新增專案** ] 對話方塊的左側會提供加入的節點，以及由 Folder_Label_ResID 資源決定的名稱。 此資源是從 VSPackage 附屬 DLL 載入的。  
  
 **資料夾**值代表顯示 Folder_Label_ResID 節點的資料夾 GUID。 在此範例中，GUID 代表 [**新增專案**] 對話方塊的 [**專案類型**] 窗格中的 [**其他專案**] 資料夾。 如果 [ **其他專案** ] 值不存在，標籤就會位於最上層。  
  
 TemplatesDir 值會指定包含專案範本之目錄的完整路徑。 這些檔案可以是 .vsz 檔案或要複製的一般範本檔案。  
  
 如果您指定 TemplatesLocalizedSubDir，它必須是字串的資源識別碼，其會為保存當地語系化範本的 TemplatesDir 子目錄命名。 由於 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 從附屬 dll 載入字串資源（如果有的話），因此每個附屬 dll 都可以包含不同的子目錄名稱。 SortPriority 值指定排序優先權。  
  
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
 [註冊專案和專案範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [在 [加入新專案] 對話方塊中加入專案](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [將目錄新增至新增項目對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
