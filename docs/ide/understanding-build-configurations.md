---
title: 了解組建組態
ms.date: 01/20/2020
ms.technology: vs-ide-compile
ms.topic: conceptual
f1_keywords:
- SolutionProperties.ActiveConfig
- vs.build.newprojectconfiguration
- vc.proj.configurationsctrl.multipleconfigs
- vs.build.editsolutionconfigurations
- vs.build.editprojectconfigurations
- vs.multipleconfigurations
- vs.build.newsolutionconfiguration
- VS.ConfigurationManager
- VS.MultipleConfig
helpviewer_keywords:
- solution build configurations, about build configurations
- build configurations
- project build configurations
- build configurations, advanced
- projects [Visual Studio], build configuration
- solutions [Visual Studio], build configuration
ms.assetid: 934c727d-3a22-429c-bd13-3552cecf2e24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a37d4fa5dc92253b94dc64590c9df5fec7703ceb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/18/2020
ms.locfileid: "77904161"
---
# <a name="understand-build-configurations"></a>了解組建組態

當您需要使用不同的設置生成專案時，您需要組建組態。 例如，**調試**和**發佈**是配置，在構建它們時相應地使用不同的編譯器選項。  一個配置處於活動狀態，並在 IDE 頂部的命令列中指示。

![活動配置](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的組建組態](/visualstudio/mac/configurations)。

存儲生成輸出檔案的配置和平臺控制項。 通常，當 Visual Studio 生成專案時，輸出將放置在使用活動配置命名的專案子資料夾中（例如 *，bin/Debug/x86），* 但您可以更改該子資料夾。

您可以在解決方案和專案級別創建自己的組建組態。 當組建組態處於活動狀態時，解決方案配置確定生成中包含哪些專案。 將僅組建活動解決方案配置中指定的專案。 如果在組態管理員中選擇多個目標平臺，則生成應用於該平臺的所有專案。 專案配置確定生成專案時使用哪些生成設置和編譯器選項。

若要建立、選取、修改或刪除組態，您可以使用 [組態管理員]****。 要打開它，在功能表列上，選擇 **"生成** > **組態管理員**"，或僅在搜索框中鍵入 **"配置**"。 您也可以使用 [標準]**** 工具列上的 [方案組態]**** 清單，來選取組態或開啟 [組態管理員]****。

![組態管理員](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> 如果在工具列上找不到解決方案配置設置，並且無法訪問**組態管理員**，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]則可以應用開發設置。 有關詳細資訊，請參閱[如何：使用應用了視覺化基本開發人員設置管理配置](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md)。

預設情況下，使用[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]範本創建的專案中包含**調試**和**發佈**配置。 **調試**配置支援應用的調試，**發佈**配置生成可部署的應用版本。 有關詳細資訊，請參閱[操作操作：設置調試和發佈配置](../debugger/how-to-set-debug-and-release-configurations.md)。 您也可以建立自訂方案組態和專案組態。 有關詳細資訊，請參閱[操作：創建和編輯配置](../ide/how-to-create-and-edit-configurations.md)。

## <a name="solution-configurations"></a>方案組態

方案組態指定如何建置和部署方案中的專案。 若要修改方案組態或定義新的組態，請在 [組態管理員]**** 的 [使用中的方案組態]**** 下，選擇 [編輯]**** 或 [新增]****。

方案組態之 [專案內容]**** 方塊中的每個項目，分別代表方案中的一個專案。 針對 [使用中的方案組態]**** 和 [使用中的方案平台]**** 的每種組合，您可以設定每個專案的使用方式 (如需方案平台的詳細資訊，請參閱[了解組建平台](../ide/understanding-build-platforms.md))。

當您定義新的方案組態並選取 [建立新專案組態]**** 核取方塊時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將新的組態自動指派給所有專案。 同樣地，當您定義新的方案平台並選取 [建立新專案組態]**** 核取方塊時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將新的平台自動指派給所有專案。 此外，如果您加入以新平台為目標的專案，Visual Studio 會將該平台加入方案平台清單中，並指派給所有專案。 您仍然可以修改每個專案的設定。

使用中的方案組態也會提供 IDE 的內容。 例如，如果您正在處理某個專案，且組態指定這個專案是針對行動裝置所建置，則 [工具箱]**** 只會顯示可用於行動裝置專案中的項目。

## <a name="project-configurations"></a>專案組態

專案目標的配置和平臺一起使用，以指定生成設置和編譯器選項，以便在生成時使用。 對於配置和平臺的每個組合，專案可以有不同的設置。 要修改專案的屬性，請打開**解決方案資源管理器**中專案的快顯功能表，然後選擇 **"屬性**"。  在專案設計器的 **"生成"** 選項卡的頂部，選擇活動配置以編輯其生成設置。

![專案設計器配置](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>構建多種配置

使用**生成** > **生成解決方案**命令生成解決方案時，Visual Studio 僅組建活動配置。 生成解決方案配置中指定的所有專案，並且構建的唯一專案配置是在活動解決方案配置和活動解決方案平臺中指定的專案，顯示在 Visual Studio 中的工具列中。 例如，**調試**和**x86**。 其他定義的配置和平臺未生成。

如果要在一個操作中構建多個配置和平臺，可以在視覺化工作室中使用 **"生成** > **批次處理生成**"選項。 要訪問此功能，請按**Ctrl**+**Q**打開搜索框，然後`Batch build`輸入 。 批次處理不適用於所有專案類型。 請參閱[操作方式：同時生成多個配置](how-to-build-multiple-configurations-simultaneously.md)。

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio 如何指派專案組態

當您定義新的方案組態，而不是從現有的組態複製設定時，Visual Studio 會使用下列準則來指派預設的專案組態。 準則的評估順序如下所示。

1. 如果專案具有與新解決方案配置名稱完全符合的配置名稱 （*\<配置名稱>\<平臺名稱>），* 則分配該配置。 組態名稱不區分大小寫。

1. 如果專案組態名稱的組態名稱部分符合新的方案組態，則無論平台部分是否相符，都會指派該組態。

1. 如果仍然沒有相符項目，就會指派專案中所列的第一個組態。

## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio 如何指派方案組態

當您建立專案組態 (透過在 [組態管理員]**** 中，選擇該專案 [組態]**** 欄之下拉式功能表中的 [新增]****) 並選取 [建立新方案組態]**** 核取方塊時，Visual Studio 會尋找名稱相同的方案組態，以在每個支援的平台上建置專案。 在某些情況下，Visual Studio 會重新命名現有的方案組態，或定義新的組態。

Visual Studio 使用下列準則來指派方案組態。

- 如果專案組態不會指定平台，或只指定一個平台，則會找到或加入其名稱符合新專案組態名稱的方案組態。 此解決方案配置的預設名稱不包括平臺名稱;因此，此解決方案配置的預設名稱不包括平臺名稱。它採用表單*\<專案配置名稱>*。

- 如果專案支援多個平台，則會為每個支援的平台找到或加入一個方案組態。 每個解決方案配置的名稱包括專案配置名稱和平臺名稱，並且具有*\<>>平臺名稱的\<表單專案配置名稱*。

## <a name="see-also"></a>另請參閱

- [演練：構建應用程式](../ide/walkthrough-building-an-application.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [解決方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ 組建參考](/cpp/build/reference/c-cpp-building-reference)
- [瞭解構建平臺](understanding-build-platforms.md)
- [組建組態 (Visual Studio for Mac)](/visualstudio/mac/configurations)
