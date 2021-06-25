---
title: 內容參數 |Microsoft Docs
description: 瞭解 Visual Studio 整合式開發環境中的內容參數 (IDE) ，以在您新增或執行 wizard 時定義專案的狀態。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 536e5abf92884c5c19399e73b4e1773e66919657
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898223"
---
# <a name="context-parameters"></a>內容參數
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境中 (IDE) ，您可以將嚮導加入至 [ **新增專案**]、[ **加入新** 專案] 或 [ **加入子專案** ] 對話方塊。 您可以在 [檔案 **] 功能表上，或** 以滑鼠右鍵按一下 **方案總管** 中的專案，來使用新增的嚮導。 IDE 會將內容參數傳遞至 wizard 的執行。 當 IDE 呼叫 wizard 時，內容參數會定義專案的狀態。

 IDE 會 <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> 在 ide 呼叫專案的方法時，將旗標設定為啟動嚮導 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> 。 當設定時，專案必須 `IVsExtensibility::RunWizardFile` 使用已註冊的 wizard 名稱或 GUID，以及 IDE 傳遞給它的其他內容參數，來執行方法。

## <a name="context-parameters-for-new-project"></a>新專案的內容參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊的 wizard 類型 (<xref:EnvDTE.Constants.vsWizardNewProject>) 或表示 wizard 類型的 GUID。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 執行中，wizard 的 GUID 是 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 唯一 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案名稱的字串。 |
| `LocalDirectory` | 工作專案檔案的本機位置。 |
| `InstallationDirectory` | 的目錄路徑 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 是安裝。 |
| `FExclusive` | 布林值旗標，表示專案應該關閉開啟的方案。 |
| `SolutionName` | 沒有目錄部分或 *.sln* 副檔名的方案檔名稱。 此外 ，也 `SolutionName` 會使用建立 .suo 檔案名。 當這個引數不是空字串時，wizard 會使用來 <xref:EnvDTE._Solution.Create%2A> 加入專案 <xref:EnvDTE._Solution.AddFromTemplate%2A> 。 如果這個名稱是空字串，請在 <xref:EnvDTE._Solution.AddFromTemplate%2A> 不呼叫的情況下使用 <xref:EnvDTE._Solution.Create%2A> 。 |
| `Silent` | 布林值，指出是否應以無訊息模式執行，如同按一下 **[完成]** (`TRUE`) 。 |

## <a name="context-parameters-for-add-new-item"></a>新增專案的內容參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊的 wizard 類型 (<xref:EnvDTE.Constants.vsWizardAddItem>) 或表示 wizard 類型的 GUID。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 執行中，wizard 的 GUID 是 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 唯一 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案名稱的字串。 |
| `ProjectItems` | 包含工作專案檔案的本機位置。 |
| `ItemName` | 要加入之專案的名稱。 這個名稱可以是預設的檔案名，或是使用者從 [ **加入專案** ] 對話方塊輸入的檔案名。 名稱是根據在 *vsdir* 檔案中設定的旗標。 名稱可以是 null 值。 |
| `InstallationDirectory` | 的目錄路徑 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 是安裝。 |
| `Silent` | 布林值，指出是否應以無訊息模式執行，如同按一下 **[完成]** (`TRUE`) 。 |

## <a name="context-parameters-for-add-sub-project"></a>加入子專案的內容參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊的 wizard 類型 (<xref:EnvDTE.Constants.vsWizardAddSubProject>) 或表示 wizard 類型的 GUID。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 執行中，wizard 的 GUID 是 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 唯一 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案名稱的字串。 |
| `ProjectItems` | 由 `ProjectItems` wizard 操作之集合的指標。 這個指標會根據專案階層選項傳遞至 wizard。 使用者通常會選取要放置專案的資料夾，然後呼叫專案的 [ **加入專案** ] 對話方塊。 |
| `LocalDirectory` | 工作專案檔案的本機位置。 |
| `ItemName` | 要加入之專案的名稱。 這個名稱可以是預設的檔案名，或是使用者從 [ **加入專案** ] 對話方塊輸入的檔案名。 名稱是根據在 *vsdir* 檔案中設定的旗標。 名稱可以是 null 值。 |
| `InstallationDirectory` | 安裝的目錄路徑 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 。 |
| `Silent` | 布林值，指出是否應以無訊息模式執行，如同按一下 **[完成]** (`TRUE`) 。 |

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [自訂參數](../../extensibility/internals/custom-parameters.md)
- [精靈](../../extensibility/internals/wizards.md)
- [Wizard ( .vsz) 檔](../../extensibility/internals/wizard-dot-vsz-file.md)
- [啟動嚮導的內容參數](/previous-versions/tz690efs(v=vs.140))