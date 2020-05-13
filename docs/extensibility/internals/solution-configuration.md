---
title: 解決方案配置 |微軟文件
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c96b73747ef8b136a74a7256cde7fef8d1c42de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705383"
---
# <a name="solution-configuration"></a>方案組態
解決方案配置存儲解決方案級屬性。 它們指示**開始**(F5) 鍵和**生成**命令的行為。 默認情況下,這些命令生成並啟動調試配置。 這兩個命令都在解決方案配置的上下文中執行。 這意味著使用者可以期望 F5 啟動和生成通過設置配置的活動解決方案的任何內容。 該環境旨在優化解決方案,而不是專案,當涉及到構建和運行。

 標準 Visual Studio 工具列包含"開始"按鈕和"開始"按鈕右側的解決方案配置下拉。 此清單允許用戶選擇在按下 F5 時啟動的配置、創建自己的解決方案配置或編輯現有配置。

> [!NOTE]
> 沒有可擴展介面來創建或編輯解決方案配置。 您必須使用 `DTE.SolutionBuild`。 但是,存在用於管理解決方案構建的可擴充性 API。 如需詳細資訊，請參閱 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>。

 以下是實現項目類型支援的解決方案配置的方式:

- 隨附此逐步解說的專案

   顯示當前解決方案中找到的專案名稱。

- 組態

   要提供項目類型支援在屬性頁中顯示的設定清單,請實現<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>。

   設定"列顯示要在此解決方案配置中生成的專案配置的名稱,並在單擊箭頭按鈕時列出所有專案配置。 環境調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A>方法 以填寫此清單。 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>方法指示專案支援配置編輯,則"新建"或"編輯"選擇也會顯示在"配置"標題下。 每個選擇都會啟動對話框,這些對話框調用`IVsCfgProvider2`介面的方法來編輯專案的配置。

   如果專案不支援配置,則"配置"列將顯示"無"並禁用。

- 平台

   顯示所選專案配置生成的平臺,並在按一下箭頭按鈕時列出專案的所有可用平臺。 環境調用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A>方法 以填寫此清單。 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>方法指示專案支援平臺編輯,則"新建"或"編輯"選擇也會顯示在"平臺"標題下。 每個選擇都會啟動對話框,這些對話框調用`IVsCfgProvider2`方法來編輯專案的可用平臺。

   如果專案不支援平臺,該專案的平臺列將顯示"無"並禁用。

- 組建

   指定專案是否由當前解決方案配置生成。 調用解決方案級生成命令時,即使其中包含任何項目依賴項,則不會生成未選擇的專案。 未選擇要生成的專案仍包含在解決方案的調試、運行、打包和部署中。

- 部署

   指定在"開始"或"部署"命令與所選解決方案生成配置一起使用時,是否將部署專案。 如果專案支援通過在其<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg><xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>物件上實現介面來部署,則此欄位的複選框將可用。

  添加新解決方案配置後,用戶可以從標準工具列上的"解決方案配置"下拉列表框中選擇它,以生成和/或啟動該配置。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [專案組態物件](../../extensibility/internals/project-configuration-object.md)
