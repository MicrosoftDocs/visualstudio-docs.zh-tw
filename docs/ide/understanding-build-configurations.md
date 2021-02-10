---
title: 了解組建組態
description: 瞭解當您需要使用 Visual Studio 中的不同設定來建立專案時，您需要建立組建設定的方式。
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3c6037bd6ed3b7899ff00bce202df7707356683a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971397"
---
# <a name="understand-build-configurations"></a>了解組建組態

當您需要使用不同的設定來建立專案時，您需要組建設定。 例如， **Debug** 和 **Release** 是設定，在建立時，會據以使用不同的編譯器選項。  其中一個設定為作用中，並在 IDE 頂端的命令列中指出。

![Active configuration](media/understanding-build-configurations/active-config.png)

> [!NOTE]
> 本主題適用於 Windows 上的 Visual Studio。 針對 Visual Studio for Mac，請參閱 [Visual Studio for Mac 中的組建組態](/visualstudio/mac/configurations)。

設定和平臺控制項，在其中儲存內建的輸出檔案。 一般來說，當 Visual Studio 建立專案時，會將輸出放在名為「使用中設定」的專案子資料夾中 (例如 *bin/Debug/x86*) ，但您可以變更該專案。

您可以在方案和專案層級建立您自己的組建設定。 解決方案設定會決定要在組建中包含哪些專案。 只會建立作用中方案設定中指定的專案。 如果在設定管理員中選取了多個目標平臺，則會建立適用于該平臺的所有專案。 專案設定會決定當您建立專案時所使用的組建設定和編譯器選項。

若要建立、選取、修改或刪除組態，您可以使用 [組態管理員]。 若要開啟它，請在功能表列上，選擇 [**建立**  >  **設定管理員**]  ，或只在 [搜尋] 方塊中輸入設定。 您也可以使用 [標準] 工具列上的 [方案組態] 清單，來選取組態或開啟 [組態管理員]。

![Configuration Manager](media/understanding-build-configurations/config-manager.png)

> [!NOTE]
> 如果您在工具列上找不到 [方案設定] 設定，而且無法存取 **設定管理員**，可能會套用 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 開發設定。 如需詳細資訊，請參閱 [如何：管理已套用 Visual Basic 開發人員設定的設定](../ide/how-to-manage-build-configurations-with-visual-basic-developer-settings-applied.md)。

根據預設， **Debug** 和 **Release** 設定會包含在使用範本建立的專案中 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 。 **Debug** 設定支援應用程式的偵錯工具，而 **發行** 設定會建立可部署的應用程式版本。 如需詳細資訊，請參閱 [如何：設定 debug 和 Release 設定](../debugger/how-to-set-debug-and-release-configurations.md)。 您也可以建立自訂方案組態和專案組態。 如需詳細資訊，請參閱 [如何：建立和編輯](../ide/how-to-create-and-edit-configurations.md)設定。

## <a name="solution-configurations"></a>方案組態

方案組態指定如何建置和部署方案中的專案。 若要修改方案組態或定義新的組態，請在 [組態管理員] 的 [使用中的方案組態] 下，選擇 [編輯] 或 [新增]。

方案組態之 [專案內容] 方塊中的每個項目，分別代表方案中的一個專案。 針對 [使用中的方案組態] 和 [使用中的方案平台] 的每種組合，您可以設定每個專案的使用方式 (如需方案平台的詳細資訊，請參閱[了解組建平台](../ide/understanding-build-platforms.md))。

當您定義新的方案組態並選取 [建立新專案組態] 核取方塊時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將新的組態自動指派給所有專案。 同樣地，當您定義新的方案平台並選取 [建立新專案組態] 核取方塊時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會將新的平台自動指派給所有專案。 此外，如果您加入以新平台為目標的專案，Visual Studio 會將該平台加入方案平台清單中，並指派給所有專案。 您仍然可以修改每個專案的設定。

