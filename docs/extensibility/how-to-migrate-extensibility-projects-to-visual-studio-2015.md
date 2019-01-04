---
title: HOW TO：將擴充性專案移轉至 Visual Studio 2015 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 456661c06934063041f06c36c20eee72d52c5b4a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/02/2019
ms.locfileid: "53915331"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>HOW TO：將擴充性專案移轉至 Visual Studio 2015
以下是如何升級您的延伸模組。  
  
> [!IMPORTANT]
>  如果您想要維護您的擴充方案，針對較早版本的 Visual Studio 的版本，請務必製作複本，才能將它升級。 它可能難以返回先前的狀態中的升級的版本。  
  
### <a name="to-upgrade-an-extensibility-solution"></a>若要升級的擴充性解決方案  
  
1.  您想要升級，請開啟新的版本中使用的複本。 升級是無法復原就會收到通知。  
  
2.  在升級完成之後，可將外部程式的路徑變更為新版本的*devenv.exe*。 以滑鼠右鍵按一下專案節點，在**方案總管**，然後選擇**屬性**。 在 **偵錯**索引標籤上，尋找由文字方塊**啟動外部程式**和變更的路徑*devenv.exe*至 Visual Studio 2015 的路徑，這應該看起來像這樣：  
  
     *%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe*  
  
3.  將參考加入*Microsoft.VisualStudio.Shell.14.0.dll*。 (以滑鼠右鍵按一下專案節點，在**方案總管**，然後選擇**新增** > **參考**。 選取**延伸模組**索引標籤，然後再檢查**Microsoft.VisualStudio.Shell.14.0**。)  
  
4.  建置方案。 建置的檔案部署至：  
  
     *%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< 撰寫名稱\>\\< 專案名稱\>\\< 專案版本\>\\*。  
  
### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>更新 NuGet VS SDK 參考組件的擴充性專案  
  
1.  判斷您的專案需要的 VS SDK 參考組件。  在 [**方案總管] 中**，展開專案的**參考**節點和檢閱專案參考的清單。  VS SDK 參考的組件會具有前置詞**Microsoft.VisualStudio**名稱中 (例如：Microsoft.VisualStudio.Shell.14.0)。  
  
2.  從專案移除 VS SDK 參考組件，方法是選取它們，以滑鼠右鍵按一下並選取**移除**。  
  
3.  加入 VS SDK 參考組件的 NuGet 版本。  當您依然在**方案總管參考**節點，開啟**管理 NuGet 套件**對話方塊。  如果您想要深入了解此對話方塊，請參閱[套件管理員 UI](/NuGet/Tools/Package-Manager-UI)。 VS SDK 參考組件上發佈[nuget.org](http://www.nuget.org)依[VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility)。  
  
4.  使用**nuget.org**做為您**套件來源**，搜尋符合所需的參考組件的 NuGet 套件名稱 (例如：Microsoft.VisualStudio.Shell.14.0) 並將它安裝在您的專案。  NuGet 可以新增多個參考組件，以滿足初始的組件相依性。  
  
     如果您喜歡，您可以加入所有 VS SDK 參考組件一次安裝 VS SDK[中繼套件](http://www.nuget.org/packages/VSSDK_Reference_Assemblies)。  
  
5.  您也可以切換成使用 VS SDK 建置工具的 NuGet 版本。 此 NuGet 封裝[Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools)並一次新增至您的專案會包含必要的工具和目標，讓您的電腦上建置您的擴充性專案，而不需要安裝 VS SDK 的檔案。  
  
> [!NOTE]
>  不需要您更新您現有的擴充性專案，以使用 NuGet 參考組件和工具。  他們可以繼續建置使用參考組件和工具與 VS SDK 一起安裝。