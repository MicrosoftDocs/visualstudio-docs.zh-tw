---
title: 內容參數 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03e95dce70b38a6c2b51e0b610cb8e8bd6379239
ms.sourcegitcommit: 3dd15e019cba7d35dbabc1aa3bf55842a59f5278
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46370987"
---
# <a name="context-parameters"></a>內容參數
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 (IDE)，您可以加入至精靈**新增專案**，**加入新項目**，或**加入子專案**對話方塊。 加入的精靈都位於**檔案** 功能表或以滑鼠右鍵按一下專案，以在**方案總管 中**。 IDE 會將內容參數傳遞至精靈的實作。 IDE 呼叫精靈時，內容參數會定義專案的狀態。  
  
 在 IDE 啟動精靈，藉由設定<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION>IDE 的呼叫中的旗標<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>專案的方法。 設定時，專案必須造成`IVsExtensibility::RunWizardFile`方法，以利用已註冊的精靈名稱或 GUID 和其他 IDE 傳遞給它的內容參數來執行。  
  
## <a name="context-parameters-for-new-project"></a>針對新專案的內容參數  
  
|參數|描述|  
|---------------|-----------------|  
|`WizardType`|註冊精靈 的型別 (<xref:EnvDTE.Constants.vsWizardNewProject>) 或 GUID，表示類型的精靈。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]實作中，精靈的 GUID 是 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|是唯一的字串[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱。|  
|`LocalDirectory`|使用專案檔的本機位置。|  
|`InstallationDirectory`|目錄路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是安裝。|  
|`FExclusive`|布林值旗標，指出專案應該關閉開啟的方案。|  
|`SolutionName`|方案檔，而不需要的目錄部分名稱或 *.sln*延伸模組。 *.Suo*檔案名稱也會建立使用`SolutionName`。 當這個引數不是空字串時，精靈會使用<xref:EnvDTE._Solution.Create%2A>新增的專案之前<xref:EnvDTE._Solution.AddFromTemplate%2A>。 如果這個名稱是空字串，請使用<xref:EnvDTE._Solution.AddFromTemplate%2A>而不需呼叫<xref:EnvDTE._Solution.Create%2A>。|  
|`Silent`|布林值，指出是否應該以無訊息模式執行精靈好像**完成**已按下 (`TRUE`)。|  
  
## <a name="context-parameters-for-add-new-item"></a>內容參數加入新項目  
  
|參數|描述|  
|---------------|-----------------|  
|`WizardType`|註冊精靈 的型別 (<xref:EnvDTE.Constants.vsWizardAddItem>) 或 GUID，表示類型的精靈。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]實作中，精靈的 GUID 是 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|是唯一的字串[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱。|  
|`ProjectItems`|包含工作的專案檔案的本機位置。|  
|`ItemName`|要加入之項目的名稱。 這個名稱是預設檔案名稱或使用者類型的檔案名稱**新增的項目** 對話方塊。 名稱根據中所設定的旗標 *.vsdir*檔案。 名稱可以是 null 值。|  
|`InstallationDirectory`|目錄路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]是安裝。|  
|`Silent`|布林值，指出是否應該以無訊息模式執行精靈好像**完成**已按下 (`TRUE`)。|  
  
## <a name="context-parameters-for-add-sub-project"></a>加入子專案的內容參數  
  
|參數|描述|  
|---------------|-----------------|  
|`WizardType`|註冊精靈 的型別 (<xref:EnvDTE.Constants.vsWizardAddSubProject>) 或 GUID，表示類型的精靈。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]實作中，精靈的 GUID 是 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}。|  
|`ProjectName`|是唯一的字串[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱。|  
|`ProjectItems`|指標`ProjectItems`精靈運作方式的集合。 此指標會根據專案階層架構的選取項目精靈。 使用者通常會選取的資料夾中放置項目，然後再呼叫專案組**加入項目** 對話方塊。|  
|`LocalDirectory`|使用專案檔的本機位置。|  
|`ItemName`|要加入之項目的名稱。 這個名稱是預設檔案名稱或使用者類型的檔案名稱**新增的項目** 對話方塊。 名稱根據中所設定的旗標 *.vsdir*檔案。 名稱可以是 null 值。|  
|`InstallationDirectory`|目錄路徑[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]安裝。|  
|`Silent`|布林值，指出是否應該以無訊息模式執行精靈好像**完成**已按下 (`TRUE`)。|  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>   
 [自訂參數](../../extensibility/internals/custom-parameters.md)   
 [精靈](../../extensibility/internals/wizards.md)   
 [精靈 (.vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)   
 [啟動精靈的內容參數](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)