使用中的方案組態也會提供 IDE 的內容。 例如，如果您正在處理某個專案，且組態指定這個專案是針對行動裝置所建置，則 [工具箱] 只會顯示可用於行動裝置專案中的項目。

## <a name="project-configurations"></a>專案組態

專案目標的設定和平臺會一起使用，以指定組建設定以及建立時所使用的編譯器選項。 專案可以針對每個設定和平臺組合進行不同的設定。 若要修改專案的屬性，請在 [ **方案總管**] 中開啟專案的快捷方式功能表，然後選擇 [ **屬性**]。  在 [專案設計工具] 的 [ **組建** ] 索引標籤頂端，選擇使用中的設定以編輯其組建設定。

![專案設計工具設定](media/understanding-build-configurations/project-designer-configuration.png)

## <a name="building-multiple-configurations"></a>建立多個設定

當您使用 **組建**  >  **組建方案** 命令來建立方案時，Visual Studio 只會建立作用中的設定。 系統會建立該方案設定中指定的所有專案，而且唯一建立的專案設定是在使用中的方案設定和使用中的方案平臺中指定的專案，這會顯示在 Visual Studio 的工具列中。 例如， **Debug** 和 **x86**。 未建立其他定義的設定和平臺。

如果您想要以一個動作來建立多個設定和平臺，您可以使用 Visual Studio 中的 [**組建**  >  **批次組建**] 選項。 若要存取此功能，請按下 **Ctrl** + **Q** 開啟 [搜尋] 方塊，然後輸入 `Batch build` 。 並非所有專案類型都可使用批次組建。 請參閱 [如何：同時建立多個](how-to-build-multiple-configurations-simultaneously.md)設定。

## <a name="how-visual-studio-assigns-project-configurations"></a>Visual Studio 如何指派專案組態

當您定義新的方案組態，而不是從現有的組態複製設定時，Visual Studio 會使用下列準則來指派預設的專案組態。 準則的評估順序如下所示。

1. 如果專案具有完全符合新方案設定 *\<configuration name> \<platform name>* 名稱的設定名稱 () ，則會指派該設定。 組態名稱不區分大小寫。

1. 如果專案組態名稱的組態名稱部分符合新的方案組態，則無論平台部分是否相符，都會指派該組態。

1. 如果仍然沒有相符項目，就會指派專案中所列的第一個組態。

## <a name="how-visual-studio-assigns-solution-configurations"></a>Visual Studio 如何指派方案組態

當您建立專案組態 (透過在 [組態管理員] 中，選擇該專案 [組態] 欄之下拉式功能表中的 [新增]) 並選取 [建立新方案組態] 核取方塊時，Visual Studio 會尋找名稱相同的方案組態，以在每個支援的平台上建置專案。 在某些情況下，Visual Studio 會重新命名現有的方案組態，或定義新的組態。

Visual Studio 使用下列準則來指派方案組態。

- 如果專案組態不會指定平台，或只指定一個平台，則會找到或加入其名稱符合新專案組態名稱的方案組態。 此解決方案設定的預設名稱不包含平臺名稱;它會採用表單 *\<project configuration name>* 。

- 如果專案支援多個平台，則會為每個支援的平台找到或加入一個方案組態。 每個解決方案設定的名稱都包含專案設定名稱和平臺名稱，且格式 *\<project configuration name> \<platform name>* 為。

## <a name="see-also"></a>另請參閱

- [逐步解說：建置應用程式](../ide/walkthrough-building-an-application.md)
- [編譯和建置](../ide/compiling-and-building-in-visual-studio.md)
- [方案和專案](../ide/solutions-and-projects-in-visual-studio.md)
- [C/C++ 組建參考](/cpp/build/reference/c-cpp-building-reference)
- [瞭解組建平臺](understanding-build-platforms.md)
- [組建組態 (Visual Studio for Mac)](/visualstudio/mac/configurations)
