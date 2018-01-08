---
title: "內容參數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 45c05f738086cad87d204e1421513da54a01e211
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="context-parameters"></a>內容參數
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE) 中，您可以加入至精靈**新專案**，**加入新項目**，或**加入子專案**對話方塊。 加入的精靈位於**檔案**功能表或以滑鼠右鍵按一下專案，以在**方案總管 中**。 IDE 會將內容參數傳遞給精靈的實作。 IDE 呼叫精靈時，內容參數會定義專案的狀態。  
  
 IDE 啟動精靈，藉由設定<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>IDE 的呼叫中的旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>專案的方法。 設定時，專案必須造成`IVsExtensibility::RunWizardFile`方法所使用的已註冊的精靈名稱或 GUID 和其他 IDE 傳遞給它的內容參數來執行。  
  
## <a name="context-parameters-for-new-project"></a>新專案的內容參數  
  
|參數|描述|  
|---------------|-----------------|  
|`WizardType`|註冊精靈類型 (<xref:EnvDTE.Constants.vsWizardNewProject>) 或用來表示的精靈類型的 GUID。 在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]實作中，精靈的 GUID 是 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|是唯一的字串[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱。|  
|`LocalDirectory`|使用專案檔的本機位置。|  
|`InstallationDirectory`|目錄路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是安裝。|  
|`FExclusive`|布林值旗標表示專案應該關閉開啟的方案。|  
|`SolutionName`|沒有目錄部分，或是副檔名為.sln 的方案檔的名稱。 .Suo 檔案名稱也會建立使用`SolutionName`。 當這個引數不是空字串時，此精靈會使用<xref:EnvDTE._Solution.Create%2A>加入與專案之前<xref:EnvDTE._Solution.AddFromTemplate%2A>。 如果這個名稱是空字串，使用<xref:EnvDTE._Solution.AddFromTemplate%2A>而不需呼叫<xref:EnvDTE._Solution.Create%2A>。|  
|`Silent`|布林值，指出是否應該以無訊息模式執行精靈如同**完成**所按下 (`TRUE`)。|  
  
## <a name="context-parameters-for-add-new-item"></a>內容參數加入新項目  
  
|參數|描述|  
|---------------|-----------------|  
|`WizardType`|註冊精靈類型 (<xref:EnvDTE.Constants.vsWizardAddItem>) 或用來表示的精靈類型的 GUID。 在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]實作中，精靈的 GUID 是 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|是唯一的字串[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱。|  
|`ProjectItems`|包含工作的專案檔案的本機位置。|  
|`ItemName`|要加入的項目名稱。 這個名稱是預設檔案名稱或檔案名稱的使用者型別從**新增的項目** 對話方塊。 名稱根據.vsdir 檔案中所設定的旗標。 名稱可以是 null 值。|  
|`InstallationDirectory`|目錄路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是安裝。|  
|`Silent`|布林值，指出是否應該以無訊息模式執行精靈如同**完成**所按下 (`TRUE`)。|  
  
## <a name="context-parameters-for-add-sub-project"></a>新增子專案的內容參數  
  
|參數|描述|  
|---------------|-----------------|  
|`WizardType`|註冊精靈類型 (<xref:EnvDTE.Constants.vsWizardAddSubProject>) 或用來表示的精靈類型的 GUID。 在[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]實作中，精靈的 GUID 是 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|是唯一的字串[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱。|  
|`ProjectItems`|指標`ProjectItems`精靈運作方式的集合。 此指標會傳遞給精靈根據選取的專案階層。 使用者通常會選取要將項目放在其中的資料夾，然後呼叫專案的**加入項目** 對話方塊。|  
|`LocalDirectory`|使用專案檔的本機位置。|  
|`ItemName`|要加入的項目名稱。 這個名稱是預設檔案名稱或檔案名稱的使用者型別從**新增的項目** 對話方塊。 名稱根據.vsdir 檔案中所設定的旗標。 名稱可以是 null 值。|  
|`InstallationDirectory`|目錄路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是安裝。|  
|`Silent`|布林值，指出是否應該以無訊息模式執行精靈如同**完成**所按下 (`TRUE`)。|  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [自訂參數](../../extensibility/internals/custom-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈 (。Vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [啟動精靈的內容參數](http://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)