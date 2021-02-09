---
title: 解決方案設定 |Microsoft Docs
description: 瞭解如何執行您的專案類型所支援的解決方案設定，這些設定會指示 Start (F5) 機碼和組建命令的行為。
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99a0de44d5e7ac240187c929a8134ab47c7de55c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910990"
---
# <a name="solution-configuration"></a>方案組態
解決方案設定會儲存解決方案層級的屬性。 他們會導向 **Start** (F5) Key 和 **Build** 命令的行為。 根據預設，這些命令會建立並啟動偵錯工具設定。 這兩個命令都會在解決方案設定的內容中執行。 這表示使用者可以預期 F5 啟動，並建立任何使用中解決方案設定的設定。 環境是設計來針對解決方案進行優化，而不是在建立和執行時進行專案。

 標準 Visual Studio 工具列包含 [開始] 按鈕右邊的 [開始] 按鈕和方案設定下拉式清單。 這份清單可讓使用者在按下 F5 時，選擇要啟動的設定，建立自己的解決方案設定，或編輯現有的設定。

> [!NOTE]
> 沒有可建立或編輯解決方案設定的擴充性介面。 您必須使用 `DTE.SolutionBuild`。 不過，有一些擴充性 Api 可用於管理解決方案組建。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>。

 以下是您可以如何執行您的專案類型所支援的解決方案設定：

- Project

   顯示在目前方案中找到的專案名稱。

- 組態

   若要提供專案類型所支援並顯示在屬性頁中的設定清單，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2> 。

   [設定] 欄會顯示要在此解決方案設定中建立之專案設定的名稱，並在您按一下箭號按鈕時列出所有的專案設定。 環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> 方法來填寫這份清單。 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 方法指出專案支援設定編輯，則新的或編輯選項也會顯示在 [設定] 標題下。 上述每個選項都會啟動對話方塊，以呼叫介面的方法 `IVsCfgProvider2` 來編輯專案的設定。

   如果專案不支援設定，[設定] 欄會顯示 [無] 並停用。

- 平台

   顯示選取之專案設定建立的平臺，並列出當您按一下箭號按鈕時，專案的所有可用平臺。 環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> 方法來填寫這份清單。 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 方法指出專案支援平臺編輯，則新的或編輯選項也會顯示在 [平臺] 標題下。 上述每個選項都會啟動對話方塊， `IVsCfgProvider2` 以呼叫方法來編輯專案的可用平臺。

   如果專案不支援平臺，該專案的 [平臺] 欄會顯示 [無] 並停用。

- 組建

   指定專案是否由目前的方案設定所建立。 當您叫用方案層級組建命令時，如果它們包含任何專案相依性，則不會建立未選取的專案。 未選取要建立的專案仍包含在偵測、執行、封裝和部署解決方案中。

- 部署

   指定當啟動或部署命令搭配選取的解決方案組建設定使用時，是否要部署專案。 如果專案支援藉由 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 在其物件上執行介面來進行部署，則可以使用此欄位的核取方塊 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 。

  新增方案設定之後，使用者可以從 [標準] 工具列上的 [方案設定] 下拉式清單方塊中選取該設定，以建立及/或啟動該設定。

## <a name="see-also"></a>另請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [專案組態物件](../../extensibility/internals/project-configuration-object.md)
