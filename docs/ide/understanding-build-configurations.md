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
ms.openlocfilehash: 6b472ca78d36247a76bf397989f48e04230ccd7d
ms.sourcegitcommit: b2fc9ac7d73c847508f6ed082bed026476bb3955
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/05/2020
ms.locfileid: "77027620"
---
# <a name="understand-build-configurations"></a>了解組建組態

當您需要使用不同的設定來建立專案時，您需要組建設定。 例如， **Debug**和**Release**是設定，而建立它們時，會使用不同的編譯器選項。  其中一個設定為作用中，並在 IDE 頂端的命令列中指出。

![Active configuration](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的組建組態](/visualstudio/mac/configurations)。

設定和平臺控制項，其中會儲存建立的輸出檔案。 一般來說，當 Visual Studio 建立您的專案時，輸出會放在名為的專案子資料夾中，並使用作用中的設定（例如*bin/Debug/x86*），但您可以變更它。

您可以在方案和專案層級建立自己的組建設定。 解決方案設定會決定當組建在使用中時，哪些專案會包含在組建中。 只會建立在使用中方案設定中指定的專案。 專案設定會決定當您建立專案時所使用的組建設定和編譯器選項。

若要建立、選取、修改或刪除組態，您可以使用 [組態管理員]。 若要開啟組態，請在功能表列上，選擇 [建置] > [組態管理員]，或直接在搜尋方塊中鍵入**組態**。 您也可以使用 [標準] 工具列上的 [方案組態] 清單，來選取組態或開啟 [組態管理員]。

![組態管理員](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> 如果您在工具列上找不到方案組態設定，而且無法存取 [組態管理員]，則可能會套用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開發設定。 如需詳細資訊，請參閱[如何：在套用 Visual Basic 開發者設定的情況下管理組態](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md)。

根據預設， **Debug**和**Release**設定會包含在使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 範本所建立的專案中。 **Debug**設定支援應用程式的偵測，而**發行**設定則會建立可部署的應用程式版本。 如需詳細資訊，請參閱[如何：設定偵錯和發行組態](../debugger/how-to-set-debug-and-release-configurations.md)。 您也可以建立自訂方案組態和專案組態。 如需詳細資訊，請參閱[如何：建立和編輯組態](../ide/how-to-create-and-edit-configurations.md)。

## <a name="solution-configurations"></a>方案組態

方案組態指定如何建置和部署方案中的專案。 若要修改方案組態或定義新的組態，請在 [組態管理員] 的 [使用中的方案組態] 下，選擇 [編輯] 或 [新增]。

方案組態之 [專案內容] 方塊中的每個項目，分別代表方案中的一個專案。 針對 [使用中的方案組態] 和 [使用中的方案平台] 的每種組合，您可以設定每個專案的使用方式 (如需方案平台的詳細資訊，請參閱[了解組建平台](../ide/understanding-build-platforms.md))。

當您定義新的方案組態並選取 [建立新專案組態] 核取方塊時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將新的組態自動指派給所有專案。 同樣地，當您定義新的方案平台並選取 [建立新專案組態] 核取方塊時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將新的平台自動指派給所有專案。 此外，如果您加入以新平台為目標的專案，Visual Studio 會將該平台加入方案平台清單中，並指派給所有專案。 您仍然可以修改每個專案的設定。

使用中的方案組態也會提供 IDE 的內容。 例如，如果您正在處理某個專案，且組態指定這個專案是針對行動裝置所建置，則 [工具箱] 只會顯示可用於行動裝置專案中的項目。

## <a name="project-configurations"></a>專案組態

專案目標的設定和平臺會一起使用，以指定組建設定和編譯器選項，以在建立時使用。 針對每個設定和平臺組合，專案可以有不同的設定。 若要修改專案的屬性，請在 [**方案總管**] 中開啟專案的快捷方式功能表，然後選擇 [**屬性**]。  在 [專案設計工具] 的 [**組建**] 索引標籤頂端，選擇作用中的設定來編輯其組建設定。

![專案設計工具設定](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio 如何指派專案組態

當您定義新的方案組態，而不是從現有的組態複製設定時，Visual Studio 會使用下列準則來指派預設的專案組態。 準則的評估順序如下所示。

1. 如果專案具有完全符合新方案組態名稱的組態名稱 ( *\<組態名稱> \<平台名稱>* )，則會指派該組態。 組態名稱不區分大小寫。

1. 如果專案組態名稱的組態名稱部分符合新的方案組態，則無論平台部分是否相符，都會指派該組態。

1. 如果仍然沒有相符項目，就會指派專案中所列的第一個組態。

## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio 如何指派方案組態

當您建立專案組態 (透過在 [組態管理員] 中，選擇該專案 [組態] 欄之下拉式功能表中的 [新增]) 並選取 [建立新方案組態] 核取方塊時，Visual Studio 會尋找名稱相同的方案組態，以在每個支援的平台上建置專案。 在某些情況下，Visual Studio 會重新命名現有的方案組態，或定義新的組態。

Visual Studio 使用下列準則來指派方案組態。

- 如果專案組態不會指定平台，或只指定一個平台，則會找到或加入其名稱符合新專案組態名稱的方案組態。 這個方案組態的預設名稱不包含平台名稱，其採用 *\<專案組態名稱>* 格式。

- 如果專案支援多個平台，則會為每個支援的平台找到或加入一個方案組態。 每個方案組態的名稱包含專案組態名稱和平台名稱，並且採用 *\<專案組態名稱> \<平台名稱>* 格式。

## <a name="see-also"></a>另請參閱

- [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ 組建參考](/cpp/build/reference/c-cpp-building-reference)
- [瞭解組建平臺](understanding-build-platforms.md)
- [組建組態 (Visual Studio for Mac)](/visualstudio/mac/configurations)
