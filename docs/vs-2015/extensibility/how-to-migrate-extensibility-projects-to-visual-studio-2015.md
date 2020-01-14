---
title: 如何：將擴充性專案遷移至 Visual Studio 2015 |Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2f4926a503304491164635b983353ba7f3bb0f6
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/13/2020
ms.locfileid: "75915975"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>如何：將擴充性專案遷移至 Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

以下是升級延伸模組的方式。  
  
> [!IMPORTANT]
> 如果您想要維護舊版 Visual Studio 的延伸模組解決方案，請務必在升級之前建立複本。 可能很難以將升級的版本傳回到先前的狀態。  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>升級擴充性解決方案  
  
1. 使用您想要升級的複本，在新版本中開啟。 我們會建議您不要還原升級。  
  
2. 升級完成之後，請將外部程式的路徑變更為新版本的 devenv .exe。 以滑鼠右鍵按一下 **方案總管**中的專案節點，然後選擇 **屬性**。 在 [**調試**程式] 索引標籤中，尋找 [**啟動外部程式**] 文字方塊，並將 devenv 的路徑變更為 Visual Studio 2015 路徑，這看起來應該如下所示：  
  
     **%ProgramFiles%\Microsoft Visual Studio 14.0 \ Common7\IDE\devenv.exe**  
  
3. 將參考新增至 VisualStudio，然後加入 .dll。 （以滑鼠右鍵按一下 **方案總管**中的專案節點，然後選擇 **新增/參考**。 選取 [**擴充**功能] 索引標籤，然後檢查**VisualStudio**。）  
  
4. 建置方案。 建立的檔案會部署到：  
  
     **%LOCALAPPDATA%\Microsoft\VisualStudio.14.0Exp\Extensions\\< 作者名稱\>\\< 專案名稱\>\\< 專案版本\>\\** 。  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>將擴充性專案更新為 NuGet 與 SDK 參考元件  
  
1. 判斷您的專案所需的 VS SDK 參考元件。  在**方案總管**中，展開專案的 [**參考**] 節點，並查看專案參考的清單。  VS SDK 參考元件的名稱中會有**VisualStudio**的前置詞（例如： VisualStudio. Shell 14.0）。  
  
2. 選取專案中的 VS SDK 參考元件，並以滑鼠右鍵按一下並**移除**，以將其移除。  
  
3. 新增 VS SDK 參考元件的 NuGet 版本。  仍在 [**方案總管參考**] 節點中，開啟 [**管理 NuGet 套件 ...** ] 對話方塊中，新增使用者帳戶。  如果您想要深入瞭解此對話方塊，請參閱[使用對話方塊管理 NuGet 套件](/nuget/consume-packages/install-use-packages-visual-studio)。 VS SDK 參考元件會在[nuget.org](https://www.nuget.org/) by [VisualStudioExtensibility](https://www.nuget.org/profiles/VisualStudioExtensibility)發行。  
  
4. 使用**nuget.org**作為您的**套件來源**，搜尋符合所需參考元件（例如： VisualStudio）的 nuget 套件名稱，並將它安裝在您的專案中。  NuGet 可能會加入多個參考元件，以便滿足初始元件的相依性。  
  
     如果您想要的話，也可以藉由安裝 VS SDK[中繼套件](https://www.nuget.org/packages/VSSDK_Reference_Assemblies)，一次加入所有 VS sdk 參考元件。  
  
5. 您也可以切換為使用 NuGet 版本的 VS SDK build tools。 此 NuGet 套件是[VSSDK. BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) ，一旦新增至您的專案，就會包含必要的工具和目標檔案，讓您在未安裝 VS SDK 的電腦上建立擴充性專案。  
  
> [!NOTE]
> 您不需要更新現有的擴充性專案，即可使用 NuGet 參考元件和工具。  他們可以繼續使用與 VS SDK 一起安裝的參考元件和工具來建立。
