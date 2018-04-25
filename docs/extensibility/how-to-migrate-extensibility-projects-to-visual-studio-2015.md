---
title: 如何： 將擴充性專案移轉至 Visual Studio 2015 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5adad311c1696d958902d9ad33ed1d1872606458
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>如何： 將擴充性專案移轉至 Visual Studio 2015
以下是如何升級您的擴充功能。  
  
> [!IMPORTANT]
>  如果您想要維護舊版的 Visual Studio 擴充功能方案的版本，請務必製作複本，然後再升級它。 可能會難以返回先前的狀態中的升級的版本。  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>若要升級的擴充性解決方案  
  
1.  您想要升級，請開啟新的版本中使用的複本。 您會建議您升級即無法復原。  
  
2.  在升級完成之後，請至新版的 devenv.exe 變更外部程式的路徑。 以滑鼠右鍵按一下專案節點中的**方案總管] 中**，然後選擇 [**屬性**。 在**偵錯**索引標籤上，尋找由文字方塊**啟動外部程式**並將 devenv.exe 的路徑變更為 Visual Studio 2015 路徑看起來應該像這樣：  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  加入 Microsoft.VisualStudio.Shell.14.0.dll 的參考。 (以滑鼠右鍵按一下專案節點中的**方案總管] 中**，然後選擇 [**加入 / 參考**。 選取**延伸**索引標籤，然後檢查**Microsoft.VisualStudio.Shell.14.0**。)  
  
4.  建置方案。 若要部署已建置的檔案：  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< 撰寫名稱\>\\< 專案名稱\>\\< 專案版本\>\\**。  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>若要更新的擴充性專案 NuGet VS SDK 的參考組件  
  
1.  判斷您的專案需要 VS SDK 參考組件。  在**方案總管 中**，展開專案**參考**節點，然後檢閱專案參考的清單。  VS SDK 的參考組件會具有前置詞**Microsoft.VisualStudio**名稱中 (例如： Microsoft.VisualStudio.Shell.14.0)。  
  
2.  從專案移除 VS SDK 的參考組件，來選取它們，以滑鼠右鍵按一下和**移除**。  
  
3.  加入 NuGet 版本的 VS SDK 的參考組件。  在**方案總管參考**節點，開啟**管理 NuGet 封裝...** 對話方塊。  如果您想要深入了解此對話方塊，請參閱[封裝管理員 UI](/NuGet/Tools/Package-Manager-UI)。 VS SDK 的參考組件上發佈[nuget.org](http://www.nuget.org)由[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)。  
  
4.  使用**nuget.org**做為您**套件來源**，搜尋符合所需的參考組件的 NuGet 封裝名稱 (例如： Microsoft.VisualStudio.Shell.14.0) 並將它安裝在您專案。  NuGet 可以新增多個參考組件，以滿足初始的組件相依性。  
  
     如果您想要的話，您可以新增所有 VS SDK 的參考組件一次安裝 VS SDK[中繼封裝](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。  
  
5.  您也可以切換到使用 VS SDK 建置工具的 NuGet 版本。 此 NuGet 封裝是[Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools)並一次加入至您的專案將包含必要的工具和檔案可讓您的電腦上建立擴充性專案，而不安裝 VS SDK 為目標。  
  
> [!NOTE]
>  它不需要您更新現有擴充性專案以使用 NuGet 參考組件和工具。  他們可以繼續使用參考組件和工具與 VS SDK 一起安裝。