---
title: 方案組態 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- solution configurations
ms.assetid: f22cfc75-3e31-4e0d-88a9-3ca99539203b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: caf55b341cc34bb4101f27d2468f0da8e5cf6c96
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2018
ms.locfileid: "49875316"
---
# <a name="solution-configuration"></a>方案組態
方案組態儲存方案層級屬性。 這些指示的行為**開始**(F5) 索引鍵和**建置**命令。 根據預設，這些命令會建置，並開始偵錯組態。 這兩個命令的方案組態的內容中執行。 這表示使用者可以預期 F5 來啟動和任何使用中方案已透過設定的組建。 環境被設計來建置和執行時，最佳化解決方案，而不是專案中。  
  
 標準的 Visual Studio 工具列包含 [開始] 按鈕和方案組態下拉式清單右邊的 [開始] 按鈕。 這份清單可讓使用者選擇在按下 F5 時要啟動的組態，建立自己的方案組態，或編輯現有的組態。  
  
> [!NOTE]
>  沒有擴充性介面來建立或編輯方案組態。 您必須使用`DTE.SolutionBuilder`。 不過，有擴充性 Api 用於管理方案的組建。 如需詳細資訊，請參閱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2>。  
  
 以下是如何實作您的專案類型所支援的解決方案組態：  
  
- 專案  
  
   顯示目前方案中找不到專案的名稱。  
  
- 組態  
  
   提供您的專案類型所支援的組態清單，並顯示在 屬性頁中，實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2>。  
  
   [組態] 欄位會顯示要在這個方案組態中建置的專案組態名稱，並列出所有的專案組態，當您按一下箭號按鈕。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgNames%2A>填寫這份清單的方法。 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>方法指出專案支援組態編輯、 新增或編輯選取項目也會顯示在 [設定] 標題下。 每個這些選取項目啟動呼叫方法的對話方塊`IVsCfgProvider2`介面以編輯專案的組態。  
  
   如果專案不支援的組態，組態 欄位會顯示 無，並已停用。  
  
- Platform  
  
   顯示選取的專案組態，建置，並當您按一下箭號按鈕時，請列出所有可用的平台專案的平台。 環境呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetPlatformNames%2A>填寫這份清單的方法。 如果<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgProviderProperty%2A>方法指出專案支援編輯平台，新增或編輯選取項目也會顯示平台 標題下。 每個這些選取項目啟動對話方塊呼叫`IVsCfgProvider2`編輯專案的可用平台的方法。  
  
   如果專案不支援的平台，該專案的平台欄會顯示 無，並已停用。  
  
- 組建  
  
   指定由目前的方案組態建置專案。 儘管其所包含的任何專案相依性叫用的方案層級建置命令時，不會建置未選取的專案。 未選取要建置的專案仍會包含在偵錯、 執行、 封裝和部署解決方案。  
  
- 部署  
  
   指定與所選取的方案建置組態使用 [開始] 或 [部署] 命令時，會部署專案。 此欄位的核取方塊會使用專案支援藉由實作部署<xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg>介面上其<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2>物件。  
  
  加入新的方案組態後，使用者可以選取它從建置及/或啟動該組態 標準 工具列上的 方案組態下拉式清單方塊。  
  
## <a name="see-also"></a>另請參閱  
 [管理組態選項](../../extensibility/internals/managing-configuration-options.md)   
 [建置的專案組態](../../extensibility/internals/project-configuration-for-building.md)   
 [專案組態物件](../../extensibility/internals/project-configuration-object.md)