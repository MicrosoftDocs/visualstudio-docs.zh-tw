---
title: 解決方案設定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 243af2549862f1d29c44ba5bfc3060d87d5c6f85
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723837"
---
# <a name="solution-configuration"></a>方案組態
解決方案設定會儲存解決方案層級的屬性。 它們會指示**Start** （F5）按鍵和**Build**命令的行為。 根據預設，這些命令會建立並啟動 debug 設定。 這兩個命令都是在解決方案設定的內容中執行。 這表示使用者可以預期 F5 啟動，並建立任何透過設定來設定使用中的方案。 環境是設計用來優化解決方案，而不是專案在建立和執行時。

 [標準 Visual Studio] 工具列包含 [啟動] 按鈕，以及 [開始] 按鈕右邊的 [方案設定] 下拉式。 這份清單可讓使用者選擇按 F5 時要啟動的設定、建立自己的解決方案設定，或編輯現有的設定。

> [!NOTE]
> 沒有可建立或編輯解決方案設定的擴充性介面。 您必須使用 `DTE.SolutionBuilder`。 不過，有擴充性 Api 可用於管理解決方案組建。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>。

 以下是您可以如何執行專案類型所支援的解決方案設定：

- 專案

   顯示在目前方案中找到的專案名稱。

- Configuration

   若要提供專案類型支援的設定清單並顯示在屬性頁中，請執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>。

   [設定] 資料行會顯示要在此解決方案設定中建立之專案設定的名稱，當您按一下箭號按鈕時，會列出所有專案設定。 環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A> 方法來填寫這份清單。 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 方法指出專案支援設定編輯，則 [新增] 或 [編輯] 選項也會顯示在 [設定] 標題之下。 這些選取專案都會啟動對話方塊，以呼叫 `IVsCfgProvider2` 介面的方法來編輯專案的設定。

   如果專案不支援設定，[設定] 資料行會顯示 [無]，而且會停用。

- Platform

   顯示所選取專案設定的組建平臺，並在您按一下箭號按鈕時，列出該專案的所有可用平臺。 環境會呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A> 方法來填寫這份清單。 如果 <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A> 方法指出專案支援平臺編輯，則 [新增] 或 [編輯] 選項也會顯示在 [平臺] 標題底下。 這些選項都會啟動對話方塊，以呼叫 `IVsCfgProvider2` 方法來編輯專案的可用平臺。

   如果專案不支援平臺，該專案的 [平臺] 欄就會顯示 [無]，而且會停用。

- 組建

   指定專案是否由目前的解決方案設定所建立。 當叫用方案層級的組建命令時，不論其包含的專案相依性為何，都不會建立已取消選取的專案。 未選取要建立的專案仍會包含在此解決方案的調試、執行、封裝和部署中。

- 部署

   指定當使用 [啟動] 或 [部署] 命令搭配選取的解決方案組建設定時，是否要部署專案。 如果專案支援在其 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2> 物件上執行 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 介面來進行部署，則可以使用此欄位的核取方塊。

  新增解決方案設定之後，使用者可以從 [標準] 工具列上的 [解決方案設定] 下拉式清單方塊中選取該設定，以建立及/或啟動該設定。

## <a name="see-also"></a>請參閱
- [管理組態選項](../../extensibility/internals/managing-configuration-options.md)
- [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)
- [專案組態物件](../../extensibility/internals/project-configuration-object.md)