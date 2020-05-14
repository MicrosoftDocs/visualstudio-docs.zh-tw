---
title: 上下文參數 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, context parameters
- context parameters
ms.assetid: 1a062dcb-8a8f-40dd-bea9-3d10f9448966
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6673ad8f26c94165635b5f1bc652b91dcbbfd24f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709300"
---
# <a name="context-parameters"></a>內容參數
在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式開發環境 (IDE) 中,您可以將精靈加入**到新專案**,**添加新專案**或**新增子項目**對話框。 添加的嚮導可在 **「檔」** 選單上或通過右鍵單擊**解決方案資源管理器**中的專案。 IDE 將上下文參數傳遞給嚮導的實現。 當 IDE 調用精靈時,上下文參數定義專案的狀態。

 IDE 通過在 IDE<xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION><xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A>對專案 方法的調用中設置標誌來啟動嚮導。 設置時,專案必須使用已註冊的`IVsExtensibility::RunWizardFile`嚮導名稱或 GUID 以及 IDE 傳遞給它的其他上下文參數來執行該方法。

## <a name="context-parameters-for-new-project"></a>新專案的內容參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊精靈型態<xref:EnvDTE.Constants.vsWizardNewProject>( ) 或指示精靈類型的 GUID。 在實現中[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)],嚮導的 GUID 是 {0F90E1D0-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 作為唯一[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱的字串。 |
| `LocalDirectory` | 工作專案檔的本地位置。 |
| `InstallationDirectory` | 正在安裝的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]目錄路徑。 |
| `FExclusive` | 表示專案應關閉打開的解決方案的布爾標誌。 |
| `SolutionName` | 沒有目錄部分或 *.sln*副檔名的解決方案檔的名稱。 *.suo*檔案名稱也使用建立`SolutionName`。 當此參數不是空字串時,嚮導在使用<xref:EnvDTE._Solution.Create%2A><xref:EnvDTE._Solution.AddFromTemplate%2A>添加專案之前使用。 如果此名稱為空字串,請使用<xref:EnvDTE._Solution.AddFromTemplate%2A>不叫 。<xref:EnvDTE._Solution.Create%2A> |
| `Silent` | 布林,指示精靈是否應以靜默方式執行,就像按下 **「完成」**`TRUE`一樣 ( 。 |

## <a name="context-parameters-for-add-new-item"></a>新增項目的文字參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊精靈型態<xref:EnvDTE.Constants.vsWizardAddItem>( ) 或指示精靈類型的 GUID。 在實現中[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)],嚮導的 GUID 是 {0F90E1D1-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 作為唯一[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱的字串。 |
| `ProjectItems` | 包含工作項目檔的本地位置。 |
| `ItemName` | 要添加的項的名稱。 此名稱是預設檔名或使用者從 **「添加專案」** 對話框中鍵入的檔名。 名稱基於*在 .vsdir*檔中設定的標誌。 名稱可以是空值。 |
| `InstallationDirectory` | 正在安裝的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]目錄路徑。 |
| `Silent` | 布林,指示精靈是否應以靜默方式執行,就像按下 **「完成」**`TRUE`一樣 ( 。 |

## <a name="context-parameters-for-add-sub-project"></a>新增子項目的文字參數

| 參數 | 描述 |
|-------------------------| - |
| `WizardType` | 已註冊精靈型態<xref:EnvDTE.Constants.vsWizardAddSubProject>( ) 或指示精靈類型的 GUID。 在實現中[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)],嚮導的 GUID 是 {0F90E1D2-4999-11D1-B6D1-00A0C90F2744}。 |
| `ProjectName` | 作為唯一[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案名稱的字串。 |
| `ProjectItems` | 指向`ProjectItems`嚮導操作的集合。 此指標根據專案層次結構選擇傳遞給嚮導。 使用者通常選擇一個資料夾,將專案放在其中,然後調用專案的 **「添加專案」** 對話方塊。 |
| `LocalDirectory` | 工作專案檔的本地位置。 |
| `ItemName` | 要添加的項的名稱。 此名稱是預設檔名或使用者從 **「添加專案」** 對話框中鍵入的檔名。 名稱基於*在 .vsdir*檔中設定的標誌。 名稱可以是空值。 |
| `InstallationDirectory` | 安裝的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]目錄路徑。 |
| `Silent` | 布林,指示精靈是否應以靜默方式執行,就像按下 **「完成」**`TRUE`一樣 ( 。 |

## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2>
- [自訂參數](../../extensibility/internals/custom-parameters.md)
- [嚮導](../../extensibility/internals/wizards.md)
- [匯入匯(.vsz) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)
- [啟動精靈的內容](https://msdn.microsoft.com/Library/051a10f4-9e45-4604-b344-123044f33a24)
