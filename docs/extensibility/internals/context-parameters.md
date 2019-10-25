---
title: 內容參數 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ea38b79be362f78fcc34161a480597fb0ecce40
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727552"
---
# <a name="context-parameters"></a>內容參數
在 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 整合式開發環境（IDE）中，您可以將嚮導加入至 [**新增專案**]、[**加入新專案**] 或 [**加入子專案**] 對話方塊。 在 [檔案] 功能表上或以滑鼠右鍵按一下**方案總管**中的**專案，即可**取得新增的嚮導。 IDE 會將內容參數傳遞至 wizard 的執行。 當 IDE 呼叫 wizard 時，內容參數會定義專案的狀態。

 IDE 會藉由在 IDE 對專案的 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> 方法呼叫中設定 <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> 旗標，來啟動嚮導。 設定時，專案必須使用已註冊的 wizard name 或 GUID 以及 IDE 傳遞給它的其他內容參數，來執行 `IVsExtensibility::RunWizardFile` 方法。

## <a name="context-parameters-for-new-project"></a>新專案的內容參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊的 wizard 類型（<xref:EnvDTE.Constants.vsWizardNewProject>）或表示 wizard 類型的 GUID。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 的執行中，wizard 的 GUID 是 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 唯一 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案名稱的字串。 |
| `LocalDirectory` | 工作專案檔案的本機位置。 |
| `InstallationDirectory` | @No__t_0 的目錄路徑是安裝。 |
| `FExclusive` | 布林值旗標，指出專案應關閉開啟的方案。 |
| `SolutionName` | 不含目錄部分或 *.sln*副檔名的方案檔名稱。 您也可以使用 `SolutionName` 來建立 *.suo*檔案名。 當這個引數不是空字串時，wizard 會使用 <xref:EnvDTE._Solution.Create%2A>，然後再使用 <xref:EnvDTE._Solution.AddFromTemplate%2A> 加入專案。 如果此名稱是空字串，請使用 <xref:EnvDTE._Solution.AddFromTemplate%2A>，而不需要呼叫 <xref:EnvDTE._Solution.Create%2A>。 |
| `Silent` | 布林值，指出 wizard 是否應該以無訊息模式執行，如同按一下 **[完成**] （`TRUE`）。 |

## <a name="context-parameters-for-add-new-item"></a>[加入新專案] 的內容參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊的 wizard 類型（<xref:EnvDTE.Constants.vsWizardAddItem>）或表示 wizard 類型的 GUID。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 的執行中，wizard 的 GUID 是 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 唯一 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案名稱的字串。 |
| `ProjectItems` | 包含工作專案檔案的本機位置。 |
| `ItemName` | 要加入之專案的名稱。 這個名稱可以是預設檔案名，也就是使用者在 [**加入專案**] 對話方塊中輸入的檔案名。 該名稱是以此*vsdir*檔案中所設定的旗標為基礎。 名稱可以是 null 值。 |
| `InstallationDirectory` | @No__t_0 的目錄路徑是安裝。 |
| `Silent` | 布林值，指出 wizard 是否應該以無訊息模式執行，如同按一下 **[完成**] （`TRUE`）。 |

## <a name="context-parameters-for-add-sub-project"></a>新增子專案的內容參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊的 wizard 類型（<xref:EnvDTE.Constants.vsWizardAddSubProject>）或表示 wizard 類型的 GUID。 在 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 的執行中，wizard 的 GUID 是 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 唯一 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案名稱的字串。 |
| `ProjectItems` | Wizard 操作所在之 `ProjectItems` 集合的指標。 這個指標會根據專案階層選取而傳遞至 wizard。 使用者通常會選取要放置專案的資料夾，然後呼叫專案的 [**加入專案**] 對話方塊。 |
| `LocalDirectory` | 工作專案檔案的本機位置。 |
| `ItemName` | 要加入之專案的名稱。 這個名稱可以是預設檔案名，也就是使用者在 [**加入專案**] 對話方塊中輸入的檔案名。 該名稱是以此*vsdir*檔案中所設定的旗標為基礎。 名稱可以是 null 值。 |
| `InstallationDirectory` | @No__t_0 安裝的目錄路徑。 |
| `Silent` | 布林值，指出 wizard 是否應該以無訊息模式執行，如同按一下 **[完成**] （`TRUE`）。 |

## <a name="see-also"></a>請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [自訂參數](../../extensibility/internals/custom-parameters.md)
- [精靈](../../extensibility/internals/wizards.md)
- [Wizard （.vsz）檔案](../../extensibility/internals/wizard-dot-vsz-file.md)
- [用於啟動嚮導的內容參數](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)